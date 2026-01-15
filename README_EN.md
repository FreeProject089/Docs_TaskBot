# 🤖 TaskBot - The Ultimate Discord Assistant

[Version Française](./README.md)

[![Discord.js](https://img.shields.io/badge/discord.js-v14-blue.svg)](https://discord.js.org)
[![Node.js](https://img.shields.io/badge/node.js->=18.0.0-green.svg)](https://nodejs.org)
[![SQLite](https://img.shields.io/badge/database-SQLite3-orange.svg)](https://www.sqlite.org)

TaskBot is a versatile and powerful Discord bot designed to automate your server management. It combines a **Join-To-Create** system, advanced **Ticket** management, customizable **Welcome Messages**, and a unique **Tiered Subscription** system.

---

## ✨ Key Features

*   **🎮 Join-To-Create (JTC)**: Temporary voice channels with a full control panel (Rename, Limit, Kick, Lock, Presets).
*   **🎫 Ticket System**: Multi-category management, automatic archiving, and ticket transfers.
*   **👋 Welcome & Goodbye**: Dynamically generated images (Canvas) with live preview.
*   **💎 Subscription System**: Three tiers (Classic, Premium, Ultra) unlocking higher limits via SubBoosts.
*   **🛡️ Moderation & Security**: Anti-Raid (Account Age), Anti-Phishing with global database, and Auto-Moderation.
*   **📩 Invite Tracking**: Smart invite tracking system with validity checks (Criteria: Account age, voice time, messages).
*   **📊 Statistics**: Precise activity tracking (messages, voice time) and boosts.

👉 **[View Detailed Features List (FEATURES_EN.md)](./FEATURES_EN.md)**

---

## 🚀 Quick Start

### 1. Prerequisites
*   [Node.js](https://nodejs.org/) v18 or higher.
*   A Discord developer account and a bot created on the [Developer Portal](https://discord.com/developers/applications).

### 2. Cloning and Dependencies
```bash
git clone https://github.com/your-repo/taskbot.git
cd taskbot
npm install
```

### 3. Configuration
Create a `.env` file at the root of the project:
```env
DISCORD_TOKEN=your_token_here
CLIENT_ID=your_client_id_here
CLIENT_SECRET=your_client_secret_here
```

### 4. Deploying Commands
```bash
npm run deploy
```

### 5. Launch
```bash
# Production Mode
npm start

# Development Mode (with auto-reload)
npm run dev
```

---

## 🗃️ Technical Architecture

*   **Language**: JavaScript (Node.js)
*   **Library**: Discord.js v14
*   **Database**: SQLite3 (via better-sqlite3)
*   **Image Engine**: Canvas (for welcome messages)
*   **Scheduling**: Node-cron (for daily/monthly tasks)

---

## 💎 Subscription Model

| Benefits | Classic | Premium | Ultra |
|-----------|-----------|---------|-------|
| **SubBoosts** | 0 | 5 | 12 |
| **JTC Lobbies** | 1 | 3 | 6 |
| **JTC Presets** | 1 | 2 | 3 |
| **Ticket Types** | 3 | 5 | 8 |

---

## 📝 License
This project is under a private license. Any reproduction or distribution without authorization is prohibited.
