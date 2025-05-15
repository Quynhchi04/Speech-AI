# 🎤 Speech AI Dataset Repository

This repository contains annotated training data for the **Speech AI** feature of our AI Nurse Assistant. The feature is designed to respond to user-recorded voice inputs by transcribing the audio, detecting user intent, extracting key health-related entities, and generating helpful responses.

---

## 📁 Repository Structure
```
Speech-AI-Dataset/
│
├── data/
│ ├── raw/ # Raw user audio files
│ ├── annotated/ # Annotated JSON entries linked to audio
│ │ ├── speech_batch1.json
│ │ └── ...
│ ├── processed/ # Cleaned, labeled data entries
│ │ └── ...
│
├── notebooks/ # Jupyter notebooks for audio preprocessing and model training
│ └── ...
│
├── schema/
│ └── audio_schema.json # JSON schema definition for data format
│
├── scripts/ # Python scripts (e.g., transcription, labeling)
│ └── ...
│
├── annotation_guidelines.md # Instructions for labeling intents, entities, etc.
│
└── README.md # This file
```
---

## 🧾 Data Schema

Each data entry follows this schema:

| Field    | Type   | Description                                                  |
|----------|--------|--------------------------------------------------------------|
| input    | object | Contains `audio_path` and optional `transcription` string    |
| response | string | Suggested or generated response                              |
| intent   | string | Purpose of the message (e.g., `report_symptom`, `ask_info`)  |
| entities | list   | Extracted keywords/phrases (e.g., `["nausea", "chest pain"]`)|
| sentiment| string | Detected sentiment: `positive`, `neutral`, or `negative`     |
| meta     | object | Optional metadata (age, gender, timestamp)                   |

---

## 🏷️ Annotation Process

- Annotators listen to the audio and label:
  - **Transcription** (if not auto-generated)
  - **Intent**: What is the user expressing or asking for?
  - **Entities**: Key medical terms, symptoms, or experiences mentioned
  - **Sentiment**: Overall emotional tone of the message
- All annotations follow the [Annotation Guidelines](annotation/annotation_guidelines.md).

---

## 🧪 Example Entry

```json
{
  "input": {
    "audio_path": "data/raw_audio/user123_2025-05-15_10-30.wav",
    "transcription": "I’ve been feeling a sharp pain in my lower back since yesterday."
  },
  "response": "Thanks for sharing. Based on your description, it may be muscle strain or inflammation. Please monitor the pain and consult a professional if it persists.",
  "intent": "report_symptom",
  "entities": ["sharp pain", "lower back"],
  "sentiment": "negative",
  "meta": {
    "age": 42,
    "gender": "female",
    "timestamp": "2025-05-15T10:30:00Z"
  }
}