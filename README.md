# RTOS Real Time Fire Alarm System

<p align="center">
<a href="https://twitter.com/12dtan" target="_blank"><img src="https://img.shields.io/twitter/follow/12dtan.svg?style=social&label=Follow"></a>
<a href="https://fb.com/duytan.hh" target="_blank"><img src="https://img.shields.io/badge/Facebook%20-%20%230866FF"></a>
<a href="https://t.me/duytan2003" target="_blank"><img src="https://img.shields.io/badge/Telegram%20-%20%2333CCFF"></a>
<a href="https://www.linkedin.com/in/l%C3%AA-tr%E1%BA%A7n-duy-t%C3%A2n-81112a23a/" target="_blank"><img src="https://img.shields.io/badge/Linkedin%20-%20%2300CCFF"></a>
<a href="https://instagram/duytan.hh" target="_blank"><img src="https://img.shields.io/badge/Instagram%20-%20%23FF9900"></a>
</p>

## 📌 Introduction

This project builds a **real-time fire alarm system (RTOS)** using temperature and gas sensors to detect potential fire risks and provide early warnings. The system utilizes **FreeRTOS** to manage multitasking, ensuring fast and stable response times.

<p align="center">
  <img src="/output/012.png" alt="Output Image">
  CLIENT SIMULATION: RECEIVE DATA FROM SENSORS AND SEND TO SERVER
  <img src="/output/022.png" alt="Output Image">
  SERVER SIMULATION: RECEIVE DATA FROM CLIENT AND ISSUE ALERTS
  <img src="/output/032.png" alt="Output Image">
</p>

---

## ⚙️ Technologies and Components

- **Microcontroller**: ESP32 with FreeRTOS support
- **Sensors**:
  - `DHT11` – measures temperature and humidity
  - `MQ-2` – detects gas (LPG, CO, smoke)
- **RTOS**: FreeRTOS
- **Communication**: TCP/IP (between ESP32 and Java Server)
- **Simulation Language**: Java (Server/Client)
- **Synchronization Techniques**: Thread, Semaphore, Socket Programming

---

## 🏗️ System Architecture

```
   [ESP32 Client] -----------------------> [Java TCP Server]
   (DHT11, MQ-2 Sensor)                       (Real-time Monitor)
          |                                        |
      FreeRTOS                              Alarm thresholds
      Multitask                             Visual warning UI
```

- Each sensor operates on a separate thread and sends data periodically to the server.
- The server receives the data and displays it in real-time.
- If the values exceed a threshold, a warning system is triggered (via UI or indicator).

---

## 🔄 Workflow

### Client (ESP32):
- Initializes FreeRTOS tasks:  
  - `readTempTask` – reads data from DHT11  
  - `readGasTask` – reads data from MQ-2  
- Sends data via TCP socket to the server.

### Server (Java):
- Listens for connections on port `12345`.
- Each sensor connection is handled in a separate thread.
- Displays real-time values and triggers warnings when thresholds are exceeded.

---

## 🧪 Simulation and Emulation

- **Client**: Sensor simulation runs in Java (each sensor is a `SensorThread`) and sends periodic data.
- **Server**: Displays sensor values and triggers alerts when thresholds are exceeded.

> ✅ Example threshold values:  
> - Temperature > 50°C  
> - Gas concentration > 70 ppm

---

## 💡 Key Features

- Real-time response using RTOS.
- Each sensor runs independently, reducing data bottlenecks.
- System is easily extensible for adding more sensors or clients.
- Supports integration with GUI monitoring tools.

---

## 🖥️ Simulation Run Guide

### Server:
```bash
javac SensorServer.java
java SensorServer
```

### Client:
```bash
javac SensorClient.java
java SensorClient
```

> 📌 Make sure the IP address and port match (default `127.0.0.1:12345`)

---

## 📂 Suggested Directory Structure

```
📁 RealTimeFireAlarmRTOS/
│
├── 📁 src/
│   ├── SensorServer.java
│   ├── SensorClient.java
│   ├── SensorThread.java
│
├── 📁 esp32/
│   ├── main.ino              # FreeRTOS code for ESP32
│
├── README.md
└── presentation.pdf          # Optional: converted from PowerPoint
```

---

## 📣 Contributions and Future Development

- This is an academic project, open-source and ready to be expanded with features like:
  - Email/SMS alert integration
  - Automatic fire suppression control
  - Cloud service integration

---

## 📜 License

This project is for educational and non-commercial research purposes.
