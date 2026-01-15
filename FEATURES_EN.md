# 📋 Features List - TaskBot

This document details all the features and commands available in TaskBot, categorized by permission level.

---

## 🛡️ Administration (Owner Only)
These commands are reserved for the bot owner (configured ID) and global admins.

| Command | Description |
|----------|-------------|
| `/genkey` | Generates subscription keys (Classic, Premium, Ultra). |
| `/serverban` | Bans a server from using the bot (with evidence). |
| `/scan` | Forces a global scan of servers and users to sync the DB. |
| `/botinfo` | Displays technical statistics and bot status. |
| `/feedbackban` | Bans a user from the feedback system. |
| `/feedbackunban` | Unbans a user from the feedback system. |
| `/globalban` | Global ban of a user (impacts all servers). |

---

## ⚙️ Configuration (Staff/Server Admin)
Commands to configure the bot on a specific server.

### 🎮 Join-To-Create (JTC)
*   `/jtc toggle`: Enable or disable the voice channel creation system.
*   `/config jtc`: Configure "Lobby" channels and destination categories.
    *   Supports up to 6 different lobbies (depending on SubBoosts).
    *   Dynamic control interface for channel owners (Rename, Limit, Kick, Lock, NSFW, Presets).

### 🎫 Tickets
*   `/ticket toggle`: Enable or disable the ticket system.
*   `/ticket panel`: Send the ticket creation panel to a channel.
*   `/ticket setup`: Configure ticket types, support roles, and archiving categories.

### 👋 Welcome & Goodbye
*   `/welcome toggle`: Enable or disable welcome/leave messages.
*   `/welcome configure`: Configure images (Canvas), texts, and channels.
    *   Supported variables: `{user}`, `{server}`, `{membercount}`, etc.
    *   Live preview during configuration.

### 🛡️ Security & Moderation
*   `/security status`: Displays the current security status.
*   `/security setup`: Configure minimum account age and **Global Anti-Phishing**.
*   `/automod config`: Configure automatic filters (Bad words, Links, Caps spam).
*   `/antiraid config`: Advanced configuration for raid detection thresholds (Join burst, Mass mention).

### 🎭 Roles & Members
*   `/reactionrole panel`: Create reaction role panels (Toggle, Verify, Unique).
*   `/activemembers config`: Define criteria for "Active Member" status (Messages/Voice per week).
*   `/invites configure`: Configure invitation validity criteria (Invitee account age, stay duration).

---

## 💎 Subscription System & Boosts
TaskBot uses a "SubBoosts" system to unlock higher limits.

| Command | Description |
|----------|-------------|
| `/enablesubkey` | Activate a subscription key on your account. |
| `/subboost add` | Allocate SubBoosts from your account to the current server. |
| `/subboost remove` | Remove your SubBoosts from a server. |
| `/subboost status` | Displays your boost balance and current allocations. |
| `/checkkey` | Check the status of a key or your own subscription. |

---

## 👤 User (Public)
Commands accessible to all users.

| Command | Description |
|----------|-------------|
| `/help` | Displays the interactive help menu by category. |
| `/stats` | Displays your personal statistics (messages, voice time, boosts). |
| `/invites show` | Displays your total, valid, and invalid invitations. |
| `/level` | Displays your experience level and progress. |
| `/feedback` | Send a suggestion or bug report to the developers. |
| `/report` | Report a user for inappropriate behavior. |
| `/serverreport` | Report the current server for rule violations. |
| `/userappeal` | Submit an appeal following a user ban. |

---

## 📊 Automated Systems
*   **Anti-Phishing**: Proactive detection of malicious links via global database and external API. Centralized case management.
*   **Invite Tracking**: Smart calculation of invite validity based on invitee retention and activity.
*   **Boost Decay**: Servers lose 4 SubBoosts per month (requires subscription renewal).
*   **Auto-Moderation**: Account age verification upon entry and message content filtering.
*   **Voice Tracking**: Recording time spent in voice channels for statistics.
