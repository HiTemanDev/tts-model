# Model Text-to-Speech (TTS)
This model created by :
1. Azam Azri Ahmad – Universitas Ahmad Dahlan
2. Igga Febrian Virgiani – Universitas Telkom

Notebook :
https://colab.research.google.com/drive/1GSgPRTUTHQswAEDZD9Axwn-5ciykX3Yi?usp=sharing

# 🗣️ HiTeman TTS (Text-to-Speech) Model

**HiTeman TTS** adalah modul berbasis Python untuk menghasilkan narasi otomatis dan mengonversinya ke audio menggunakan model **Gemini 1.5 Flash** dan **TTS Native Gemini (gemini-2.5-flash-preview-tts)** dari Google.

Proyek ini dirancang untuk menghasilkan narasi dari prompt/topik yang diberikan oleh label klasifikasi emosi (lihat [HiTeman Klasifikasi](https://github.com/HiTemanDev/clasification-model)), serta menyintesis suara dari teks tersebut menjadi file audio (MP3).

---

## 🔍 Fitur Utama

- 🎙️ **Text Generation**: Menggunakan Gemini 1.5 Flash untuk menghasilkan narasi dari prompt teks label emosi (lihat [HiTeman Klasifikasi](https://github.com/HiTemanDev/clasification-model)) .
- 🔊 **Text-to-Speech**: Menggunakan TTS Native Gemini (gemini-2.5-flash-preview-tts) untuk mengonversi narasi menjadi audio.
- 💾 **Output Otomatis**: Menyimpan hasil narasi dan audio ke Google Drive atau lokal.
- 🤖 Dapat digunakan secara terintegrasi dalam backend (lihat [HiTeman API](https://github.com/HiTemanDev/backend-api)).

---

## 🧠 Teknologi yang Digunakan

- **Google Gemini 1.5 Flash** — untuk pembuatan konten narasi.
- **TTS Native Gemini (gemini-2.5-flash-preview-tts)** — untuk sintesis suara (text-to-speech).
- **Google Colab + Drive** — untuk penyimpanan hasil.
- **Python** — sebagai bahasa utama implementasi.

---

## 🧠 Input
```json
{
  "emotion": "stress"
}
```

## 🔊 Output
- File `.wav` berupa audio terapi.
- Disimpan dengan nama format `hiteman_therapy_audio_native_<timestamp>.wav`.

## 📦 Prasyarat
```bash
pip install -r requirements.txt
```

## 📝 Catatan
- Pastikan memiliki kredensial Gemini API.

## 🧩 Integrasi

Modul ini didesain agar dapat digunakan dalam backend lain, seperti FastAPI API (`hitemanAPI`).

---

## 📄 Lisensi

MIT License © HiTeman Dev
