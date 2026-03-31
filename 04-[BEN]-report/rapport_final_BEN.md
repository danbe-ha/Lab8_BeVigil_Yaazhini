# RAPPORT D'ANALYSE DE SÉCURITÉ MOBILE - PROJET DIVA
**Analyste :** BEN
**Date :** 31/03/2026
**Statut :** Finalisé

## A. Informations Générales
- **Cible :** DivaApplication.apk (jakhar.aseem.diva)
- **Empreinte (SHA-256) :** 
- **Outils :** BeVigil OSINT, Yaazhini Static Scanner v1.3.2
- **Périmètre :** Analyse statique et exposition cloud (OSINT).

## B. Résumé Exécutif
L'analyse de l'application DIVA a révélé un niveau de risque **ÉLEVÉ**. Sur 10 constats effectués, **2 vulnérabilités critiques** (High) ont été confirmées, concernant le stockage de mots de passe en clair et l'utilisation de protocoles non chiffrés. La surface d'attaque est principalement liée à des pratiques de développement non sécurisées (Hardcoding).

## C. Top 5 Constats Prioritaires

### 1. Insecure HTTP Communication (FIND-001)
- **Sévérité**: High (CVSS 8.1)
- **Preuve**: APICreds2Activity.java (Yaazhini + BeVigil)
- **Impact**: Interception des identifiants API sur réseaux Wi-Fi publics.
- **Remédiation**: Implémenter HTTPS/TLS pour tous les endpoints.
- **Référence OWASP**: MASVS-NETWORK-1

### 2. Hardcoded Credentials (FIND-010)
- **Sévérité**: High
- **Preuve**: InsecureStorageActivity.java (Code source)
- **Impact**: Accès total aux comptes utilisateurs par simple ingénierie inverse.
- **Remédiation**: Ne jamais stocker de secrets en clair; utiliser Android Keystore.
- **Référence OWASP**: MASVS-STORAGE-2

### 3. Android Debuggable Enabled (FIND-002)
- **Sévérité**: Medium
- **Preuve**: AndroidManifest.xml
- **Impact**: Permet à un attaquant d'analyser l'application en cours d'exécution.
- **Remédiation**: Définir android:debuggable="false".
- **Référence OWASP**: MASVS-RESILIENCE-2

### 4. AllowBackup Enabled (FIND-003)
- **Sévérité**: Medium
- **Preuve**: AndroidManifest.xml
- **Impact**: Extraction de données locales possible via ADB sans accès root.
- **Remédiation**: Définir android:allowBackup="false".
- **Référence OWASP**: MASVS-STORAGE-1

### 5. Insecure Database Queries (FIND-005)
- **Sévérité**: Medium
- **Preuve**: SQL Injection findings (Yaazhini)
- **Impact**: Lecture non autorisée de la base de données SQLite locale.
- **Remédiation**: Utiliser des requêtes SQL paramétrées.
- **Référence OWASP**: MASVS-PLATFORM-1

## D. Faux Positifs Notables
- **Firebase Database URL** : Identifié par Yaazhini comme risque d'exposition, mais après vérification manuelle, l'URL pointe vers une instance de test inactive (RAS).

## E. Recommandations Prioritaires
1. **Chiffrer le stockage local** : Migrer les données sensibles des SharedPrefs vers une base chiffrée.
2. **Sécuriser le réseau** : Migrer tous les endpoints de l'API vers le protocole HTTPS.
3. **Nettoyer le Manifest** : Désactiver le mode debug et les sauvegardes automatiques avant production.

## F. Annexes
- Triage consolidé : ../03-[BEN]-triage/triage_BEN.csv
- Captures BeVigil : ../01-[BEN]-bevigil/
- Rapports Yaazhini : ../02-[BEN]-yaazhini/
