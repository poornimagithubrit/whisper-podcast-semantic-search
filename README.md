# 🎙️ Whisper Podcast Semantic Search

> Transcribed 235 podcast files with timestamp-level precision using OpenAI Whisper, then built a FAISS-powered semantic search engine to query the full corpus using natural language.

---

## 🧩 Problem

Podcast content is locked inside audio — unsearchable, unindexed, and impossible to query. Teams waste hours scrubbing through recordings to find specific discussions, topics, or quotes.

## ✅ Solution

An end-to-end pipeline that:
1. Transcribes audio files with **word-level timestamps** using OpenAI Whisper
2. Chunks transcripts into semantically meaningful segments
3. Embeds chunks using **OpenAI Embeddings**
4. Stores vectors in **FAISS** for fast similarity search
5. Lets users search across all 235 episodes using **natural language queries**

---

## 🏗️ Architecture

```
Audio Files (.mp3/.wav)
        │
        ▼
  OpenAI Whisper API
  (Transcription + Timestamps)
        │
        ▼
  Text Chunking & Preprocessing
        │
        ▼
  OpenAI Embeddings (text-embedding-ada-002)
        │
        ▼
  FAISS Vector Index
        │
        ▼
  Semantic Search API (FastAPI)
        │
        ▼
  Query Results with Timestamps + Episode Info
```

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Transcription | OpenAI Whisper API |
| Embeddings | OpenAI text-embedding-ada-002 |
| Vector Store | FAISS |
| Backend API | FastAPI |
| Language | Python 3.10+ |

---

## 📂 Project Structure

```
whisper-podcast-semantic-search/
├── transcribe/
│   ├── whisper_transcriber.py      # Whisper API transcription logic
│   └── timestamp_extractor.py      # Extract word-level timestamps
├── embeddings/
│   ├── chunker.py                  # Semantic text chunking
│   └── embed_and_index.py          # Create FAISS index
├── search/
│   └── semantic_search.py          # Query the FAISS index
├── api/
│   └── main.py                     # FastAPI endpoints
├── requirements.txt
├── .env.example
└── README.md
```

---

## ⚙️ Setup & Installation

```bash
git clone https://github.com/poornimagithubrit/whisper-podcast-semantic-search
cd whisper-podcast-semantic-search
pip install -r requirements.txt
cp .env.example .env
# Add your OpenAI API key to .env
```

---

## 🔑 Environment Variables

```env
OPENAI_API_KEY=your_openai_api_key_here
AUDIO_FILES_DIR=./data/audio
INDEX_PATH=./data/faiss_index
```

---

## 🚀 Usage

```bash
# Step 1: Transcribe all audio files
python transcribe/whisper_transcriber.py

# Step 2: Build the FAISS index
python embeddings/embed_and_index.py

# Step 3: Start the search API
uvicorn api.main:app --reload

# Step 4: Search!
# GET /search?q=machine+learning+best+practices
```

---

## 📊 Results

- ✅ **235 podcast episodes** transcribed with timestamp precision
- ✅ Sub-second semantic search across the full corpus
- ✅ Timestamp-linked results allow direct navigation to relevant audio segments

---

## 📦 Requirements

```
openai
faiss-cpu
fastapi
uvicorn
python-dotenv
numpy
```

---

## 📄 License

MIT License
