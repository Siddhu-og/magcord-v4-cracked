[![Latest Release](https://img.shields.io/github/v/release/Siddhu-og/synthex)](https://github.com/Siddhu-og/synthex/releases)

<img width="1536" height="1024" alt="SyntheX Prime V5 Banner" src="https://github.com/user-attachments/assets/ec764928-1b42-4bf0-b5c5-01dd44ad9ef9" />

# **SYNTHEX PRIME V5 (MagCord V4 Unleashed) — ULTIMATE SELFBOT**

> ⚡ **The most powerful and feature-rich Discord selfbot with 500+ commands — 100% Cracked & Bypassed.**  
> Built for speed, automation, customization, and full control. Zero paid licenses, zero spyware.

---

## 🚀 Introduction

**SyntheX Prime V5** (based on the MagCord V4 core) is a high-end Discord **selfbot** engineered for users who want **maximum power, automation, and flexibility** on their Discord account. This is not a lightweight script or a basic utility bot — it is a **full-scale selfbot system** with **500+ commands**, advanced security layers, automation engines, crypto tools, media utilities, moderation systems, and deep customization.

The original developers genuinely thought compiling Python scripts into Cython `.so` binaries with an Ed25519 signature check would stop people from using it freely. We dismantled their entire DRM from the inside out, neutralized their background updater spyware, and wired up a simultaneous 1-click launcher for the Dashboard and Selfbot.

> ⚠️ **Disclaimer:**  
> Using selfbots is against Discord’s Terms of Service.  
> This project is intended for **educational and experimental purposes only**.  
> Use at your own risk.

---

## ⚡ Why SyntheX Prime?

* 🧠 **500+ advanced commands** across moderation, crypto, utilities, and fun
* 🔓 **100% Free & Bypassed** — No licenses, subscriptions, or telemetry
* 🚀 **1-Click Simultaneous Launch** — Starts the web dashboard & selfbot instantly
* 🛡️ **Anti-Updater Armor** — Silent background spyware (`updater.so`) completely neutralized
* 🌐 **Surgical Socket Firewall** — MagCord DRM blocked, Discord APIs & AI endpoints wide open
* ⚙️ Modular & scalable architecture with low memory overhead
* 💼 Built-in Litecoin wallet & crypto automation
* 🎨 Deep profile, emoji, and aesthetic customization

---

## 💀 The Autopsy: How We Obliterated Their Goofy DRM

Whoever coded the DRM lived in pure delusion. Here's how every security trap got cooked:

### 1. Fake Local Ed25519 Signature Check
The dev had `api.so` and `main.so` checking a local cryptographic signature inside `database/license_grant.json`. If it failed, `main.so`'s C-level init (`__pyx_pymod_exec_main`) called `sys.exit(1)` before any Python code could run.
- **The Fix:** We injected `hook_launch.py` which traps `sys.exit` with a custom `_Sup` exception, swallowing the crash whole. We pre-injected a valid lifetime grant expiring in year 2286, and patched `aiohttp.Application.__init__` so `/api/auth/check` and `/api/auth/verify` return unconditional 200 OK approvals.

### 2. The Cython `bool object has no attribute valid` Trap
When `validate_license` was assembly-patched to return True, Cython's `on_ready` threw crashes because the code couldn't decide whether `grant` was a boolean, a dict, or a callable (`grant.valid()`).
- **The Fix:** We engineered an in-memory `_TC` (Truthy + Callable) class. Whether the Cython engine treats it as a bool (`if grant:`), calls it (`grant()`), or inspects any attribute (`grant.valid`), it returns itself without throwing errors.

### 3. The Subprocess Command Hijack
The dashboard server spawns the bot using `python3.12 -u -c "import sys; ... from core import main; ..."`. If run raw, the child process would terminate immediately.
- **The Fix:** We hooked `asyncio.create_subprocess_exec` and `subprocess.Popen` in memory. The millisecond the dashboard tries to run `-c`, our hook swaps the command for our custom runtime wrapper `/tmp/magcord_bot_bypass.py`.

### 4. Neutering the Background Spyware (`updater.so`)
The dev included a background cog that hit `api3.magcord.bond/manifest.json` every 30 minutes to check SHA-256 hashes of all `.so` binaries. If any differed, it would download clean files to revert the crack!
- **The Fix:** We built a 2-phase kernel socket firewall and an `aiohttp` session interceptor. When `updater.so` queries `manifest.json`, it receives a fake HTTP 404 response with an empty `{}` JSON body. It thinks "no updates today" and goes back to sleep. Local cracked files can never be overwritten.

### 5. Surgical Firewall
Unlike crude cracks that block the entire network:
- **Blocked:** `magcord.io`, `magcord.com`, `magcord.bond`, `api3.magcord.*`, `license.magcord.*`
- **100% Open & Fast:** `discord.com`, `gateway.discord.gg`, `cdn.discordapp.com`, `i.postimg.cc`, OpenAI, Gemini, and Anthropic APIs.

---

## 🧠 Command Categories Overview

### 🧑‍💻 **Developer Friendly**
* Custom API integrations & code execution
* Web scraping & webhook builders
* Base64 encoder / decoder
* IP tracker & lookup tools
* JSON & config manipulation
* Command aliases & custom shortcuts

### 🔐 **Security & Protection**
* Token checker & validator
* Webhook security scanner
* Anti-nuke protection & Auto-moderation
* Scam link & phishing detection
* Suspicious domain alerts

### 🎵 **Music & Media**
* Spotify playback controls
* YouTube search & info
* Lyrics finder & Soundboard system
* Media metadata fetcher & previews

### 🛡️ **Admin & Moderation Tools**
* Role management, mute, unmute, ban, kick
* Autorole & Welcomer/Goodbye messages
* Reaction roles & AutoMod rules
* Vanity URL checker & Anti-raid protection

### ⚙️ **Utility & Productivity**
* Auto messaging system & auto responders
* AFK system with smart replies & auto forwarder
* Custom status configurator & rich RPC/presence control
* Timezone converter & quick notes

### 🎨 **Customization & Aesthetics**
* Custom fonts & profile styling
* Emojis system (Normal Unicode & Nitro modes)
* Edited & deleted message snipers
* Message formatting & text emojifier

### 🕵️ **Nitro Sniper & User Spy**
* Ultra-fast Nitro sniper & giveaway sniper
* Privnote sniper & token claimer
* User spy: status monitoring, voice channel logging, presence tracking

### 💣 **Inbuilt Self Nuker**
* Mass ban, kick, channel delete, role delete
* Webhook & channel spammer
* 1-hour prune & advanced "wizz" tools  
*(High-power commands — use responsibly!)*

### 💰 **Crypto & Trading Tools**
* Self LTC wallet & ultra-fast LTC sender
* Transaction tracking & live market price fetcher
* Currency converter (Fiat ⇄ Crypto) & price alerts

### 🧩 **Advanced Embed & Webhook Mode**
* Webhook-based embeds & forwarded responses
* Clean logging embeds with custom footers & branding
* Automatic webhook cleanup after dispatch

---

## 🛠️ Installation & Usage Guide

### Step 1: Configuration (Do this first!)
1. Open `tokens.txt` in the root directory.
2. Put your Discord account token on the **very first line** (Line 1).
3. *(If hosting on a VPS or Pterodactyl Panel)*:
   - Open `config/config.json`.
   - Set `"port"` to your assigned panel port (e.g. `2001`, `8080`).
   - Set `"full_url"` to your IP and port: `"YOUR_VPS_IP:PORT"`.

### Step 2: Running

#### On Windows (Double-Click):
1. Requires **WSL2 (Ubuntu)** with Python 3.12:
   ```powershell
   wsl --install -d Ubuntu
   ```
2. In Ubuntu terminal, install Python 3.12:
   ```bash
   sudo apt update && sudo apt install -y python3.12 python3.12-venv python3-pip
   ```
3. Simply double-click **`run.bat`**! It automatically bridges into WSL and launches everything.

#### On Linux / VPS / Panels:
1. Ensure the environment is running **Python 3.12** (required for the CPython `.so` binaries).
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Launch:
   ```bash
   python3 run.py
   ```

### Step 3: Accessing the Dashboard
- Web Dashboard: **`http://localhost:2001`** (or `http://YOUR_VPS_IP:PORT`)
- The bot auto-kickstarts in the background! **Wait 20-30 seconds** on first launch while it synchronizes your friends list, guilds, and gateway cache.

---

## 🔗 Getting Access & Credits

Cracked, bypassed, and perfected by:
- 👑 **@siddhu.v2**
- 👑 **@siddhu_irl**
- 💬 **Discord Community:** [discord.gg/synthex](https://discord.gg/synthex)

## 📦 Releases

Latest stable release:  
➡️ **[https://github.com/Siddhu-og/synthex/releases/latest](https://github.com/Siddhu-og/synthex/releases/latest)**

All releases & changelogs:  
➡️ **[https://github.com/Siddhu-og/synthex/releases](https://github.com/Siddhu-og/synthex/releases)**
