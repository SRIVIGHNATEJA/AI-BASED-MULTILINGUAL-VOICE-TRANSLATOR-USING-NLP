# AI-Based Multilingual Voice Translator using NLP

🎙️ **Speak in any language → Hear it instantly in another.**

This project delivers a **real-time, offline-first voice-to-voice translation pipeline**. It captures spoken audio in a **source language**, detects and transcribes it, translates it into a **target language (chosen by voice)**, and finally speaks the translated output.

It combines **state-of-the-art models** for Indian & international languages, intelligently routing tasks for maximum accuracy & minimal latency.

---

## ✨ Key Highlights

* **Fully Voice-Driven:** No typing needed — choose the target language by simply saying its name.
* **Multimodel ASR Routing:** Smartly switches between **OpenAI Whisper** (international) and **AI4Bharat IndicConformer** (Indian languages).
* **High-Quality Many-to-Many Translation:** **Meta’s NLLB-200** provides direct translation across 200+ languages.
* **Natural Speech Output:** Uses **Indic-Parler TTS** for expressive Indian speech & **pyttsx3** for global voices.
* **Performance Profiling:** Phase-wise latency tracking & system-level logging for optimization.
* **Offline-First Design:** Once models are downloaded, works without external APIs.

---

## 🛠 Core Technologies

* **ASR (Speech Recognition):**

  * **Whisper** – Robust multilingual language detection + transcription
  * **IndicConformer** – Specialized Indian language ASR
* **Translation:** **NLLB-200** – Many-to-many multilingual translation
* **TTS (Speech Synthesis):**

  * **Indic-Parler TTS** – High-quality Indian voices
  * **pyttsx3** – Cross-platform fallback TTS
* **Frameworks:** Hugging Face Transformers, PyTorch, Sounddevice, Scipy

---

## 📜 How It Works

1. **Record Speech:** Capture & pre-process user audio.
2. **Detect Language:** Whisper auto-detects the spoken language.
3. **Transcribe:**

   * Indian languages → **IndicConformer**
   * Others → **Whisper**
4. **Target Language Selection:** Speak the desired language name (fallback: manual input).
5. **Translate:** **NLLB-200** translates from source → target language.
6. **Speech Synthesis:**

   * Indian output → **Indic-Parler TTS**
   * Other languages → **pyttsx3** fallback.
7. **Log & Profile:** Store phase-wise latencies & system stats in `asr_evaluation_log.json`.

---

## ⚡ Quick Start

```bash
# 1. Clone this repository
git clone <repo-url>
cd AI-Voice-Translator

# 2. Install system dependencies
# macOS:
brew install ffmpeg portaudio
# Ubuntu/Debian:
sudo apt-get update && sudo apt-get install ffmpeg libportaudio2

# 3. Install Python packages
pip install -r requirements.txt

# 4. Run the pipeline
python main.py
```

---

## 🎙️ Usage

1. Script plays a **beep** → Speak a sentence in any language.
2. **Second beep** → Speak the **target language name** (e.g., “English”).
3. Listen to the **translated speech output**.
4. Review **detailed logs** in `asr_evaluation_log.json`.

---

## 📊 Example Output

```
🔍 Latency Report:
 • record              : 4.39 sec
 • lang_detect         : 3.23 sec
 • asr                 : 1.83 sec
 • target_lang_select  : 7.88 sec
 • translation         : 12.39 sec
 • tts                 : 3.44 sec
 • Total Runtime       : 35.87 sec

🧾 Routing:
 • Source Language     : Telugu (te)
 • Target Language     : English (en)
 • Model Routed        : IndicConformer

🧠 Text:
 • ASR Output          : ఈ రోజు చాలా మంచి రోజు నాకు చాలా సంతోషంగా ఉంది
 • Translation Output  : Today is a very good day. I am very happy.
```

---

## 🔮 Future Enhancements

* Web-based UI for broader accessibility
* GPU acceleration & model quantization for faster processing
* Multi-speaker diarization & conversation translation
* Translation caching for frequent inputs

---

## 📜 License

Apache License 2.0
