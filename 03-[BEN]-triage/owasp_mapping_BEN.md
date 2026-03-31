# MAPPING OWASP MASVS - AUDIT DIVA
**Analyste :** BEN
**Référence :** OWASP Mobile Application Security Verification Standard (MASVS)

## FIND-001: Insecure HTTP Communication
- **Catégorie OWASP**: MASVS-NETWORK
- **Référence spécifique**: L1-5.1 (Cryptographic Protection)
- **Justification**: L'application transmet des données via HTTP. Le MASVS exige que toutes les communications réseau soient protégées par TLS.

## FIND-002: Android Debuggable Enabled
- **Catégorie OWASP**: MASVS-RESILIENCE
- **Référence spécifique**: L1-8.2 (Anti-Reversing)
- **Justification**: Le flag debuggable facilite l'analyse dynamique et l'injection de code, violant les principes de résilience.

## FIND-003: AllowBackup Enabled
- **Catégorie OWASP**: MASVS-STORAGE
- **Référence spécifique**: L1-2.8 (Local Storage)
- **Justification**: La sauvegarde ADB permet d'extraire des données sensibles du répertoire de l'application sans privilèges root.

## FIND-004: Improper Content Provider Export
- **Catégorie OWASP**: MASVS-PLATFORM
- **Référence spécifique**: L1-6.1 (Platform Interaction)
- **Justification**: L'exposition de composants sans permissions adéquates permet à des apps tierces de lire la base de données interne.

## FIND-010: Hardcoded Passwords/Secrets
- **Catégorie OWASP**: MASVS-STORAGE
- **Référence spécifique**: L1-2.1 (Sensitive Data)
- **Justification**: Le stockage de secrets en clair dans le code source est une violation directe de la gestion des données sensibles.
