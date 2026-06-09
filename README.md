# ORBIT — Smart Building Management System

ORBIT is a smart platform that monitors room security, energy usage, and maintenance requests to automate building operations. It uses AI for energy optimization, device diagnostics, and room analysis based on real-time IoT data — letting facility managers and occupants monitor and control everything from a web dashboard or mobile app.

By simulating and connecting IoT devices (ESP32), ORBIT cuts operational costs, prevents equipment breakdowns, and improves the daily experience of building occupants through simple, secure controls.

---

## Features

- **Real-time IoT monitoring** — room temperature, humidity, and device status via ESP32 sensors
- **AI-powered analysis** — local LLM (Ollama) for energy optimization suggestions, device diagnostics, and room analytics
- **Web dashboard** — React + Vite frontend for facility managers
- **Mobile app** — Flutter app for occupants and on-the-go monitoring
- **Maintenance request system** — submit and track maintenance tickets
- **Security monitoring** — room access and device status at a glance
- **PostgreSQL backend** — reliable data persistence with Django REST API

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend API | Django (Python) |
| Web Frontend | React + Vite (TypeScript) |
| Mobile App | Flutter (Dart) |
| AI / LLM | Flask + Ollama (`qwen2.5:4b`) |
| IoT Hardware | ESP32 + Arduino IDE |
| Database | PostgreSQL 17 |

---

## Project Structure

```
ORBIT/
├── api/          # Django backend REST API
├── web/          # React + Vite web frontend
├── mobile/       # Flutter mobile app
├── llm/          # Flask AI/LLM service (Ollama)
├── iot_scripts/  # ESP32 Arduino scripts
└── logs/         # Application logs
```

---

## Getting Started

### Prerequisites

- Python 3.x
- Node.js & npm
- Flutter SDK
- PostgreSQL 17
- Arduino IDE
- [Ollama](https://ollama.com) installed and running

---

### 1. Backend API (Django)

```bash
cd api
python -m venv venv
.\venv\Scripts\activate       # Windows
source venv/bin/activate      # Linux/macOS

pip install -r requirements.txt

# Set your local IP in api/dbmsAPI/settings.py ALLOWED_HOSTS
ipconfig                      # copy your IPv4 address

python manage.py migrate
python manage.py createsuperuser
python manage.py runserver 0.0.0.0:8000
```

---

### 2. Web Frontend (React + Vite)

```bash
cd web
npm install
npm run dev
```

---

### 3. Mobile App (Flutter)

```bash
cd mobile
flutter pub get

# Set your local IP in mobile/lib/Config/api.dart
flutter run
# or build for Android:
flutter build apk
```

---

### 4. AI LLM Service (Flask + Ollama)

```bash
# Start Ollama with the required model
ollama run qwen2.5:4b

# In a separate terminal
cd llm/static_remote_LLM
python -m venv venv
.\venv\Scripts\activate
pip install -r requirements.txt
python apillm.py
```

> First run may take a moment to initialize. Wait for the **"Starting enhanced server"** message.

---

### 5. IoT Scripts (ESP32)

1. Open `.ino` files in Arduino IDE
2. Install required libraries: `DHT sensor library`, `Adafruit Unified Sensor`
3. Select your ESP32 board and port
4. Flash to device

---

### 6. Database (PostgreSQL)

**Backup:**
```powershell
$env:PGPASSWORD='your_password'; & "C:\Program Files\PostgreSQL\17\bin\pg_dump.exe" -U postgres -d sbmsdb -f backup.sql
```

**Restore:**
```powershell
& "C:\Program Files\PostgreSQL\17\bin\createdb.exe" -U postgres sbmsdb
$env:PGPASSWORD='your_password'; & "C:\Program Files\PostgreSQL\17\bin\psql.exe" -U postgres -d sbmsdb -f backup.sql
```

---

## Contributors

| Name | Role |
|------|------|
| **Justin Escano** ([@JustinEscano](https://github.com/JustinEscano)) | Project Manager, Web Developer |
| **Ace Philip Denulan** ([@naxareth](https://github.com/naxareth)) | Lead Developer, IoT Implementation & Mobile App |
| **Matthew Cymon Estrada** | LLM Engineer, Backend Developer |
| **Gemerald De Guzman** | UI/UX Designer |
| **Peter Pagasartonga** | Web & Mobile Frontend Developer |
| **Shierwin Carl Sandino** | Web Frontend Developer |
| **David Paul Manaloto** | LLM Engineer |
| **Brian Villegas** | Backend Developer |
| **Xander Posadas** | Web & Mobile Frontend Developer |

---

## License

For academic use. PHINMA University of Pangasinan — Advanced Programming Project.
