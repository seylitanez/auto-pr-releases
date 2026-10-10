# AI PR Reviewer Releases

[![Release](https://img.shields.io/github/v/release/seylitanez/auto-pr-releases?color=blue&label=Latest%20Release)](https://github.com/seylitanez/auto-pr-releases/releases/latest)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20(AppImage)-orange.svg)](https://github.com/seylitanez/auto-pr-releases/releases/latest)

**AI PR Reviewer** est une application desktop moderne (Electron, React, Monaco Editor) conçue pour révolutionner la relecture de Pull Requests GitHub pour les développeurs exigeants.

Elle allie l'intelligence artificielle locale et souveraine (BYOK - Bring Your Own Keys) avec des outils d'analyse d'impact profonde et d'exécution JVM locale.

---

## 🚀 Téléchargement & Lancement Rapide

### Linux (AppImage Portable)
Téléchargez le binaire portable officiel depuis les [Releases GitHub](https://github.com/seylitanez/auto-pr-releases/releases/latest) :

```bash
# 1. Rendre le binaire exécutable
chmod +x AI-PR-Reviewer-1.2.0.AppImage

# 2. Lancer l'application
./AI-PR-Reviewer-1.2.0.AppImage
```

---

## 🌟 Superpouvoirs Clés (v1.2.0)

### 🚨 1. AI Blast Intelligence (Rayon d'Impact Sémantique)
- **Détection des Breaking Changes** : Analyse sémantique des modifications de signatures de méthodes, des altérations de DTOs et des nouvelles exceptions levées.
- **Cartographie en 3 Paliers d'Urgence** :
  - **Palier 1 (API & Endpoints)** : Contrôleurs REST directement impactés.
  - **Palier 2 (Services Métiers)** : Composants appelants avec conseils de migration précis.
  - **Palier 3 (Tests Unitaires)** : Classes exactes à relancer avec commandes `mvn test -Dtest=...` prêtes à copier.
- **Filtre Anti-Bruit** : Élimine automatiquement les imports passifs, déclarations de packages, commentaires et logs.

### 🎮 2. Banc d'Essai Réactif & Exécution JVM Locale
- **Simulateur 0 ms de latence** : Testez les variables en direct (nombres, curseurs, interrupteurs booléens VRAI/FAUX, listes déroulantes) : le verdict change immédiatement.
- **Exécution OpenJDK 21 Réelle** : Compilez et exécutez vos extraits Java en 500 ms sur votre propre machine locale (Temurin OpenJDK) avec décomposition pas-à-pas des sous-expressions booléennes et terminal de sortie intégré.
- **Aiguilleur Intelligent** : Détecte automatiquement la nature du code sélectionné (logique pure vs déclarations d'injections Spring) et génère des mocks autonomes pour les services externes.

### 🧼 3. Clean Code & Patterns d'Équipe
- **Jauge Bicolore Équilibrée** : Compare le code de votre PR aux 35 derniers commits réels de l'équipe et aux principes universels SOLID.
- **Arbitrage des Dilemmes** : Résout les compromis pragmatiques entre habitudes réelles du dépôt et théorie du Clean Code.
- **Tiroir "Pourquoi"** : Explications détaillées du risque et téléportation en 1 clic vers la ligne de code exacte.

### 🎟️ 4. Jira Dev-Pulse (Compréhension en 30s)
- **En Bref (30s)** : Synthèse ultra-concise en 3 puces (Objectif, Comportement Runtime, Périmètre & Impact).
- **En Clair (Sans Chichi)** : Explication pragmatique en langage dev direct avec métaphores concrètes.
- **Checklist PR vs US** : Croisement automatisé de chaque critère d'acceptation de l'US avec le diff Git de la PR (Respecté `✓`, Partiel `!`, Oublié `✕`).
- **Convertisseur ADF ➔ Markdown** : Rendu soigné des spécifications Atlassian.

### 📊 5. Compteur de Quota & Tokens Temps Réel
- Suivi transparent des tokens consommés par provider (Google Gemini, Mistral, OpenAI, Anthropic).
- Suivi du quota quotidien gratuit Google Gemini (1 500 requêtes/jour).

---

## 🔒 Confidentialité & Souveraineté des Données (BYOK)
- Vos clés API restent stockées localement et chiffrées sur votre machine.
- Compatible avec les modèles 100% locaux via **Ollama** pour travailler hors-ligne et sans fuite de code.

---

## 📄 Licence
Ce projet est distribué sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.
