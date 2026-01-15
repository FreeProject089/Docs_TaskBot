# 📋 Liste des Fonctionnalités - TaskBot

Ce document détaille l'ensemble des fonctionnalités et commandes disponibles dans TaskBot, classées par catégorie et niveau de permission.

---

## 🛡️ Administration (Owner Only)
Ces commandes sont réservées au propriétaire du bot (ID configuré) et aux administrateurs globaux.

| Commande | Description |
|----------|-------------|
| `/genkey` | Génère des clés d'abonnement (Classique, Premium, Ultra). |
| `/serverban` | Bannit un serveur de l'utilisation du bot (avec preuves). |
| `/scan` | Force un scan global des serveurs et utilisateurs pour synchroniser la DB. |
| `/botinfo` | Affiche les statistiques techniques et l'état du bot. |
| `/feedbackban` | Bannit un utilisateur du système de feedback. |
| `/feedbackunban` | Débannit un utilisateur du système de feedback. |
| `/globalban` | Bannissement global d'un utilisateur (impacte tous les serveurs). |

---

## ⚙️ Configuration (Staff/Admin Serveur)
Commandes pour configurer le bot sur un serveur spécifique.

### 🎮 Join-To-Create (JTC)
*   `/jtc toggle` : Active ou désactive le système de création de salons vocaux.
*   `/config jtc` : Configure les salons "Lobby" et les catégories de destination.
    *   Supporte jusqu'à 6 lobbies différents (selon les SubBoosts).
    *   Interface de contrôle dynamique pour les propriétaires de salons (Rename, Limit, Kick, Lock, NSFW, Presets).

### 🎫 Tickets
*   `/ticket toggle` : Active ou désactive le système de tickets.
*   `/ticket panel` : Envoie le panneau de création de tickets dans un salon.
*   `/ticket setup` : Configure les types de tickets, les rôles de support et les catégories d'archivage.

### 👋 Welcome & Goodbye
*   `/welcome toggle` : Active ou désactive les messages de bienvenue/départ.
*   `/welcome configure` : Configure les images (Canvas), les textes et les salons.
    *   Variables supportées : `{user}`, `{server}`, `{membercount}`, etc.
    *   Aperçu en direct lors de la configuration.

### 🛡️ Sécurité & Modération
*   `/security status` : Affiche l'état actuel de la sécurité.
*   `/security setup` : Configure l'âge minimum du compte et l'**Anti-Phishing Global**.
*   `/automod config` : Configure les filtres automatiques (Mots interdits, Liens, Spam majuscules).
*   `/antiraid config` : Configuration avancée des seuils de détection de raid (Join burst, Mass mention).

### 🎭 Rôles & Membres
*   `/reactionrole panel` : Crée des panneaux de rôles par réaction (Toggle, Verify, Unique).
*   `/activemembers config` : Définit les critères pour être "Membre Actif" (Messages/Vocal par semaine).
*   `/invites configure` : Configure les critères de validité des invitations (Âge du compte invité, temps de présence).

---

## 💎 Système d'Abonnement & Boosts
TaskBot utilise un système de "SubBoosts" pour débloquer des limites supérieures.

| Commande | Description |
|----------|-------------|
| `/enablesubkey` | Active une clé d'abonnement sur son compte. |
| `/subboost add` | Alloue des SubBoosts de son compte vers le serveur actuel. |
| `/subboost remove` | Retire ses SubBoosts d'un serveur. |
| `/subboost status` | Affiche votre solde de boosts et vos allocations actuelles. |
| `/checkkey` | Vérifie l'état d'une clé ou de son propre abonnement. |

---

## 👤 Utilisateur (Public)
Commandes accessibles à tous les utilisateurs.

| Commande | Description |
|----------|-------------|
| `/help` | Affiche le menu d'aide interactif par catégorie. |
| `/stats` | Affiche vos statistiques personnelles (messages, temps vocal, boosts). |
| `/invites show` | Affiche vos invitations totales, valides, et invalides. |
| `/level` | Affiche votre niveau d'expérience et votre progression. |
| `/feedback` | Envoie une suggestion ou un rapport de bug aux développeurs. |
| `/report` | Signale un utilisateur pour comportement inapproprié. |
| `/serverreport` | Signale le serveur actuel pour non-respect des règles. |
| `/userappeal` | Formule un appel suite à un bannissement utilisateur. |

---

## 📊 Systèmes Automatisés
*   **Anti-Phishing** : Détection proactive des liens malveillants via base de données globale et API externe. Gestion centralisée des cas.
*   **Suivi d'Invitations** : Calcul intelligent de la validité des invitations basé sur la rétention et l'activité des invités.
*   **Boost Decay** : Les serveurs perdent 4 SubBoosts par mois (nécessite un renouvellement des abonnements).
*   **Auto-Modération** : Vérification de l'âge des comptes à l'entrée et filtrage du contenu des messages.
*   **Voice Tracking** : Enregistrement du temps passé en vocal pour les statistiques.
