# Vynix Studio Web

The official website and control center for **Vynix Studio**, a Minecraft technology and development studio. Vynix creates its own products, software, modpacks, shaders, and developer tools. It is not a marketplace or community project directory.

---

## ✨ Features

* 🔴 **Live Modrinth data for official Vynix PVP and VynixShader products**
* 🧭 Official product showcase
* 🛠️ Vynix Studio Control Center and local developer workspace
* 🌙 Dark Minecraft-inspired UI
* 📱 Fully responsive design
* 🔗 Official Vynix product links only

---

## 🛠️ Tech Stack

* **HTML5**
* **Tailwind CSS (CDN)**
* **Vanilla JavaScript**
* **Fetch API** for the two official Modrinth product integrations

No build tools or backend are required for the public static site. The developer workspace can save product status and studio records in browser storage, but it is not an authenticated server-management panel.

## Production and security boundary

This repository does not contain a backend, database, authentication flow, server-control API, file manager, or rate limiter. Browser-local studio records are not private security controls and are not published. See [SECURITY.md](SECURITY.md) before connecting a real Control Panel backend.

The site uses bounded, timeout-controlled Modrinth requests and escapes remote values before rendering them. Volumetric DDoS protection, trusted proxy handling, authentication, authorization, abuse limits, security headers, and private server workers must be configured in the CDN/WAF, reverse proxy, and backend layers described in [SECURITY.md](SECURITY.md).

---

## 📦 Project Structure

```
vynix-studio-web/
├── index.html
├── dashboard/index.html
├── CNAME
└── README.md
```

---

## 🚀 Getting Started

### Local Preview

Simply open **index.html** in your browser.

```bash
# optional local server
python -m http.server 8000
```

Then visit:

```
http://localhost:8000
```

---

## 🌐 Official Product API Data

The application uses Modrinth project and version endpoints only for the official Vynix PVP and VynixShader pages. It does not search, browse, recommend, or import arbitrary Modrinth projects.

---

## 📄 License

This project is provided for **Vynix Studio** and may be modified for personal or community Minecraft projects.

---

## 💜 Credits

* **Vynix Studio** — Website & design
* **Modrinth** — Live metadata for configured official products
* **Minecraft** — The platform Vynix Studio builds for

---

## 🎮 About

Vynix Studio Web is designed to present a **Minecraft technology studio**, combining a premium dark public site with a live product control center.
