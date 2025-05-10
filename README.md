
# YTBriefAI – YouTube Video Summarizer with SEO Tags & Title Generator

## 📦 **Project Overview**
**YTBriefAI** is an AI-powered tool that extracts key insights from YouTube videos, providing a **concise summary**, **SEO-optimized hashtags**, and **catchy title suggestions**. The tool automates the content repurposing process, making it easier for creators and marketers to boost discoverability and engagement.

## 🧠 **Technology Stack**
- **Audio Extraction**: `moviepy`, `pytube`
- **Transcription**: `faster-whisper` (OpenAI Whisper-based)
- **Summarization**: `Google Gemini` (Generative AI)
- **Hashtags/Title Generation**: `Gemini`
- **Web UI (Optional)**: `Streamlit`

## 🚀 **Features**
- **Input**: Upload YouTube video (.mp4/.mp3) or provide URL (if applicable).
- **Audio Extraction**: Extracts audio from the video using `moviepy`.
- **Transcription**: Converts audio to text using **Faster-Whisper**.
- **Summarization**: Generates a concise 3-4 sentence summary using **Google Gemini**.
- **SEO Hashtags**: Generates 5–10 relevant SEO hashtags based on video content.
- **Title Generation**: Suggests 3–5 catchy, optimized titles for YouTube.
- **(Optional)**: You can extend the tool to generate video chapters/timestamps.

## ⚙️ **Setup Instructions**

### 1. **Clone the Repository**

```bash
git clone https://github.com/your-username/ytbriefai.git
cd ytbriefai
```

### 2. **Install Dependencies**

```bash
pip install -r requirements.txt
```

### 3. **Setup Google Gemini API**

- Create a project in Google Cloud Console and enable the **Generative AI API**.
- Obtain the API Key and set it in your environment variable or directly in the code.

```bash
export GOOGLE_API_KEY="your_api_key_here"
```

Alternatively, set it in your Python code:

```python
import google.generativeai as genai
genai.configure(api_key="your_api_key_here")
```

### 4. **Download Faster-Whisper**

Install **Faster-Whisper** for transcription:

```bash
pip install faster-whisper
```

### 5. **Configure the Project Directory Structure**

Ensure that your project directory follows this structure:

```
ytbriefai/
├── input/
│   ├── sample_video.mp4
├── processing/
│   ├── extract_audio.py
│   ├── transcribe.py
│   └── summarize_and_generate.py
├── prompts/
│   ├── summary_prompt.txt
│   ├── hashtags_prompt.txt
│   └── titles_prompt.txt
├── outputs/
│   ├── video_summary.md
│   ├── hashtags.txt
│   └── titles.txt
├── app/
│   └── streamlit_ui.py  # Optional, if you're using Streamlit
└── README.md
```

## 📝 **How to Use**

### 1. **Extract Audio from Video**
Run the script to extract audio from a `.mp4` file:

```bash
python processing/extract_audio.py
```

### 2. **Transcribe Audio**
Transcribe the audio to text using **Faster-Whisper**:

```bash
python processing/transcribe.py
```

### 3. **Summarize the Transcript**
Generate a concise summary of the transcript using **Gemini**:

```bash
python processing/summarize_and_generate.py
```

### 4. **Generate Hashtags and Titles**
Use the following scripts to generate SEO hashtags and catchy titles:

```python
# Modify the summarize_and_generate.py script to add hashtag and title generation using Gemini
```

### 5. **Optional UI (Streamlit)**
You can add a user-friendly interface using **Streamlit**. Here's a simple example of a Streamlit app to interact with your tool:

```python
# app/streamlit_ui.py
import streamlit as st
from processing.extract_audio import extract_audio_from_video
from processing.transcribe import transcribe_audio
from processing.summarize_and_generate import summarize_with_gemini, generate_hashtags, generate_titles

def main():
    st.title("YTBriefAI – YouTube Video Summarizer with SEO Tags & Title Generator")
    
    uploaded_file = st.file_uploader("Choose a video file", type=["mp4", "mp3"])

    if uploaded_file is not None:
        st.write("Extracting audio from the video...")
        # Handle video file extraction and processing
        audio_path = "input/audio.mp3"
        uploaded_file.save(audio_path)
        extract_audio_from_video(audio_path)

        st.write("Transcribing audio...")
        transcript = transcribe_audio(audio_path)

        st.write("Summarizing the video...")
        summary = summarize_with_gemini(transcript)
        st.write(f"Summary: {summary}")

        st.write("Generating SEO tags...")
        hashtags = generate_hashtags(transcript)
        st.write(f"Hashtags: {hashtags}")

        st.write("Generating Titles...")
        titles = generate_titles(transcript)
        st.write(f"Titles: {titles}")

if __name__ == "__main__":
    main()
```

Run the Streamlit app:

```bash
streamlit run app/streamlit_ui.py
```

## 📄 **Outputs**

- **Transcript**: `outputs/sample_transcript.txt`
- **Summary**: `outputs/video_summary.md`
- **Hashtags**: `outputs/hashtags.txt`
- **Titles**: `outputs/titles.txt`

---

## 🛠 **Optional Stretch Goals**

- **Video Chapter Markers**: Split the video into chapters using timestamps and topics.
- **Auto Upload Metadata**: Use the YouTube API to automatically upload video titles, descriptions, and hashtags.

---

## 📝 **Contributing**
If you would like to contribute to this project, feel free to fork the repository, open an issue, or create a pull request!
