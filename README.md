# AI Video Description Generator

An end-to-end AI pipeline that generates **student-friendly learning descriptions** from a video link.

The project downloads a video, extracts audio, transcribes speech, and uses a local LLM to create a structured educational summary.

## How It Works

1. Download video from URL (YouTube supported)
2. Extract and normalize audio
3. Transcribe audio using Whisper
4. Split long transcripts into chunks
5. Generate study-style description with a local GGUF model

## Tech Stack

- yt-dlp – video download  
- ffmpeg – audio extraction & chunking  
- faster-whisper – transcription  
- llama-cpp-python – local LLM inference  
- python-dotenv – configuration  

## Project Structure

models/
- Qwen2.5-14B-Instruct-Q4_K_M.gguf   # local LLM (not committed)

output/<job_name>/
- work/            # downloaded video + audio.wav
- chunks/          # chunked audio files
- chunk_results/   # per-chunk transcripts
- final/           # final transcript + description

description_generator.ipynb
- main pipeline notebook

## Setup

### Install (Mac)

brew install ffmpeg
pip install -U yt-dlp faster-whisper llama-cpp-python python-dotenv torch

### Environment

Create .env file:

HF_TOKEN=your_token

## Usage

1. Open description_generator.ipynb  
2. Set:
   - URL = video link  
   - JOB_NAME = output folder  
   - MODEL_PATH = path to GGUF model  
3. Run all cells

### Output

output/<JOB_NAME>/final/
- transcript.txt  
- transcript.json  
- transcript.srt  
- transcript.vtt  
- student_description.md  

## Notes

- Designed for long lectures and educational videos  
- Fully local – no external API calls for summarization  
- Resumable chunk processing  

## License

MIT
