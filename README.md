🤖 ITSAROBO: Real-Time AI Assistant for UPES
ITSAROBO is a custom-built AI chatbot designed to answer queries related to UPES using real-time web search, a smart LLM-powered summarization pipeline, and voice-based interaction. It runs locally, privately, and efficiently — all using open tools like Docker and SearxNG.

📌 Project Workflow
text
Copy
Edit
🎤 Voice Query
   ↓
🔍 SearxNG (Private Web Search)
   ↓
📄 JSON Results
   ↓
🧠 LLM Summarization (OpenRouter / Mistral)
   ↓
🔊 Text-to-Speech Output
⚙️ Tech Stack
Feature	Tool/Library
Real-time search	🕵️‍♂️ SearxNG (self-hosted)
Summarization	🧠 OpenRouter + LLMs (e.g., Mistral)
Semantic search	🔍 sentence-transformers (MiniLM / MPNet)
Voice input	🎙️ speech_recognition (Google STT)
Voice output	🔊 pyttsx3 or gTTS
Containerization	🐳 Docker

🚀 Getting Started (Local Setup)
1. 📥 Clone This Repo
bash
Copy
Edit
git clone https://github.com/yourusername/itsarobo-ai-bot.git
cd itsarobo-ai-bot
2. 🐳 Install Docker Desktop
Make sure Docker Desktop is installed and running on your machine:
👉 Get Docker Desktop

🔧 Setting Up SearxNG (Private Search Engine)
✅ Option 1: Use Included Config
Already set up to use a local instance!

🧱 Setup
Clone the SearxNG Docker repo (or use the one provided in this repo)

Place your settings.yml config file inside a folder named searxng-config

Start the container:

bash
Copy
Edit
docker run -d \
  --name searxng \
  -p 8080:8080 \
  -v ${PWD}/searxng-config:/etc/searxng \
  searxng/searxng:latest
🔁 Usage
✅ Start: docker start searxng

🛑 Stop: docker stop searxng

🌐 Open in browser: http://localhost:8080

💡 How the Bot Works
User asks a question (voice or text)

Question is passed to your local SearxNG instance

Top results are selected using semantic similarity

The best match is summarized by an LLM (via OpenRouter API)

Final answer is spoken back to the user via TTS

🧠 Model Info
Using OpenRouter allows free access to:

mistralai/mistral-small

meta-llama/3-8b

...and more without GPU setup

You can change models in summarize_with_openrouter().

🗣️ Voice Mode
Voice-to-text via speech_recognition (Google STT)

Text-to-speech via pyttsx3 or gTTS (depending on environment)

All voice actions are local and private

🔐 Privacy First
All searches run through your local SearxNG — no external tracking

You control what data is accessed and stored

🧩 Future Enhancements
 Gradio/Streamlit UI for better UX

 Continuous voice mode (while True)

 Answer memory / context follow-ups

 Deployable API server (Flask/FastAPI)

