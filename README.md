```markdown
# 🤖 SARAH — Discord Bot & Web Dashboard

SARAH est un **bot Discord modulaire** accompagné d’un **dashboard web moderne**, conçu pour la gestion avancée de communautés (notamment Albion Online) et d’outils internes.

Le projet est pensé **production-ready**, avec une architecture claire et sécurisée séparant le bot, l’API interne et l’interface web.

---

## ✨ Fonctionnalités

### 🔹 Bot Discord
* **Gestion des calls / compositions** : ZvZ, events, dispatch.
* **Gestion financière** : Forges, dépôts/retraits, calculs automatiques.
* **Suivi des stocks** : Gestion des inventaires de guilde (ex: siphons Albion).
* **Système de permissions** : Modules activables/désactivables par guilde.
* **Infrastructure** : Base de données SQLite et API interne sécurisée par token.

### 🔹 Dashboard Web
* **Authentification** : Connexion via Discord OAuth.
* **Accès multi-guildes** : Interface dédiée pour les admins et utilisateurs.
* **Gestion temps réel** : Suivi des calls, compositions et finances via Server-Sent Events (SSE).
* **UI Moderne** : Interface fluide construite avec React et Tailwind CSS.

---

## 🧱 Architecture

```text
┌────────────┐       ┌────────────────┐
│  Discord   │◀─────▶│  Bot Discord   │
│            │       │     Python     │
└────────────┘       └───────┬────────┘
                             │ API interne (token)
                             ▼
┌──────────────────┐  ┌────────────────┐
│  Navigateur      │◀─▶│ Dashboard Web  │
│  Utilisateur     │  │    Next.js     │
└──────────────────┘  └────────────────┘

```

---

## 🛠️ Stack Technique

### **Bot / Backend**

* **Langage** : Python 3.11+
* **Librairies** : `discord.py`, `aiohttp`
* **Base de données** : SQLite
* **Communication** : API REST interne

### **Web**

* **Framework** : Next.js 15 (App Router)
* **Langage** : TypeScript / React
* **Styles** : Tailwind CSS
* **Auth** : NextAuth (Discord OAuth)
* **Update** : Server-Sent Events (SSE)

---

## 📁 Structure du Projet

```bash
.
├── bot/                # Code source du Bot Discord
│   ├── cogs/           # Modules et commandes
│   ├── api/            # Endpoints de l'API interne
│   ├── finance.db      # Base de données (SQLite)
│   └── main.py         # Point d'entrée du bot
│
├── webapps/            # Application Next.js
│   ├── src/
│   │   ├── app/        # Pages et routes
│   │   ├── components/ # Composants UI
│   │   └── lib/        # Utilitaires et hooks
│   └── next.config.mjs
│
├── docs/               # Documentation supplémentaire
├── .env.example        # Modèle des variables d'environnement
└── README.md

```

---

## ⚙️ Configuration (.env)

### **Bot / API**

```env
BOT_TOKEN=votre_token_discord
BOT_API_TOKEN=sarah-internal-token
BOT_INTERNAL_URL=[http://127.0.0.1:8765](http://127.0.0.1:8765)

```

### **Web**

```env
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=votre_secret_nextauth

DISCORD_CLIENT_ID=votre_id_client
DISCORD_CLIENT_SECRET=votre_secret_client

BOT_INTERNAL_URL=[http://127.0.0.1:8765](http://127.0.0.1:8765)
BOT_API_TOKEN=sarah-internal-token

```

---

## 🚀 Installation

### 1. Bot Discord

```bash
cd bot
python3 -m venv venv
source venv/bin/activate  # ou venv\Scripts\activate sur Windows
pip install -r requirements.txt
python main.py

```

### 2. Dashboard Web

```bash
cd webapps
npm install
npm run dev

```

---

## 🔐 Sécurité

* **Communication Web ↔ Bot** via token interne propriétaire.
* **Authentification obligatoire** via Discord pour l'accès au dashboard.
* **Permissions granulaires** basées sur les rôles Discord réels.
* **Endpoints protégés** : aucun accès public non autorisé.

---

## 📌 Roadmap

* [ ] Support PostgreSQL pour de plus gros volumes.
* [ ] Historique avancé & exports (CSV/PDF).
* [ ] Notifications temps réel croisées Discord ↔ Web.
* [ ] Mode Multi-tenant.
* [ ] API publique documentée (Swagger).

---

## 👤 Auteur

**Mickaël Chamberod** - *Lausen IT Consulting*
