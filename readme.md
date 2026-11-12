[![Latest Release](https://img.shields.io/github/v/release/Siddhu-og/synthex)](https://github.com/Siddhu-og/synthex/releases)
[![Python](https://img.shields.io/badge/Python-3.12-blue)](https://python.org)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20WSL2-orange)](https://github.com/Siddhu-og/synthex/releases)
[![Discord](https://img.shields.io/badge/Discord-discord.gg%2Fsynthex-5865F2)](https://discord.gg/synthex)

# MagCord V4 — Cracked & Fully Bypassed

> ⚡ Full DRM removed. License bypass, updater spyware killed, 1-click simultaneous dashboard + selfbot startup.  
> No paid keys. No subscriptions. No clown behavior.

---

## 📸 Preview

> Dashboard + selfbot both firing up simultaneously on `run.bat` double click.

---

## 🔓 What's Bypassed

| System | Status |
|---|---|
| Ed25519 License Signature Check | ✅ Bypassed in-memory — Lifetime grant injected |
| `sys.exit()` Cython Death Trap | ✅ Neutralized — Exit suppressed at C-level import |
| Dashboard Auth (`/api/auth/check`) | ✅ Patched — Always returns authenticated |
| Bot Subprocess Command Injection | ✅ Hijacked — Custom wrapper swapped at spawn time |
| `updater.so` SHA-256 Integrity Checks | ✅ Killed — Gets fake 404s, never overwrites local files |
| MagCord License Renewal Loops | ✅ Intercepted at aiohttp layer |
| Raw Socket Telemetry | ✅ Kernel-level firewall — magcord.* domains hard blocked |

---

## ⚡ Features

- 🚀 **1-Click Launch** — `run.bat` or `run.py` starts the web dashboard and selfbot at the same time, no manual button clicking
- 🔐 **Permanent Lifetime Grant** — Fake license injected, good until year 2286, no renewal checks
- 🛡️ **Updater Nuked** — `updater.so` polls every 30 min to overwrite your files; it now gets served a fake empty response and goes back to sleep
- 🌐 **Surgical Firewall** — Only magcord telemetry domains are blocked; Discord, OpenAI, Gemini, image hosts are 100% untouched
- 🖥️ **Windows & Linux** — Works on Windows via WSL2 or directly on any Linux VPS/panel

---

## 🛠️ Setup & Usage

### Step 1 — Configuration

1. Open `tokens.txt` in the root folder
2. Put your Discord token on **Line 1**
3. *(Optional)* Adjust prefix, settings in `config/config.json`

**On a VPS or Pterodactyl Panel?**  
Open `config/config.json` and set:
```json
{
  "port": "YOUR_PANEL_PORT",
  "full_url": "YOUR_VPS_IP:YOUR_PANEL_PORT"
}
```
Then open `http://YOUR_VPS_IP:PORT` in your browser to access the dashboard.

---

### Step 2 — Running

#### 🪟 Windows (Recommended — Double Click)

Requirements: **WSL2 (Ubuntu)** + **Python 3.12** inside WSL

Install WSL if not already:
```powershell
wsl --install -d Ubuntu
```

Install Python 3.12 inside Ubuntu:
```bash
sudo apt update && sudo apt install -y python3.12 python3.12-venv python3-pip
```

Then just double-click:
```
run.bat
```

#### 🐧 Linux / VPS / Panel

Requirements: **Python 3.12** (the Cython `.so` binaries are compiled specifically for CPython 3.12)

```bash
pip install -r requirements.txt
python3 run.py
```

---

### Step 3 — Access Dashboard

```
http://localhost:2001
```
or if on a VPS:
```
http://YOUR_VPS_IP:PORT
```

**Wait 20-30 seconds** after the dashboard loads — the bot syncs Discord gateway, friends list, and guild cache in the background automatically.

---

## ⚠️ Important Notes

- ❌ **Never run `bypass.py` again** — The `.so` binaries are already patched. Re-running it corrupts them.
- ❌ **Never use `launch.py`** — It doesn't have bypass hooks. Always use `run.bat` or `run.py`.
- ✅ **All Discord, AI, and image APIs work normally** — The firewall is surgical.

---

## 📦 Releases

Latest release:  
➡️ [Magcord v4 License Bypassed](https://github.com/Siddhu-og/magcord-v4-cracked/releases/tag/MagCord)


---

## 👑 Credits

Cracked and maintained by:

- **@siddhu.v2**
- **@siddhu_irl**
- 💬 Community: [discord.gg/synthex](https://discord.gg/synthex)

---

## ⚠️ Disclaimer

This project is provided for **educational purposes only**.  
Using selfbots violates Discord's Terms of Service. Use at your own risk.  
The authors are not responsible for any account bans or actions taken against your account.
