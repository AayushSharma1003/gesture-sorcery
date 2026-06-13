# 🔮 Gesture Sorcery — The Relic

![Made with JavaScript](https://img.shields.io/badge/Made%20with-JavaScript-f7df1e?style=for-the-badge&logo=javascript&logoColor=black)
![MediaPipe](https://img.shields.io/badge/MediaPipe-Hands-blue?style=for-the-badge&logo=google&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-Canvas%202D-red?style=for-the-badge)
![Web Audio](https://img.shields.io/badge/Web%20Audio-API-9b59b6?style=for-the-badge)
![No Install](https://img.shields.io/badge/No%20Install-Just%20a%20Browser-27ae60?style=for-the-badge)
![Live](https://img.shields.io/badge/Live-GitHub%20Pages-0366d6?style=for-the-badge&logo=github)

> *"To wield the power of the ancient relic, you must hold the orb. But all power comes with a price."*

Wield four ancient powers through your webcam — no controllers, no plugins, just your hands.

**[🌐 Try it live →](https://aayushsharma1003.github.io/gesture-sorcery/)**

---

<!-- Add your best screenshot here — the sword or fire one works great -->
<!-- ![Gesture Sorcery in action](your-screenshot.png) -->

---

## ✨ The Powers

| Gesture | Power | Effect |
|---|---|---|
| ✊ **Fist** | Energy Blast | A charged blue beam fires from your fist, aimed along your forearm |
| 🖐 **Open Palm** | Flame Stream | A roaring fire cone — white hot at the core, burning to embers at the edges |
| ✊✊ **Both Fists Together** | Arcane Shield | A rune-circle shield materializes with rotating sigils and cracking energy |
| ✌️ **Peace Sign** (hold) | Soul Blade | Summons a blade into your hand — swing fast for light trails and swoosh sounds. Peace sign again to dissolve it |

### 🎙️ Voice Amplification
Speak a power's name while gesturing to supercharge it for ~4 seconds:

- **"blast"** or **"beam"** → energy blast amplified
- **"fire"** or **"flame"** or **"agni"** → flame stream amplified  
- **"shield"** or **"protect"** → shield amplified
- **"sword"** or **"blade"** → blade amplified

> Voice works on Chrome/Edge only (Web Speech API). Gestures always work regardless.

---

## ⚠️ The Price

A **Vitality bar** drains while you cast. Let it hit zero and the relic rejects you — you're sent back to the temple. The Keeper warned you.

Press **ESC** to voluntarily return the power. The Keeper always has something to say.

---

## 🏛️ How It Works

```
Webcam feed
    ↓
MediaPipe Hands (21 landmarks per hand @ 30+ FPS)
    ↓
Gesture classifier (fist / open / peace / none)
    ↓
Power state machine
    ├── Blast: beam drawn along wrist→knuckle vector
    ├── Fire: particle cone, 9-16 particles/frame, additive blend
    ├── Shield: rotating rune rings + canvas arc geometry  
    └── Sword: blade bound to hand, velocity-triggered swoosh trails
    ↓
Canvas 2D renderer + Web Audio API synthesizer
    ↓
You feel like a wizard
```

---

## 🛠️ Tech Stack

- **[MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands)** — real-time hand landmark detection, runs entirely in browser via WebAssembly
- **HTML5 Canvas 2D** — particle systems, additive blending, sword trails, rune rendering
- **Web Audio API** — fully synthesized sounds: beam hum, fire roar, shield shimmer, blade swoosh, temple drone
- **Web Speech API** — continuous keyword recognition for voice amplification (Chrome/Edge)
- **Vanilla JS** — zero frameworks, zero dependencies beyond MediaPipe CDN
- **CSS** — the entire temple scene (pillars, god rays, dust motes, pedestal, old man) is pure CSS + DOM

---

## 🚀 Running Locally

No build step. No install. Literally just:

```bash
git clone https://github.com/AayushSharma1003/gesture-sorcery.git
cd gesture-sorcery
# open index.html in Chrome
open index.html
```

Camera and voice require HTTPS in production — GitHub Pages handles that automatically.

---

## 💡 Tips for Best Experience

- **Face a light source** — backlighting makes hand detection unreliable. Face a window or lamp.
- **Keep hands fully in frame** — especially for the peace sign, make sure both fingers are visible.
- **Sword + fire simultaneously** — summon the blade with your right hand (peace sign), then open your left palm. Dual wielding is the showcase.
- **Voice + gesture combo** — shout "fire" while streaming flame for the amplified version. It's a lot.

---

## 📁 Project Structure

```
gesture-sorcery/
└── index.html          # the entire project — temple, powers, audio, everything
```

One file. 887 lines. No node_modules folder. Deploys in 30 seconds.

---

## 🧠 How Gesture Detection Works

MediaPipe returns 21 3D landmarks per hand. Gesture classification is pure geometry — no ML beyond the landmark model itself:

```
Fist   → all 4 fingertips closer to wrist than their PIP joints
Open   → 3+ fingertips extended past their PIP joints  
Peace  → index + middle extended, ring + pinky folded
```

Aim direction for blast and fire is the **wrist → middle knuckle vector** (landmarks 0 → 9), giving you natural, intuitive aiming that follows your forearm.

---

## 👤 Author

**Aayush Sharma** — B.Tech CSE, Bennett University  
NLP researcher | ML practitioner | apparently also a wizard now

[![GitHub](https://img.shields.io/badge/GitHub-AayushSharma1003-181717?style=flat-square&logo=github)](https://github.com/AayushSharma1003)

---

## 📄 License

MIT — do whatever you want with it. If you build something cool on top of this, I'd love to see it.

---

