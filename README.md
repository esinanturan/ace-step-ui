<p align="center">
  <img src="https://img.shields.io/badge/🎵-ACE--Step_UI-ff69b4?style=for-the-badge&labelColor=1a1a1a" alt="ACE-Step UI" height="60">
</p>

<h1 align="center">ACE-Step UI</h1>

<p align="center">
  <strong>A professional, local-first music generation studio for <a href="https://github.com/ace-step/ACE-Step">ACE-Step 1.5</a></strong>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#demo">Demo</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#configuration">Configuration</a> •
  <a href="#credits">Credits</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-18.3-61DAFB?style=flat-square&logo=react" alt="React">
  <img src="https://img.shields.io/badge/Express-4.x-000000?style=flat-square&logo=express" alt="Express">
  <img src="https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat-square&logo=typescript" alt="TypeScript">
  <img src="https://img.shields.io/badge/TailwindCSS-3.x-06B6D4?style=flat-square&logo=tailwindcss" alt="TailwindCSS">
  <img src="https://img.shields.io/badge/SQLite-3-003B57?style=flat-square&logo=sqlite" alt="SQLite">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License">
</p>

---

## Demo

<p align="center">
  <img src="docs/demo.gif" alt="ACE-Step UI Preview" width="100%">
</p>

## Features

### 🎵 AI Music Generation
| Feature | Description |
|---------|-------------|
| **Full Song Generation** | Create complete songs with vocals and lyrics up to 4+ minutes |
| **Instrumental Mode** | Generate instrumental tracks without vocals |
| **Custom Mode** | Fine-tune BPM, key, time signature, and duration |
| **Style Tags** | Define genre, mood, tempo, and instrumentation |
| **Batch Generation** | Generate multiple variations at once |
| **Thinking Mode** | Let AI enhance your prompts automatically |

### 🎨 Advanced Parameters
| Feature | Description |
|---------|-------------|
| **Reference Audio** | Use any audio file as a style reference |
| **Audio Cover** | Transform existing audio with new styles |
| **Repainting** | Regenerate specific sections of a track |
| **Seed Control** | Reproduce exact generations for consistency |
| **Inference Steps** | Control quality vs speed tradeoff |

### 🎤 Lyrics & Prompts
| Feature | Description |
|---------|-------------|
| **Lyrics Editor** | Write and format lyrics with structure tags |
| **Format Assistant** | AI-powered caption and lyrics formatting |
| **Prompt Templates** | Quick-start with genre presets |
| **Reuse Prompts** | Clone settings from any previous generation |

### 🎧 Professional Interface
| Feature | Description |
|---------|-------------|
| **Spotify-Inspired UI** | Clean, modern design with dark/light mode |
| **Bottom Player** | Full-featured player with waveform and progress |
| **Library Management** | Browse, search, and organize all your tracks |
| **Likes & Playlists** | Organize favorites into custom playlists |
| **Real-time Progress** | Live generation progress with queue position |
| **LAN Access** | Use from any device on your local network |

