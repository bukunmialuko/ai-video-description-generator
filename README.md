# 🤖 AI Video Description Generator

An end-to-end AI pipeline that transforms video URLs into **structured, student-friendly learning materials**. 

This project automates the heavy lifting of media processing—downloading, audio extraction, and transcription—before leveraging a local LLM to generate high-quality educational summaries and study guides.

## 🚀 How It Works

The pipeline follows a modular 5-step process:
1. **Ingestion:** Downloads video from any supported URL via `yt-dlp`.
2. **Audio Processing:** Extracts and normalizes audio using `ffmpeg`.
3. **Transcription:** Converts speech to text with high accuracy using `faster-whisper`.
4. **Context Management:** Smart-chunks long transcripts to fit within LLM context limits.
5. **Inference:** Generates a structured `.md` summary using a local GGUF model via `llama-cpp-python`.

## 🛠 Tech Stack

- **Media:** `yt-dlp`, `ffmpeg`
- **Speech-to-Text:** `faster-whisper`
- **LLM Engine:** `llama-cpp-python`
- **Environment:** Python, Jupyter, `python-dotenv`

## 📂 Project Structure
```text
models/
└── Qwen2.5-14B-Instruct-Q4_K_M.gguf  # Local LLM (Git ignored)

output/<job_name>/
├── work/            # Raw video and extracted audio.wav
├── chunks/          # Segmented audio files for processing
├── chunk_results/   # Individual transcriptions per chunk
└── final/           # Final transcript (txt, json, srt, vtt) & AI description
```

## ⚙️ Setup & Installation

### 1. System Dependencies (Mac)
Ensure you have `ffmpeg` installed:
```bash
brew install ffmpeg
```

### 2. Python Environment
Install the core pipeline requirements:
```bash
pip install -U yt-dlp faster-whisper llama-cpp-python python-dotenv torch
```

### 3. Environment Configuration
Create a `.env` file in the root directory:
```env
HF_TOKEN=your_huggingface_token
```

## 📖 Usage

1. Open `description_generator.ipynb`.
2. Set your configuration: `URL`, `JOB_NAME`, and `MODEL_PATH`.
3. **Run All Cells**. The pipeline is resumable.

## 🤝 Contributing

We welcome contributions! 
* **UI/UX:** Help us move to a Gradio or Streamlit interface.
* **Prompt Engineering:** Refine the "student-friendly" prompts.
* **Optimization:** Improve Apple Silicon (MPS) support.

**To contribute:** Fork, Branch, Commit, and Open a Pull Request.

## 📜 License

Distributed under the MIT License.

---
*Built for students, by developers.*