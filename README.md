# 🤟 Real-Time Indian Sign Language (ISL) Translator

A real-time ISL translation system using computer vision and deep learning.
Recognizes ISL hand signs through a webcam and converts them to text and speech.

---

## ✨ Features
- **Letter mode** — Sign A-Z and 0-9, auto-builds words with autocomplete
- **Word mode** — Sign full ISL words, auto-adds to sentence
- **NLP correction** — Converts signed words into grammatically correct sentences
- **Text-to-Speech** — Speaks the final sentence aloud

---

## ⚙️ Setup (Do this once)

### 1. Clone the repo
```bash
git clone https://github.com/apekshak1415/isl-1.git
cd isl-1
```

### 2. Make sure you have Python 3.11
> ⚠️ Python 3.12+ does NOT work — MediaPipe requires Python 3.11
- Download Python 3.11 from: https://www.python.org/downloads/release/python-3119/

### 3. Create a virtual environment
```bash
py -3.11 -m venv isl_env
isl_env\Scripts\activate
```

### 4. Install dependencies
```bash
pip install -r requirements.txt
```

---

## 📦 Collect Your Own Data (Required — models are trained on your hand)

> The models must be trained on YOUR hand for accurate recognition.
> This takes about 1 hour total.

### Step 1 — Collect letter data (~20 mins)
```bash
python src/collect_own_data.py
```
- Signs each letter (A-Z, 0-9) in front of your webcam
- Follow the on-screen instructions
- Press **SPACE** to record each sign

### Step 2 — Train letter model (~5 mins)
```bash
python src/train_own_letter_model.py
```

### Step 3 — Collect word data (~30 mins)
```bash
python src/collect_own_word_data.py
```
- Signs 10 core ISL words
- Press **SPACE** to record, sign the word, repeat 30 times per word
- Words: HELLO, THANK YOU, SORRY, HELP, YES, NO, FOOD, WATER, GOOD, MY NAME

### Step 4 — Train word model (~10 mins)
```bash
python src/train_own_word_model.py
```

---

## 🚀 Run the Translator
```bash
python src/realtime_translator.py
```

### Controls
| Key | Action |
|-----|--------|
| M | Toggle Letter / Word mode |
| SPACE | Confirm current word |
| 1-4 | Pick autocomplete suggestion |
| ENTER | Speak the sentence |
| BACKSPACE | Undo last letter or word |
| C | Clear everything |
| Q | Quit |

---

## 📁 Project Structure
```
isl-1/
├── src/
│   ├── collect_own_data.py        ← collect your letter data
│   ├── collect_own_word_data.py   ← collect your word data
│   ├── train_own_letter_model.py  ← train letter model
│   ├── train_own_word_model.py    ← train word model
│   ├── realtime_translator.py     ← main app
│   ├── nlp_helper.py              ← sentence correction
│   └── tts_helper.py              ← text to speech
├── models/
│   ├── label_encoder_letters.pkl  ← letter class names
│   └── label_encoder_words.pkl    ← word class names
├── requirements.txt
└── .gitignore
```

---

## 🛠️ Tech Stack
- Python 3.11
- MediaPipe 0.10.9 — hand landmark detection
- TensorFlow 2.13.0 — deep learning
- OpenCV — real-time video
- pyttsx3 — text to speech

---

## ⚠️ Common Issues

**MediaPipe not installing?**
Make sure you're using Python 3.11, not 3.12 or 3.13.

**Low accuracy in letter mode?**
Collect more data using `collect_own_data.py` and retrain.

**Word mode not recognizing signs?**
Make sure you signed each word consistently during collection.
Try collecting 10-20 more clips for that specific word and retrain.

