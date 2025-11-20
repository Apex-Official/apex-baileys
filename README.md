تمام 😎🔥، هعمل لك نسخة Markdown جاهزة كـ README.md لــ APEX Baileys، بنفس تنسيق TanjiroDev، بالألوان الداكنة/أحمر عبر GitHub Badges، وكل الأقسام جاهزة:

<div align='center'>
  <h1>💀 APEX Baileys — WhatsApp Multi-Device API 💀</h1>
  <img src="https://raw.githubusercontent.com/Apex-Official/apex-baileys/main/banner-neon.png" width="600"/>
</div>

<div align='center'>
Enhanced WhatsApp Web API library by RADIO
</div>

[🌐 Visit Official Site](https://apex-official.github.io)

---

## Fixed Issues
- **lid** - Core connection fixes
- **Sessions** - Dual authentication support:
  - QR Code Login
  - 8-Digit Pairing Code Login

## Enhanced Features
- Optimized group performance
- Full media support (Images, Audio, Video, Documents, Stickers)
- Advanced session management
- Clean error handling
- Auto reconnect system
- Developer-friendly API

## Installation

Use the latest stable release:

```bash
npm i git+https://github.com/Apex-Official/apex-baileys.git
# or
yarn add git+https://github.com/Apex-Official/apex-baileys.git

Then import your code using:

import { makeWASocket } from "apex-baileys"
// or
const { default: makeWASocket } = require("apex-baileys")


---

Connecting Account

You can connect via QR Code or Pairing Code.

QR Code Example

const sock = makeWASocket({
    printQRInTerminal: true,
    browser: Browsers.ubuntu('My App')
})

Scan the QR with WhatsApp and login instantly.

Pairing Code Example

const sock = makeWASocket({ printQRInTerminal: false })

// Normal Pairing
if(!sock.authState.creds.registered){
    const number = 'XXXXXXXXXXX'
    const code = await sock.requestPairingCode(number)
    console.log(code)
}

// Custom Pairing
if(!sock.authState.creds.registered){
    const pair = "12345678"
    const number = 'XXXXXXXXXXX'
    const code = await sock.requestPairingCode(number, pair)
    console.log(code)
}

Full History & Browser Config

const sock = makeWASocket({
    browser: Browsers.macOS('Desktop'),
    syncFullHistory: true
})


---

Saving & Restoring Sessions

import makeWASocket, { useMultiFileAuthState } from "apex-baileys";

const { state, saveCreds } = await useMultiFileAuthState('auth_info_baileys')
const sock = makeWASocket({ auth: state })
sock.ev.on('creds.update', saveCreds)

> useMultiFileAuthState saves credentials in a single folder for easy reconnects without QR.




---

Handling Events

sock.ev.on('messages.upsert', ({ messages }) => {
    for(const m of messages){
        console.log(m)
        await sock.sendMessage(m.key.remoteJid, { text: "Hello from APEX 🔥" })
    }
})

All events: BaileysEventMap



---

Example Project

1. Clone repository



git clone https://github.com/Apex-Official/apex-baileys.git
cd apex-baileys
npm install
node example.js


---

Plugins Example

// Auto-reply
sock.ev.on('messages.upsert', async ({ messages }) => {
  for(const m of messages){
    if(m.message?.conversation?.includes("hi")){
      await sock.sendMessage(m.key.remoteJid, { text: "Hello 👋" })
    }
  }
})

// Welcome group members
sock.ev.on('group-participants.update', async (update) => {
  for(const participant of update.participants){
    await sock.sendMessage(update.id, { text: `Welcome ${participant} to the group! 🌟` })
  }
})


---

Developer

RADIO — Lead Developer
GitHub: Apex-Official


---

Version

v1.0.0 — Experimental


---

Support

⭐ If you like the project, star the repo!
Your support keeps the project aliveكثر
