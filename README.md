# Model Text-to-Speech (TTS)
This model created by :
1. Azam Azri Ahmad – Universitas Ahmad Dahlan
2. Igga Febrian Virgiani – Universitas Telkom

Notebook :
https://colab.research.google.com/drive/1kbkHQ1XiY48HJaCALgehikldd-wr1Ljs?usp=sharing

# Text-to-Speech (TTS) untuk HiTeman Audio Therapy
Sistem HiTeman Audio Therapy menggunakan pendekatan Text-to-Speech (TTS) berbasis Multilingual MMS TTS (facebook/mms-tts-ind) dari Hugging Face untuk menghasilkan audio terapi dalam bahasa Indonesia yang natural. Sistem ini ditujukan untuk mendukung terapi psikologis berbasis audio yang responsif dan ramah pengguna

# Arsitektur Sistem
HiTeman TTS terdiri dari tiga komponen utama:

1. MMSTTSEngine – Mesin TTS berbasis model facebook/mms-tts-ind dengan post-processing lanjutan.
2. AudioTherapyGenerator – Modul pembangkit terapi berdasarkan skrip dan kondisi emosional pengguna.
3. HiTemanAudioTherapy – Sistem integratif yang menangani greeting, screening, sesi terapi, dan demo sistem.

# Model Yang Digunakan
1. Model: facebook/mms-tts-ind
2. Framework: Hugging Face Transformers
3. Sampling Rate: 16,000 Hz
4. Arsitektur: VITS (Variational Inference Text-to-Speech)
5. Bahasa: Bahasa Indonesia

Model ini dilatih untuk menghasilkan suara bahasa Indonesia yang alami dan dipilih karena:
1. Mendukung inferensi lokal
2. Open-source dan ringan

# Pipeline Pemrosesan TTS
## 1. Synthesis dengan MMS TTS
a. Teks di-tokenisasi menggunakan AutoTokenizer\
b. Model VitsModel menghasilkan waveform mentah\
c. Proses dilakukan di CPU atau GPU sesuai ketersediaan perangkat

## 2. Post-Processing (v2)
a. Untuk meningkatkan kejernihan dan kualitas suara, dilakukan beberapa langkah lanjutan.\
b. Noise Reduction: Menggunakan pustaka noisereduce, menyaring noise latar dengan parameter konservatif.\
c. High-Pass Filtering: Menghapus frekuensi rendah di bawah 90 Hz yang sering mengganggu kejernihan suara.\
d. Equalization (Peaking Filter):
  - Boost di 3000 Hz dengan Q=1.8 dan gain=2.0 dB untuk meningkatkan kejernihan vokal.\
  - Opsional: tuning frekuensi mid dan low untuk menghindari suara “boxy”.\

## 3. Normalisasi
Amplitudo suara dinormalisasi agar konsisten di berbagai perangkat.

## 4. Fallback TTS (Basic)
Jika model MMS gagal dimuat (misalnya tidak ada koneksi internet), sistem otomatis menggunakan fallback basic TTS sintetis berbasis waveform sinus, harmonik, dan formant secara heuristik.

# Skrip Terapi dan Output Audio
Sistem mendukung 3 kondisi emosional utama: sedih, cemas, dan stress. Setiap kondisi memiliki skrip audio terapeutik yang disintesis menjadi .wav file melalui AudioTherapyGenerator. Contoh skrip untuk kondisi cemas:

> "Mari kita praktikkan teknik grounding lima-empat-tiga-dua-satu. Sebutkan dalam hati lima hal yang dapat Anda lihat di sekitar Anda sekarang..."

Output file disimpan dalam format .wav seperti therapy_mms_cemas_1.wav, therapy_mms_stress_3.wav, dan seterusnya.
# Fitur:
1. Suara yang Natural: Menghasilkan suara yang mirip dengan manusia untuk meningkatkan pengalaman pengguna.
2. Pengaturan Kecepatan dan Intonasi: Pengguna dapat menyesuaikan kecepatan berbicara dan intonasi suara untuk pengalaman yang lebih personal.
3. Proses Pasca-Pengolahan: Menerapkan teknik pengurangan noise dan filter suara untuk kejernihan audio yang lebih baik.
4. Pemrosesan Real-Time: Memberikan hasil suara dalam waktu nyata, cocok untuk aplikasi interaktif seperti chatbot.

# Cara Kerja
Proses secara umum meliputi:
1. Tokenisasi: Mengonversi teks menjadi format yang dapat dipahami oleh model.
2. Sintesis Suara: Menggunakan model TTS untuk menghasilkan waveform audio dari input teks.
3. Pasca-Pengolahan: Menerapkan filter dan teknik pengurangan noise untuk meningkatkan kualitas audio.

# Persyaratan
Sebelum menggunakan model ini, pastikan telah menginstal dependensi berikut:

1. torch
2. transformers
3. librosa
4. soundfile
5. numpy
6. scipy
7. noisereduce
