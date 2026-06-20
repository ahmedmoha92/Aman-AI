# AMAN-AI MVP

Discrete, intelligent protection for people in risky situations.

## Project Structure

- `training/`: Dockerized Jupyter training environment.
- `backend/`: Node.js server and PostgreSQL database managed with Docker Compose.
- `android/`: Kotlin / Jetpack Compose mobile app.

## Quick Start

### 1. Training
```bash
cd training
docker build -t aman-jupyter .
docker run -p 8888:8888 -v $(pwd):/home/jovyan/work aman-jupyter
```

### 2. Backend
```bash
cd backend
docker-compose up --build
```

### 3. Android App
- Copy the `.tflite` models into `android/app/src/main/assets/`.
- Open the project in Android Studio and build it from there.

## Architecture

- **AI**: TensorFlow Lite models (CNN for audio, Bi-LSTM for motion).
- **Backend**: Node.js, Express, PostgreSQL, Firebase Cloud Messaging.
- **Mobile**: Kotlin, Jetpack Compose, Retrofit, TFLite.

## Integrated Setup Guide

### Firebase Configuration
Both the app and the backend use Firebase.

- For the app, download `google-services.json` from Firebase Console and place it in `android/app/`.
- For the backend, generate a Firebase service account key and place it in `backend/fcm_key.json`.

### Backend and Training Setup
1. Go to the `backend/` folder.
2. Make sure `.env` contains your database credentials.
3. Start the stack with:
```bash
docker-compose up --build
```

This starts the API, the database, and the training environment.

### Android App Setup
1. Open the project in Android Studio.
2. If you are testing on a physical device, update the IP address in `AlertRepository.kt` from `10.0.2.2` to your machine's local IP.
3. Sync Gradle and run the app.

## Testing the MVP
1. Start the backend containers.
2. Open the app on a device or emulator.
3. Trigger the Safety Status flow to simulate a high-risk event.
4. Verify the alert reaches the backend and is stored in PostgreSQL.

---
*End-of-module project - FST Marrakech - April 2026*
