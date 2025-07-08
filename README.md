
# 🤖 ITSAROBO: Real-Time AI Assistant for UPES

ITSAROBO is a custom-built AI chatbot designed to answer queries related to UPES using real-time web search, a smart LLM-powered summarization pipeline, and voice-based interaction. It runs locally, privately, and efficiently — all using open tools like Docker and SearxNG.

---

## 📌 Project Workflow

```
🎤 Voice Query
 ↓
🔍 SearxNG (Private Web Search)
 ↓
📄 JSON Results
 ↓
🧠 LLM Summarization
 ↓
🔊 Text-to-Speech Output
```

---

## ⚙️ Tech Stack Overview

| Component        | Tool / Library Used                |
|------------------|------------------------------------|
| Web Search       | SearxNG (self-hosted)              |
| Summarization    | LLMs via OpenRouter (e.g., Mistral)|
| Semantic Matching| Sentence Transformers (MiniLM)     |
| Voice Input      | `speech_recognition` (Google STT)  |
| Voice Output     | `pyttsx3` or `gTTS`                |
| Containerization | Docker                             |

---

## 🧰 Getting Started (Local Setup)

### 1. Clone the Repository

```bash
git clone https://github.com/hima-97435/ITSAROBO
cd itsarobo-ai-bot
```

### 2. Install Docker Desktop

Make sure Docker Desktop is installed and running on your machine.

---

## 🛠 Setting Up SearxNG (Private Search Engine)

### Option 1: Use Included Config

This project is already configured to use a local SearxNG instance with your own settings.

### Steps:

1. Clone the SearxNG Docker repo (or use the config folder in this repo)
2. Place your `settings.yml` file inside a folder named `searxng-config`

---

### 🧪 Running the Container

```bash
docker run -d \
  --name searxng \
  -p 8080:8080 \
  -v ${PWD}/searxng-config:/etc/searxng \
  searxng/searxng:latest
```

---

### 🔁 Usage

- ✅ Start:  
  ```bash
  docker start searxng
  ```

- 🛑 Stop:  
  ```bash
  docker stop searxng
  ```

---

## 🧠 How the Bot Works

1. User speaks a query (or types it)
2. The query is sent to SearxNG to fetch real-time search results
3. Semantic search filters the best results
4. The top result is passed to an LLM to summarize the page
5. The answer is converted to audio using TTS and spoken aloud