### 🛠️ Built-in Tools
| Feature | Description |
|---------|-------------|
| **Audio Editor** | Trim, fade, and apply effects with AudioMass |
| **Stem Extraction** | Separate vocals, drums, bass, and other with Demucs |
| **Video Generator** | Create music videos with Pexels backgrounds |
| **Gradient Covers** | Beautiful procedural album art (no internet needed) |

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | React 18, TypeScript, TailwindCSS, Vite |
| **Backend** | Express.js, SQLite, better-sqlite3 |
| **AI Engine** | [ACE-Step 1.5](https://github.com/ace-step/ACE-Step) |
| **Audio Tools** | AudioMass, Demucs, FFmpeg |

## Requirements

| Requirement | Specification |
|-------------|---------------|
| **Node.js** | 18 or higher |
| **Python** | 3.10+ (3.11 recommended) |
| **NVIDIA GPU** | 8GB+ VRAM (12GB+ recommended) |
| **FFmpeg** | For audio processing |
| **uv** | Python package manager (recommended) |

## Quick Start

```bash
# 1. Start ACE-Step API (in ACE-Step directory)
cd /path/to/ACE-Step
uv run acestep-api --port 8001

# 2. Start ACE-Step UI (in another terminal)
cd ace-step-ui
./start.sh
```

Open **http://localhost:3000**

## Installation

### 1. Install ACE-Step

```bash
# Clone ACE-Step
git clone https://github.com/ace-step/ACE-Step
cd ACE-Step

# Create virtual environment and install
uv venv
uv pip install -e .

# Models download automatically on first run (~5GB)
cd ..
```

### 2. Install ACE-Step UI

```bash
# Clone this repository
git clone https://github.com/fspecii/ace-step-ui
cd ace-step-ui

# Run setup script
./setup.sh
```

**Or manually:**

```bash
# Install frontend dependencies
npm install

# Install server dependencies
cd server
npm install
cd ..

# Copy environment file
cp server/.env.example server/.env
```

## Usage

### Step 1: Start ACE-Step API Server

```bash
cd /path/to/ACE-Step
uv run acestep-api --port 8001
```

Wait for "Application startup complete" before proceeding.

### Step 2: Start ACE-Step UI

```bash
cd ace-step-ui
./start.sh
```

**Or manually in two terminals:**

```bash
# Terminal 1 - Backend
cd server && npm run dev

# Terminal 2 - Frontend
npm run dev
```

### Step 3: Open the UI

| Mode | URL |
|------|-----|
| Local | http://localhost:3000 |
| LAN | http://YOUR_IP:3000 |

On first launch, you'll be asked to set a username. This is stored locally.

## Configuration

### Environment Variables

Edit `server/.env`:

```env
# Server
PORT=3001
NODE_ENV=development

# ACE-Step API
ACESTEP_API_URL=http://localhost:8001

# Database
DATABASE_PATH=./data/acestep.db

# Storage
AUDIO_DIR=./public/audio

# Optional: Pexels API for video backgrounds
PEXELS_API_KEY=your_key_here
```

### LAN Access

ACE-Step UI automatically supports LAN access. Start the servers and access from any device:

1. Find your computer's IP: `hostname -I` (Linux) or `ipconfig` (Windows)
2. Open `http://YOUR_IP:3000` on any device

## Generation Modes

### Simple Mode
Enter a description of the music you want. The AI handles the rest.

### Custom Mode
Fine-tune every parameter:

| Parameter | Description |
|-----------|-------------|
| **Title** | Song title |
| **Lyrics** | Full lyrics with structure tags `[Verse]`, `[Chorus]`, etc. |
| **Style** | Genre, mood, instruments, tempo descriptors |
| **Duration** | 30-240 seconds |
| **BPM** | 60-200 beats per minute |
| **Key** | Musical key (C major, A minor, etc.) |
| **Time Signature** | 4/4, 3/4, 6/8, etc. |

### Advanced Settings

| Setting | Description |
|---------|-------------|
| **Inference Steps** | Higher = better quality, slower (default: 60) |
| **Guidance Scale** | Prompt adherence strength (default: 15) |
| **Batch Size** | Number of variations to generate |
| **Thinking Mode** | AI prompt enhancement |
| **Random Seed** | For reproducible results |

## Built-in Tools

### Audio Editor
Click the edit icon on any song to open AudioMass:
- Cut, copy, paste audio
- Apply fades and effects
- Export in multiple formats

### Stem Extraction
Separate any song into:
- 🎤 Vocals
- 🥁 Drums
- 🎸 Bass
- 🎹 Other instruments

### Video Generator
Create music videos with:
- Pexels stock footage (requires API key)
- Gradient animations
- Lyrics overlay
- Album art display

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **ACE-Step API not reachable** | Ensure `uv run acestep-api --port 8001` is running |
| **CUDA out of memory** | Close other GPU apps, reduce duration/batch size |
| **Songs show 0:00 duration** | Install FFmpeg: `sudo apt install ffmpeg` |
| **LAN access not working** | Check firewall allows ports 3000 and 3001 |
| **Liked songs not saving** | Refresh page, check browser console for errors |

## Project Structure

```
ace-step-ui/
├── components/           # React components
│   ├── CreatePanel.tsx   # Main generation form
│   ├── Player.tsx        # Bottom audio player
│   ├── LibraryView.tsx   # Song library
│   └── ...
├── server/
│   ├── src/
│   │   ├── routes/       # API endpoints
│   │   ├── services/     # Business logic
│   │   └── db/           # SQLite database
│   ├── public/
│   │   ├── audio/        # Generated audio files
│   │   └── demucs-web/   # Stem extraction UI
│   └── audio-editor/     # AudioMass editor
├── services/             # Frontend API client
├── context/              # React context providers
└── docs/                 # Documentation & assets
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/generate` | Start music generation |
| `GET` | `/api/generate/status/:id` | Get job status |
| `GET` | `/api/songs` | Get user's songs |
| `POST` | `/api/songs/:id/like` | Toggle like |
| `GET` | `/api/playlists` | Get playlists |
| `POST` | `/api/playlists` | Create playlist |

## Development

```bash
# Development mode with hot reload
./start.sh

# Build for production
npm run build
cd server && npm run build
```

## Credits

- **[ACE-Step](https://github.com/ace-step/ACE-Step)** - AI music generation model
- **[AudioMass](https://github.com/pkalogiros/AudioMass)** - Web audio editor
- **[Demucs](https://github.com/facebookresearch/demucs)** - Audio source separation
- **[Pexels](https://www.pexels.com)** - Stock video backgrounds

## License

This project is open source under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! Please feel free to:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

<p align="center">
  Made with ❤️ for the open-source AI music community
</p>
