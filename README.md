# 🚀 Starbound Outpost: Junior Astronaut Mission Trainer

A 2.5D space exploration and planetary habitat survival trainer designed for aspiring Junior Astronauts (ages 7–12) and space science enthusiasts. Take command of a surface outpost on the Moon (**Artemis Shackleton Crater**) or Mars (**Jezero Crater**), balancing core engineering life-support systems while reacting to real space weather and planetary hazards.

---

## 🌟 Key Features

- **Genuine Engineering Trade-offs**: Every action balances three critical systems:
  - ⚡ **Electrical Power**: Solar arrays, battery storage, and kilopower reactors.
  - 💧 **Life Support**: Closed-loop oxygen recovery and hydroponic greenhouse.
  - 🛡️ **Radiation Shielding**: Regolith storm shelters and hydrogen-rich water wall barriers.
- **Authentic NASA Science Integration**:
  - **NASA DONKI** (Space Weather Database of Notifications, Knowledge, and Information): Real-time solar flare classifications (M/X class), Coronal Mass Ejections (CME speeds), and geomagnetic storms (Kp index).
  - **NASA OSDR** (Open Science Data Repository): Spaceflight biology and plant growth research (Veggie plant chambers and musculoskeletal studies).
  - **NASA RadLab Dosimetry**: Absorbed radiation dose measurements and EVA exposure planning.
- **Interactive Emergency Mini-Games**: Manual valve isolation, plasma arc welding, magnetic field deflection, and electrostatic dust mitigation.
- **Capcom Tactical Uplink**: Tactical engineering calculations and mission advice.
- **Resilient Offline Architecture**: Automatic fallback to an authentic NASA scientific snapshot if offline or when running without an API key.

---

## ⚙️ Quick Start

### 1. Prerequisites
- [Node.js](https://nodejs.org/) (v20 or newer recommended; Node 22/26 fully supported)
- npm or bun

### 2. Installation
```bash
# Clone or extract the project, then install dependencies:
npm install
```

### 3. Configure Your Environment (`.env`)
Copy `.env.example` to `.env` (or edit the pre-configured `.env` file):

```bash
cp .env.example .env
```

Open `.env` in any text editor and paste your credentials:
```env
# NASA Open API Key (Free registration at https://api.nasa.gov)
NASA_API_KEY="PASTE_YOUR_NASA_API_KEY_HERE"

# Optional: Gemini API Key for Capcom Dialogue
GEMINI_API_KEY="PASTE_YOUR_GEMINI_API_KEY_HERE"

# Optional: Server Port & Environment
PORT=3000
NODE_ENV=development
```

> **Note on NASA API Key:** If you leave `NASA_API_KEY="PASTE_YOUR_NASA_API_KEY_HERE"`, Starbound Outpost automatically boots into **NASA BASELINE** mode using authentic bundled DONKI and OSDR telemetry snapshots. Once you paste your key and restart the server, the app automatically transitions to **NASA LIVE** streaming real-time solar events!

### 4. Run the Mission
```bash
# Launch development server
npm run dev

# Open your browser at:
http://localhost:3000
```

### 5. Run Verification Tests
```bash
npm test
```
All 45 mission simulation, engineering trade-off, and space weather unit tests will run and report status.

---

## 🎮 Controls

| Action | Keyboard / Mouse |
| :--- | :--- |
| **Move Astronaut** | `W`, `A`, `S`, `D` or `Arrow Keys` (or Click anywhere on surface) |
| **Inspect / Action** | `E` when near any station building (or Click station directly) |
| **Quick Station Selection** | `1`–`5` number keys |
| **Trainee Telemetry Lab** | Click `Trainee Lab` in header |
| **Space Data Codex** | Click `Sun Mood` badge or `Codex` button |
| **Mute / Unmute Audio** | `M` key |
| **Pause / Resume** | `P` or `Escape` key |
| **Restart Mission** | `R` key |

---

## 📂 Project Architecture

```
starbound-outpost/
├── server.ts                  # Express server & API routes (/api/nasa/*, /api/mission-advisor)
├── server/
│   └── spaceWeather.ts        # NASA DONKI/OSDR telemetry service, rate limiting & cache
├── src/
│   ├── App.tsx                # Main mission control shell & HUD
│   ├── firebase.ts            # Save state & trainee logbook (cloud + local storage)
│   ├── components/
│   │   ├── AdvisorModal.tsx   # Capcom tactical advisory modal
│   │   ├── Modals.tsx         # Station trade-off & space hazard mini-game modals
│   │   ├── TraineeDashboardModal.tsx # RadLab & OSDR countermeasures lab
│   │   └── CreditsModal.tsx   # Full scientific data attribution & sources
│   ├── game/
│   │   ├── rules.ts           # Core planetary game logic, difficulty & NASA formulas
│   │   ├── rules.test.ts      # Comprehensive test suite (45 test scenarios)
│   │   ├── OutpostCanvas.tsx  # 2.5D rendering engine & astronaut controller
│   │   ├── MiniGameManager.ts # Hazard minigame logic and telemetry
│   │   └── sound.ts           # Retro synthesized audio & atmospheric background music
│   └── data/
│       ├── donki-snapshot.json # Authentic baseline NASA DONKI snapshot
│       └── sources.ts         # Citation links to NASA Open APIs, DONKI, and OSDR
├── package.json               # Scripts, build commands, and dependencies
└── .env                       # API keys and local configuration
```

---

## 📜 Scientific Attribution & Disclaimers

Starbound Outpost is an independent educational simulator. Data citations:
- **NASA DONKI**: Courtesy of the Community Coordinated Modeling Center (CCMC) at NASA Goddard Space Flight Center and the Moon to Mars Space Weather Analysis Office.
- **NASA OSDR & GeneLab**: Courtesy of the NASA Open Science Data Repository.
- **NASA Planetary Datasets**: Surface radiation, gravity, and diurnal cycle measurements derived from published Artemis Lunar Exploration and Mars Science Laboratory / Perseverance rover mission data.
