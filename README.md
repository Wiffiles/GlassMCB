
# GlassMCB - Glass Minecraft Bridge

**Version:** 1.0.0  
**Developer:** Enzo  
**License:** THE UNLICENSED

A web-based Minecraft client that lets you join real Minecraft servers directly from your browser. Powered by **Mineflayer** on the backend and **Three.js** for world rendering.

---

## What Is GlassMCB?

GlassMCB is a browser-based Minecraft bridge — you connect to any Minecraft Java server (versions 1.8 through 1.21) from a web page. The backend spawns a Mineflayer bot that connects to the actual Minecraft server, and your browser controls it in real-time via WebSocket.

---

## Prerequisites

| Requirement | Version |
|---|---|
| **Node.js** | 18.x or higher (20+ recommended) |
| **npm** | Comes with Node.js |
| **Minecraft Server** | Any Java Edition server (1.8 - 1.21) |

### Install Node.js

- **Windows/Mac:** Download from [nodejs.org](https://nodejs.org/)
- **Linux (Ubuntu/Debian):** `sudo apt install nodejs npm`
- **Verify:** `node --version` should show v18+ or v20+

---

## How to Run

### Step 1: Extract the ZIP

Extract `glassmcb.zip` to a folder on your computer.

```bash
cd glassmcb
```

### Step 2: Install Dependencies

```bash
npm install
```

This will download all required packages (Express, Socket.IO, Mineflayer, Three.js, etc.).

**Note:** The `canvas` package may require native build tools:
- **Windows:** Install Visual Studio Build Tools or `npm install --global windows-build-tools`
- **Mac:** Install Xcode Command Line Tools: `xcode-select --install`
- **Linux:** `sudo apt install build-essential libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev`

### Step 3: Start the Server

```bash
npm start
```

For development (auto-restart on file changes):
```bash
npm run dev
```

### Step 4: Open in Browser

Navigate to: **http://localhost:3000**

The app works best in **Chrome**, **Firefox**, or **Edge**.

---

## Controls (In-Game)

| Key | Action |
|---|---|
| **W A S D** | Move |
| **Space** | Jump |
| **Shift** | Sneak |
| **Ctrl** | Sprint |
| **Mouse** | Look around (requires pointer lock) |
| **Left Click** | Attack / Break block |
| **Right Click** | Interact / Place block |
| **1-9** | Hotbar slots |
| **Scroll** | Change hotbar slot |
| **E** | Open/Close inventory |
| **T** | Open chat |
| **/** | Open command input |
| **Q** | Drop item |
| **Esc** | Pause menu / Close UI |
| **F3** | Toggle debug overlay |
| **Tab** | Show player list |

---

## Features

### Implemented
- Username prompt on first visit
- Minecraft-themed main menu with animated background
- Multiplayer server browser (add/edit/delete servers)
- Direct connect to any server IP
- Real-time connection via WebSocket
- Three.js 3D world rendering with block colors
- Chunk loading and unloading
- First-person camera following bot position
- Full HUD: health, hunger, XP bar, hotbar, crosshair
- Chat system (send/receive)
- Settings screen (FOV, render distance, sensitivity, etc.)
- Pause menu (ESC)
- Disconnect screen with reconnect
- Minecraft-themed UI throughout
- Version selector (1.8 - 1.21)

### Server-Side
- Express.js HTTP server
- Socket.IO WebSocket bridge
- Mineflayer bot per connected user
- Event forwarding (chat, health, position, chunks, entities)
- User profile storage (JSON)
- Block color mapping for all versions

---

## Project Structure

```
glassmcb/
├── server/
│   ├── index.js          # Express + Socket.IO server
│   ├── bot.js            # Mineflayer bot management
│   ├── worldRenderer.js  # Texture atlas + block colors
│   ├── versionMap.js     # Supported versions config
│   └── users.json        # User profiles
├── client/
│   ├── index.html        # App shell
│   ├── app.css           # Minecraft-themed styles
│   ├── app.js            # All frontend logic
│   └── textures/         # Texture directories (1.8 - 1.21)
├── public/
│   └── fonts/            # Minecraft font files
├── package.json          # Dependencies
└── README.md             # This file
```

---

## Supported Minecraft Versions

| Version Key | Mineflayer Version |
|---|---|
| 1.8 | 1.8.9 |
| 1.12 | 1.12.2 |
| 1.16 | 1.16.5 |
| 1.18 | 1.18.2 |
| 1.19 | 1.19.4 |
| 1.20 | 1.20.4 |
| 1.21 | 1.21 |

---

## Troubleshooting

### Connection Issues
- Make sure the target Minecraft server is online
- Check that the server IP and port are correct (default: 25565)
- Some servers have anti-bot protection and may kick the bot

### Canvas Build Errors
If `npm install` fails on the `canvas` package:
```bash
# Skip canvas (optional - block colors work without it)
npm install --omit=optional
```

### Port Already in Use
Change the port: `PORT=8080 npm start`

### Can't Click in Game
You need to click on the game canvas to activate pointer lock. The browser will ask for permission to capture your mouse.

### Chunks Not Rendering
The world uses colored blocks as a fallback when no texture pack is installed. Install Faithful 32x textures in the `client/textures/` folders for full texture support.

---

## Adding Textures (Optional)

For full texture support:
1. Download Faithful 32x for your desired Minecraft version
2. Extract block textures to `client/textures/{version}/blocks/`
3. Restart the server to generate atlas files

---

## Development

### Tech Stack
- **Runtime:** Node.js 20+
- **Backend:** Express.js + Socket.IO
- **Minecraft Protocol:** Mineflayer
- **World Rendering:** Three.js (WebGL)
- **UI:** Vanilla HTML/CSS/JS with Minecraft styling

### Environment Variables
| Variable | Default | Description |
|---|---|---|
| `PORT` | 3000 | HTTP server port |

---

*GlassMCB - built by Enzo (Wiffiles). Play anywhere. Join everything.*
