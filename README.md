# 🌊 Flood Monitor

A real-time **flood and road-water monitoring system** that connects an Arduino-based water sensor to a browser dashboard through **USB Serial communication**.

The system monitors sensor readings, identifies road conditions, and displays them through a visual traffic-signal interface with **SAFE, WATER, and ALERT** states.

> **Real-time sensing. Visual monitoring. Immediate alerts.**

---

## ✨ Features

* 🌱 **SAFE State** — Road is clear
* 💧 **WATER State** — Water detected on the road
* 🚨 **ALERT State** — Flood condition detected and road blocked
* 🔌 Direct **Arduino USB Serial** connection
* 📊 Real-time sensor reading graph
* 📜 Event log for state changes
* 🔔 Browser notifications for flood alerts
* 🔊 Audio alert when an ALERT state occurs
* 🚧 Visual road barricade during flood alerts
* 🚗 Animated traffic/road visualization
* 🎨 Light and dark theme support
* 📱 Responsive layout for smaller screens
* 🧪 Built-in **Demo Mode** for testing without hardware
* ♿ Reduced-motion support for accessibility

---

## 🖥️ Dashboard

The dashboard provides a live readout of the connected sensor and visualizes the current road condition.

It includes:

* Current sensor value
* Circular water-level indicator
* Traffic signal
* Road visualization
* Recent sensor readings
* Event history
* Connection status
* Flood alert banner

The interface starts with instructions for connecting an Arduino and provides both **Connect Device** and **Run Demo** options.

---

## 🚦 Monitoring States

The system uses three road conditions:

| State        | Meaning         | Visual Response                                   |
| ------------ | --------------- | ------------------------------------------------- |
| 🟢 **SAFE**  | Road is clear   | Green signal, traffic continues                   |
| 🔵 **WATER** | Water detected  | Blue signal, flood water appears                  |
| 🔴 **ALERT** | Flood condition | Red signal, traffic stops, road barricade appears |

The dashboard explicitly maps these states to green, blue, and red traffic indicators and changes the road animation accordingly.

---

## 📏 Sensor Thresholds

The application supports a 10-bit sensor range from **0–1023**.

Default numeric thresholds:

```text
0 – 399     → ALERT
400 – 649   → WATER
650 – 1023  → SAFE
```

## The application defines `400` as the alert threshold and `650` as the safe threshold. If the Arduino sends an explicit state, that state takes priority; otherwise, the dashboard derives the state from the sensor value.

## 🔌 Arduino Communication

The dashboard communicates directly with the Arduino using the browser's **Web Serial API**.

The expected preferred Arduino output format is:

```text
DATA,742,SAFE
DATA,610,WATER
DATA,380,ALERT
```

The dashboard also supports numeric-only sensor output:

```text
742
610
380
```

For numeric-only input, the application automatically determines the corresponding state using the configured thresholds.

---

## ⚙️ How It Works

```text
Water Sensor
     │
     ▼
  Arduino
     │
     │ USB Serial
     ▼
 Browser Web Serial API
     │
     ▼
 Flood Monitor Dashboard
     │
     ├── Sensor Reading
     ├── State Detection
     ├── Live Chart
     ├── Event Log
     ├── Traffic Signal
     ├── Road Visualization
     └── Flood Alerts
```

The browser opens the serial connection at **9600 baud** and continuously reads incoming data from the Arduino.

---

## 🚨 Flood Alert System

When the system enters the `ALERT` state:

* The traffic light switches to **red**
* The road animation stops
* A **ROAD CLOSED** barricade appears
* A flood alert banner is displayed
* An audio alert can be played
* A browser notification can be triggered
* The event is recorded in the event log

The application also preserves the last valid sensor reading when invalid or missing serial data is received.

---

## 🧪 Demo Mode

The project includes a built-in demo mode, allowing the dashboard to be tested without connecting an Arduino.

Demo mode cycles through:

```text
SAFE → WATER → ALERT → SAFE → ...
```

It generates simulated sensor values with random variation so the chart, traffic signal, road animation, alerts, and event log can all be tested.

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd flood-monitor
```

### 2. Open the Dashboard

Open the HTML file in a browser that supports the Web Serial API.

Recommended:

* Google Chrome
* Microsoft Edge
* Desktop computer

### 3. Connect the Arduino

1. Upload your Arduino sensor program.
2. Connect the Arduino through USB.
3. Close the Arduino IDE Serial Monitor.
4. Open the Flood Monitor dashboard.
5. Click **Connect Device**.
6. Select the Arduino's serial port.

Only one application can use the serial port at a time.

---

## 🧪 Testing Without Hardware

Click:

```text
Run Demo
```

The dashboard will generate simulated sensor readings automatically.

This is useful for testing the UI and flood-state behavior before connecting the physical sensor.

---

## 📊 Live Data Visualization

The dashboard maintains a rolling history of up to **50 sensor readings** and renders them on a live canvas chart.

The graph also includes the safe threshold as a visual reference.

---

## 🔔 Notifications

The system supports:

* Browser notifications
* Audio alerts

Notifications are generated when a flood alert occurs, provided the user has enabled the alert option and granted browser notification permission.

---

## 🛠️ Technologies Used

### Frontend

* HTML5
* CSS3
* JavaScript
* Canvas API
* Web Serial API
* Web Notifications API
* Web Audio API
* SVG

### Hardware

* Arduino
* Water/Flood Sensor
* USB connection

### Design

* IBM Plex Sans
* IBM Plex Mono
* Responsive CSS
* Light/Dark theme support

---

## 📁 Project Structure

```text
flood-monitor/
│
├── flood-monitor.html
└── README.md
```

The current implementation is contained in a single HTML file with the interface, styling, visualization logic, serial communication, state detection, demo mode, and alert handling.

---

## 🔐 Privacy

Sensor readings are processed directly in the browser.

The dashboard states that live Arduino values are read directly from the serial connection and are not sent elsewhere.

---

## 🔮 Future Improvements

Potential extensions include:

* ☁️ Cloud-based sensor monitoring
* 📍 GPS-based flood location tracking
* 📱 Mobile application
* 🗺️ Interactive flood-risk map
* 📈 Historical sensor analytics
* 🗄️ Database storage
* 📡 Wireless communication using Wi-Fi/LoRa
* 🤖 ML-based flood prediction
* 🌧️ Weather API integration
* 🚨 SMS emergency notifications
* 🏙️ Multi-location monitoring

---

## 🎯 Use Cases

This system can be adapted for:

* Urban flood monitoring
* Road-water detection
* Smart-city infrastructure
* Low-lying road monitoring
* Drainage overflow detection
* Community flood warning systems
* IoT-based environmental monitoring

---

## 👩‍💻 Project

**Flood Monitor**

A hardware-connected web dashboard for monitoring road water levels and providing visual and audible flood alerts in real time.

**Built with:** Arduino + Water Sensor + Web Serial + HTML/CSS/JavaScript

---

## 📄 License

Add your preferred open-source license here, such as **MIT License**.

---

⭐ If you find this project useful, consider giving the repository a star.
