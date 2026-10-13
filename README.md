# AI PR Reviewer

[![Release](https://img.shields.io/github/v/release/seylitanez/auto-pr-releases?color=blue&label=Latest%20Release)](https://github.com/seylitanez/auto-pr-releases/releases/latest)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20(AppImage)-orange.svg)](https://github.com/seylitanez/auto-pr-releases/releases/latest)
[![Issues](https://img.shields.io/github/issues/seylitanez/auto-pr-releases?color=red)](https://github.com/seylitanez/auto-pr-releases/issues)

**AI PR Reviewer** est une application desktop moderne (Electron, React, Monaco Editor) conçue pour révolutionner la relecture de Pull Requests GitHub pour les développeurs exigeants.

Elle combine l'intelligence artificielle locale et souveraine (**BYOK** - *Bring Your Own Keys*) avec des outils d'analyse d'impact sémantique (**AI Blast Intelligence**), d'évaluation Clean Code d'équipe, d'intégration Jira Dev-Pulse en 30 secondes et d'exécution JVM locale sécurisée.

---

## 📥 Guide d'Installation & Lancement (Linux)

L'application est distribuée sous forme de paquet portable universel **AppImage**. Aucune installation avec les droits administrateur (`root` / `sudo`) n'est requise.

### Option A : Téléchargement Direct & Lancement en Ligne de Commande

Ouvrez un terminal et exécutez ces 3 commandes :

```bash
# 1. Télécharger la dernière version de l'AppImage (v1.2.0)
wget https://github.com/seylitanez/auto-pr-releases/releases/download/v1.2.0/AI-PR-Reviewer-1.2.0.AppImage -O AI-PR-Reviewer.AppImage
# ou avec curl :
# curl -L -o AI-PR-Reviewer.AppImage https://github.com/seylitanez/auto-pr-releases/releases/download/v1.2.0/AI-PR-Reviewer-1.2.0.AppImage

# 2. Rendre le fichier exécutable
chmod +x AI-PR-Reviewer.AppImage

# 3. Lancer l'application
./AI-PR-Reviewer.AppImage
```

---

### Option B : Intégration Complète au Menu des Applications (Bureau)

Pour pouvoir lancer **AI PR Reviewer** directement depuis le lanceur d'applications de votre environnement (GNOME, KDE Plasma, XFCE, etc.) :

#### 1. Via `AppImageLauncher` (Recommandé)
Si vous utilisez [AppImageLauncher](https://github.com/TheAssassin/AppImageLauncher) sur votre distribution, double-cliquez simplement sur le fichier téléchargé et choisissez **"Integrate and run"**.

#### 2. Via un fichier raccourci `.desktop` manuel :
Placez l'exécutable dans votre dossier personnel (ex: `~/Applications/`) et créez le fichier desktop suivant :

```bash
mkdir -p ~/.local/share/applications ~/Applications
mv AI-PR-Reviewer.AppImage ~/Applications/

cat << 'EOF' > ~/.local/share/applications/ai-pr-reviewer.desktop
[Desktop Entry]
Name=AI PR Reviewer
Comment=Analyseur de Pull Requests IA & Simulateur de Code
Exec=/home/%u/Applications/AI-PR-Reviewer.AppImage
Icon=system-software-update
Terminal=false
Type=Application
Categories=Development;IDE;
StartupWMClass=ai-pr-reviewer
EOF

# Remplacer %u par votre nom d'utilisateur actuel
sed -i "s/%u/$USER/g" ~/.local/share/applications/ai-pr-reviewer.desktop
chmod +x ~/.local/share/applications/ai-pr-reviewer.desktop
```

---

### ⚠️ Dépannage : Problème de lancement sur Ubuntu 22.04+ / Debian 12+ (FUSE)

Si en lançant l'AppImage vous obtenez une erreur du type :
```
dlopen(): error loading libfuse.so.2: cannot open shared object file
```
C'est parce que les distributions récentes n'embarquent plus FUSE 2 par défaut. Vous pouvez régler cela en installant la bibliothèque de compatibilité :

```bash
# Ubuntu / Debian / Pop!_OS / Linux Mint
sudo apt update && sudo apt install -y libfuse2

# Fedora / Red Hat
sudo dnf install fuse-libs

# Arch Linux / Manjaro
sudo pacman -S fuse2
```

*(Alternative sans installer FUSE : vous pouvez lancer l'application avec `--appimage-extract-and-run` : `./AI-PR-Reviewer.AppImage --appimage-extract-and-run`).*

---

## ⚙️ Configuration Initiale (Prise en Main en 2 Minutes)

Au premier lancement de l'application, rendez-vous dans l'onglet **`Settings`** pour configurer vos accès :

### 1. Connexion GitHub
- **GitHub Token** : Créez un jeton d'accès personnel sur [github.com/settings/tokens](https://github.com/settings/tokens) avec la permission minimale `repo`.
- **Owner / Repo** : Renseignez le propriétaire et le dépôt par défaut (ex: `mon-organisation` et `mon-projet`).
- **Chemin Local** : Le chemin absolu vers le clone local du dépôt sur votre machine (ex: `/home/user/workspace/mon-projet`). Cela permet à l'application de fouiller l'historique Git et les conventions de votre équipe.

### 2. Choix du Fournisseur d'IA (BYOK)
- **Google Gemini (Recommandé - Quota Gratuit de 1 500 requêtes/jour)** : Obtenez une clé API gratuite en 1 clic sur [aistudio.google.com](https://aistudio.google.com).
- **Mistral AI** : Clé API sur [console.mistral.ai](https://console.mistral.ai).
- **OpenAI / Anthropic** : Vos clés API standard.
- **Ollama (100% Local & Hors-ligne)** : Entrez simplement l'URL de votre instance locale (`http://localhost:11434`) pour une analyse totalement privée sans appel sortant.

### 3. Intégration Jira Cloud (Optionnel)
- Activez le toggle **Intégration Jira**.
- **Domaine Jira** : Le sous-domaine de votre instance Atlassian (ex: `mon-equipe` pour `mon-equipe.atlassian.net`).
- **Email Atlassian** : Votre email de connexion Atlassian.
- **Token API Jira** : Généré sur [id.atlassian.com/manage-profile/security/api-tokens](https://id.atlassian.com/manage-profile/security/api-tokens).
- **Clé Projet** : Le préfixe de votre projet Jira (ex: `PROJ` ou `VOT`).

### 4. Environnement Java OpenJDK (Optionnel pour les projets Java)
- L'application détecte automatiquement le JDK installé sur votre machine (Temurin, OpenJDK, SDKMAN).
- Si aucun JDK n'est trouvé, un bouton dans les paramètres permet de télécharger et d'installer automatiquement **Eclipse Temurin OpenJDK 21** sans configuration manuelle.

---

## 🌟 Fonctionnalités Majeures (v1.2.0)

| Fonctionnalité | Description |
| :--- | :--- |
| 🚨 **AI Blast Intelligence** | Cartographie l'impact sémantique de vos modifications en 3 paliers d'urgence : Endpoints REST publics, Services métiers appelants avec conseils de migration précis, et classes de tests unitaires à relancer (`mvn test`). |
| 🎮 **Banc d'Essai Réactif & JDK** | Testez vos règles métier en direct (curseurs de valeurs, interrupteurs booléens) avec 0 ms de latence, et compilez vos extraits Java en 500 ms sur votre propre OpenJDK 21 local avec décomposition pas-à-pas des expressions. |
| 🧼 **Clean Code & Patterns d'Équipe** | Jauge bicolore intelligente croisant les 35 derniers commits réels de votre équipe avec les principes universels SOLID. Arbitre les dilemmes et fournit un tiroir d'explication "Pourquoi" avec téléportation à la ligne exacte. |
| 🎟️ **Jira Dev-Pulse** | Convertit les spécifications Jira ADF en 3 vues ciblées : *En Bref* (30s), *En Clair* (vulgarisation pragmatique pour développeur avec métaphores concrètes), et *Checklist de conformité* PR vs US. |
| 📊 **Compteur de Quotas & Tokens** | Suivi temps réel des tokens consommés et surveillance du quota quotidien gratuit de 1 500 requêtes/jour. |
| 🐞 **Signalement de Bugs In-App** | Signalez un problème ou proposez une idée en 1 clic directement depuis l'application avec diagnostics automatiques inclus. |

---

## 🐞 Signaler un Problème ou Suggérer une Amélioration

Vous pouvez soumettre vos retours de deux manières :
1. **Directement dans l'application** : Cliquez sur le bouton `[ 🐞 Signaler un Problème ]` en bas de la barre latérale ou dans le pied de page pour ouvrir le modal de signalement.
2. **Sur le dépôt GitHub** : Créez une issue sur [seylitanez/auto-pr-releases/issues](https://github.com/seylitanez/auto-pr-releases/issues/new).

---

## 🔄 Comment Mettre à Jour vers une Nouvelle Version ?

Pour mettre à jour **AI PR Reviewer** :
1. Téléchargez simplement la nouvelle AppImage depuis la page des [Releases](https://github.com/seylitanez/auto-pr-releases/releases/latest).
2. Rendez-la exécutable (`chmod +x`).
3. Remplacez l'ancien fichier : **toutes vos configurations, projets et clés API sont conservés automatiquement** dans votre dossier utilisateur (`~/.config/auto-pr/`).

---

## 📄 Licence
Ce projet est distribué sous licence MIT. Consultez le fichier [LICENSE](LICENSE) pour plus d'informations.
