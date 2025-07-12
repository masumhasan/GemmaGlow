# 🧠 Khidr - Offline AI Assistant Blueprint

## 💡 Project Goal

Create an offline-capable, multimodal AI assistant named **Khidr**, designed to help users with:

- Voice-based personal assistance
- Emergency support (calls, SMS, email)
- Persona-adaptive conversation (Elder, GenZ, Student)
- Offline tutoring and mental health support
- Real-time audio/video via self-hosted LiveKit
- Local memory, contact management, and natural learning from environment

---

## 🧱 Directory Structure

```bash
khidr/
├── main.py                     # Entry point
├── requirements.txt            # All dependencies
├── .env                        # Secrets like LiveKit keys
├── blueprint.txt               # Project setup and plan
│
├── assistants/
│   ├── gemma_engine.py         # Runs Gemma 3n locally
│   ├── prompt_builder.py       # Persona-specific prompt logic
│   └── memory.py               # TinyDB/SQLite based user memory
│
├── audio/
│   ├── stt_vosk.py             # Offline STT using Vosk
│   ├── tts_pico.py             # Offline TTS using PicoTTS
│   └── voice_loop.py           # Full loop: Listen → Think → Speak
│
├── livekit/
│   ├── token_manager.py        # Token generator for LiveKit
│   ├── live_stream.py          # Real-time voice/video room handler
│   └── emergency_room.py       # Emergency connect logic
│
├── contacts/
│   ├── contact_store.py        # Learn and store contacts
│   └── contact_utils.py        # Call/SMS/email trigger logic
│
├── vision/
│   └── emotion_detector.py     # Optional webcam mood detection
│
├── config/
│   └── persona_config.yaml     # Templates for Elder/GenZ/Tutor modes
│
└── data/
    └── user_logs.json          # Logs of interactions and emotions
```

---

## 📦 Requirements.txt

```txt
transformers
torch
sentencepiece
vosk
sounddevice
TTS
numpy
scipy
tinydb
python-dotenv
livekit
opencv-python
```

Install with:

```bash
pip install -r requirements.txt
```

---

## 🔐 .env Example

```env
LIVEKIT_API_KEY=your_api_key
LIVEKIT_API_SECRET=your_api_secret
LIVEKIT_URL=wss://your-livekit-server.com
```

---

## 🧠 Features

### 1. Offline STT

- Uses `vosk` for real-time mic transcription

### 2. Offline TTS

- Uses `pico2wave` or `Coqui TTS`

### 3. Offline LLM (Gemma 3n)

- Runs locally using HuggingFace transformers
- Supports persona-prompted responses

### 4. Local Contact Management

- Stores contacts in TinyDB or SQLite
- Triggers calls/SMS/emails (offline-capable via device)

### 5. Emergency Interaction

- “Call my wife”, “Email doctor” voice commands
- Uses LiveKit or device for real-time emergency response

### 6. Self-Hosted LiveKit

- Used for voice/video streaming
- Secure token auth via `token_manager.py`

### 7. Persona Modes

- Elder Mode → Calm, slow, formal
- GenZ Mode → Casual, funny, sarcastic
- Tutor Mode → Detailed, academic

### 8. Environmental Learning

- Learns about family/friends from speech
- Confirms before saving contact or memory

---

## ✅ Setup Checklist

1.

---

## 🏁 Next Steps

- Start with `stt_vosk.py` and `tts_pico.py`
- Build `gemma_engine.py` to run LLM offline
- Wire it all together in `main.py`
- Confirm LiveKit connection works for emergency mode

---

## 📅 Timeline

- Week 1: MVP (STT → Gemma → TTS loop)
- Week 2: Memory, contact logic, emergency actions
- Week 3: LiveKit streaming, persona fine-tuning
- Week 4: Vision/emotion, testing, Kaggle-ready packaging

