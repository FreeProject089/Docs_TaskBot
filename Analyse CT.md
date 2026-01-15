# 🤖 Analyse Complète de TaskBot

Ce document détaille l'ensemble des commandes de TaskBot, leurs fonctionnalités et leur fonctionnement interne.

---

## 📋 Sommaire
1. [Général](#-général)
2. [Modération & Sécurité](#-modération--sécurité)
3. [Join-To-Create (JTC)](#-join-to-create-jtc)
4. [Tickets](#-tickets)
5. [Giveaways & Événements](#-giveaways--événements)
6. [Abonnements & SubBoosts](#-abonnements--subboosts)
7. [Statistiques & Niveaux](#-statistiques--niveaux)
8. [Administration & Propriétaire](#-administration--propriétaire)

---

## 📋 Général
Commandes de base pour l'interaction et l'information.

- **`/help`** : Affiche le menu d'aide interactif.
  - *Fonctionnement* : Utilise des menus de sélection et des boutons pour naviguer entre les catégories et afficher le guide des systèmes.
- **`/botinfo`** : Affiche les informations techniques du bot (version, uptime, serveurs, utilisateurs).
- **`/ping`** : Affiche la latence du bot et de l'API Discord.
- **`/feedback`** : Permet d'envoyer des suggestions ou signaler des bugs.
  - *Fonctionnement* : Ouvre un modal pour la saisie. Le feedback est envoyé dans un salon de logs dédié aux administrateurs du bot.
- **`/profile`** : Affiche le profil de l'utilisateur avec ses statistiques globales et ses fonds équipés.

---

## 🛡️ Modération & Sécurité
Systèmes avancés de protection du serveur et de gestion automatique.

### Anti-Raid
- **`/antiraid config`** : Configure les seuils de détection et les réponses.
- **`/antiraid help`** : Affiche la documentation du système.
- *Sous-fonctionnement* : 
  - **Détection** : Surveille en temps réel (mémoire vive) les vagues d'arrivées (`join_burst`), les créations de salons/rôles en masse (`mass_creation`), le spam de forums (`forum_spam`) et le flood de messages (`message_flood`).
  - **Réponses** : Peut alerter les admins, mettre l'utilisateur en quarantaine (timeout 24h), activer le slowmode automatique ou passer le serveur en **Lockdown** (expulsion automatique des nouveaux arrivants).
  - **Captcha** : Système de vérification par image (générée dynamiquement) envoyé par DM ou dans un salon dédié.

### Sécurité & Anti-Phishing
- **`/security config`** : Gère l'âge minimum des comptes, l'anti-phishing et l'auto-kick des utilisateurs bannis globalement.
- **`/security status`** : Affiche l'état actuel des protections.
- *Sous-fonctionnement Anti-Phishing* :
  - **Détection** : Scan proactif des liens envoyés dans tous les messages via API externe et base de données locale.
  - **Action** : Suppression immédiate du message, Timeout de l'utilisateur, et création d'un **Case** (Dossier) dans le serveur Admin.
  - **Gestion Admin** : Les administrateurs globaux peuvent `Claim`, `Transfer`, `Close` ou `Ban Global` à partir du dossier de phishing.
  - **Preuve** : Capture automatique du contexte (messages 24h avant) pour analyse.

### Auto-Modération (Automod)
- **`/automod config`** : Configuration des filtres automatiques.
- *Filtres disponibles* :
  - **Bad Words** : Liste noire de mots interdits avec wildcard.
  - **Anti-Links** : Interdiction des invites Discord ou liens http généraux (whitelist disponible).
  - **Caps Lock** : Détection de l'abus de majuscules (ex: >70% sur messages longs).
  - **Mass Mention** : Limite le nombre de pings par message (ex: max 5).

### Modération Classique
- **`/clear`** : Supprime un grand nombre de messages (jusqu'à 100).
- **`/report`** : Signale un utilisateur aux modérateurs du serveur.
- **`/serverreport`** : Signale un serveur aux administrateurs de TaskBot.

### Membres Actifs
- **`/activemembers config`** : Définit les seuils pour obtenir le rôle "Actif" (Requiert 2 SubBoosts).
- **`/activemembers status`** : Affiche la configuration actuelle du serveur.
- *Sous-fonctionnement* : 
  - Permet de définir des critères hebdomadaires (ex: 15 messages OU 5 min de vocal).
  - Le système vérifie périodiquement l'activité et attribue/retire le rôle automatiquement.

### Rôles par Réaction
- **`/reactionrole add`** : Ajoute un rôle lié à un emoji sur un message spécifique.
- **`/reactionrole panel`** : Crée un bel embed personnalisé pour servir de base aux rôles par réaction.
- *Sous-fonctionnement* :
  - Supporte plusieurs types : `Normal` (Toggle), `Unique` (un seul par message), `Verify` (donne uniquement), `Drop` (retire uniquement).
  - Limité à 3 rôles par message par défaut, passe à 10 avec 4 SubBoosts.

---

## 🎮 Join-To-Create (JTC)
Salons vocaux temporaires et personnalisables.

- **`/config jtc`** : Configure les salons "Lobby" qui déclenchent la création.
- **`/jtc toggle`** : Active ou désactive le système sur le serveur.
- *Sous-fonctionnement* : 
  - Lorsqu'un utilisateur rejoint un salon Lobby, le bot crée un salon vocal privé et déplace l'utilisateur dedans.
  - Un **Panel de Contrôle** (Message ou Interface) est envoyé dans le salon créé, permettant au propriétaire de :
    - **Renommer** le salon (avec cooldown de 10 min).
    - **Limiter** le nombre de places.
    - **Verrouiller/Déverrouiller** l'accès.
    - **Expulser/Blacklister** des membres.
    - **Sauvegarder/Charger des Presets** (configurations favorites).
  - Le salon est automatiquement supprimé quand il devient vide.
  - **Débordement (Overflow)** : Si une catégorie est pleine (50 salons), le bot crée automatiquement une nouvelle catégorie `[FMR]`.

---

## 🎫 Tickets
Système de support par salons privés.

- **`/ticket panel`** : Envoie le message avec le menu de sélection pour ouvrir un ticket.
- **`/ticket create`** : Configure un nouveau type de ticket (nom, rôle accès, catégorie).
- *Sous-fonctionnement* :
  - Supporte plusieurs types de tickets avec des permissions spécifiques pour chaque rôle de staff.
  - **Claim** : Un modérateur peut prendre en charge un ticket, ce qui est enregistré dans les logs.
  - **Transfert** : Permet de transférer la responsabilité du ticket à un autre modérateur.
  - **Archivage** : Les tickets fermés peuvent être déplacés dans une catégorie d'archive au lieu d'être supprimés.

---

## 🎁 Giveaways & Événements
Engagement de la communauté.

### Giveaways
- **`/giveaway create`** : Lance un concours avec des conditions de participation.
- *Sous-fonctionnement* : 
  - Vérifie automatiquement les conditions : rôles requis, nombre d'invitations valides, nombre de SubBoosts, type d'abonnement, ancienneté sur le serveur ou âge du compte.
  - Tirage au sort automatique à la fin du temps imparti.

### Événements
- **`/event create`** : Organise un événement avec inscriptions.
- *Sous-fonctionnement* : 
  - Envoie des rappels automatiques aux inscrits (24h et 5min avant).
  - Possibilité de tirer un gagnant au sort parmi les participants à la fin.

---

## 💎 Abonnements & SubBoosts
Système économique et premium du bot.

- **`/perks`** : Affiche les avantages débloqués sur le serveur actuel.
- **`/subboost status`** : Affiche votre solde de boosts et vos contributions.
- **`/enablesubkey`** : Active une clé d'abonnement (Classic, Premium, Ultra).
- *Sous-fonctionnement* : 
  - Les **SubBoosts** sont des points que les abonnés peuvent donner à un serveur pour débloquer des paliers de fonctionnalités (plus de JTC, fonds personnalisés, etc.).
  - Les abonnements (`Classic`, `Premium`, `Ultra`) offrent des limites plus élevées sur tous les systèmes.

---

## 📊 Statistiques & Niveaux
Suivi de l'activité.

- **`/stats`** : Affiche vos statistiques détaillées (messages, vocal, XP).
- **`/voicestats show`** : Génère une image personnalisée de vos statistiques vocales.
- **`/leaderboard`** : Affiche le classement du serveur (XP/Messages).
- **`/level`** : Affiche votre carte de niveau actuelle.
- **`/invites show`** : Affiche vos statistiques d'invitations (valides vs invalides).
- **`/invites configure`** : (Admin) Configure les règles de validité des invitations.
  - *Algorithme de validité* : Une invitation est considérée comme valide si l'invité reste sur le serveur un temps minimum (ex: 7 jours) ET/OU atteint une activité minimale (messages/vocal) selon la configuration.

---

## 👑 Administration & Propriétaire
Commandes réservées aux administrateurs de TaskBot.

- **`/systems`** : Permet de désactiver globalement un système (ex: maintenance des tickets).
- **`/globalban`** : Bannit un utilisateur de tous les serveurs utilisant TaskBot.
- **`/serverban`** : Interdit à un serveur d'utiliser le bot.
- **`/genkey`** : Génère des clés d'abonnement.
- **`/addsub`** : Ajoute manuellement un abonnement à un utilisateur.
- **`/backgrounds`** : Gère la bibliothèque de fonds (images) pour les profils et les messages de bienvenue.
- **`/feedbackban/unban`** : Gère les accès au système de feedback.
