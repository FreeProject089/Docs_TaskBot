# 🤖 TaskBot - L'Assistant Discord Ultime

[English Version](./README_EN.md)

[![Discord.js](https://img.shields.io/badge/discord.js-v14-blue.svg)](https://discord.js.org)
[![Node.js](https://img.shields.io/badge/node.js->=18.0.0-green.svg)](https://nodejs.org)
[![SQLite](https://img.shields.io/badge/database-SQLite3-orange.svg)](https://www.sqlite.org)

TaskBot est un bot Discord polyvalent et puissant conçu pour automatiser la gestion de vos serveurs. Il combine un système de **Join-To-Create**, une gestion de **Tickets** avancée, des **Messages de Bienvenue** personnalisables et un système unique d'**Abonnements par paliers**.

---

## ✨ Fonctionnalités Clés

*   **🎮 Join-To-Create (JTC)** : Salons vocaux temporaires avec panneau de contrôle complet (Rename, Limit, Kick, Lock, Presets).
*   **🎫 Système de Tickets** : Gestion multi-catégories, archivage automatique et transfert de tickets.
*   **👋 Welcome & Goodbye** : Images générées dynamiquement (Canvas) avec prévisualisation en direct.
*   **💎 Système d'Abonnement** : Trois paliers (Classique, Premium, Ultra) débloquant des limites supérieures via des SubBoosts.
*   **🛡️ Modération & Sécurité** : Système d'anti-raid (Age du compte), Anti-Phishing avec base de données globale, et Auto-Modération.
*   **📩 Suivi d'Invitations** : Système de tracking des invitations avec validité intelligente (Critères: Âge compte, temps vocal, messages).
*   **📊 Statistiques** : Suivi précis de l'activité (messages, temps vocal) et des boosts.

👉 **[Consulter la liste détaillée des fonctionnalités (FEATURES.md)](./FEATURES.md)**

---

## 🚀 Installation Rapide

### 1. Prérequis
*   [Node.js](https://nodejs.org/) v18 ou supérieur.
*   Un compte développeur Discord et un bot créé sur le [Portail Développeur](https://discord.com/developers/applications).

### 2. Clonage et Dépendances
```bash
git clone https://github.com/votre-repo/taskbot.git
cd taskbot
npm install
```

### 3. Configuration
Créez un fichier `.env` à la racine du projet :
```env
DISCORD_TOKEN=votre_token_ici
CLIENT_ID=votre_client_id_ici
CLIENT_SECRET=votre_client_secret_ici
```

### 4. Déploiement des commandes
```bash
npm run deploy
```

### 5. Lancement
```bash
# Mode Production
npm start

# Mode Développement (avec auto-reload)
npm run dev
```

---

## 🗃️ Architecture Technique

*   **Langage** : JavaScript (Node.js)
*   **Librairie** : Discord.js v14
*   **Base de données** : SQLite3 (via better-sqlite3)
*   **Moteur d'images** : Canvas (pour les messages de bienvenue)
*   **Planification** : Node-cron (pour les tâches quotidiennes/mensuelles)

---

## 💎 Modèle d'Abonnement

| Avantages | Classique | Premium | Ultra |
|-----------|-----------|---------|-------|
| **SubBoosts** | 0 | 5 | 12 |
| **Lobbies JTC** | 1 | 3 | 6 |
| **Presets JTC** | 1 | 2 | 3 |
| **Types Tickets** | 3 | 5 | 8 |

---

## 📝 Licence
Ce projet est sous licence privée. Toute reproduction ou distribution sans autorisation est interdite.
