# Vynix Studio Web

A modern Minecraft project discovery platform for **Vynix Studio**. The website uses **live Modrinth and CurseForge APIs** to display real Minecraft projects, modpacks, plugins, shaders, and resource packs without using fake data.

---

## ✨ Features

* 🔴 **Live Modrinth API integration**
* 🟠 **Live CurseForge API integration**
* 🔍 Real-time project search
* 📂 Category filters
* 📦 Project cards with real metadata
* 🌙 Dark Minecraft-inspired UI
* 📱 Fully responsive design
* 🚀 **100,000+ Modrinth projects supported**
* ➕ **Load More** system for progressive browsing
* 🔗 Official external links only (Modrinth / CurseForge)

---

## 🛠️ Tech Stack

* **HTML5**
* **Tailwind CSS (CDN)**
* **Vanilla JavaScript**
* **Fetch API**

No build tools or backend are required.

---

## 📦 Project Structure

```
vynix-studio-web/
├── index.html
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

## 🌐 Modrinth API Example

```js
async function fetchProjects(offset = 0, limit = 100) {
  const response = await fetch(
    `https://api.modrinth.com/v2/search?limit=${limit}&offset=${offset}`
  );

  return await response.json();
}
```

---

## 📄 License

This project is provided for **Vynix Studio** and may be modified for personal or community Minecraft projects.

---

## 💜 Credits

* **Vynix Studio** — Website & design
* **Modrinth** — Live project data
* **CurseForge** — Additional project data
* **Minecraft Community** — Amazing mods, modpacks, shaders, plugins, and resource packs

---

## 🎮 About

Vynix Studio Web is designed to feel like a **modern Minecraft discovery platform**, combining a premium dark UI with live API-powered project browsing for the Minecraft community.
