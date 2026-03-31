# NOTES D'ANALYSE YAAZHINI - INDICES D'EXPOSITION RÉELS
**Analyste :** BEN
**Score de risque max :** 8.1 (High)

## Éléments identifiés

### 1. Insecure Communication
- **Localisation**: APICreds2Activity.java
- **Description**: Utilisation du protocole HTTP non chiffré.
- **Impact**: Vol de credentials via attaque de l'homme du milieu (MitM).

### 2. Android Debuggable Enabled
- **Localisation**: AndroidManifest.xml
- **Description**: Flag debuggable actif.
- **Impact**: Accès facilité au runtime pour l'ingénierie inverse.

### 3. Android Backup Vulnerability
- **Localisation**: AndroidManifest.xml
- **Description**: allowBackup="true".
- **Impact**: Extraction de données locales via ADB possible.

### 4. Improper export of providers
- **Localisation**: Content Providers
- **Description**: Composants exposés sans protection.
- **Impact**: Lecture non autorisée de la base de données de l'app.

### 5. Javascript in WebView
- **Localisation**: WebView Settings
- **Description**: setJavaScriptEnabled(true).
- **Impact**: Possibilité d'exécution de code malveillant (XSS).
