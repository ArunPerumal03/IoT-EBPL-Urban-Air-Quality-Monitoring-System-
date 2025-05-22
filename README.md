# IoT-EBPL-Urban-Air-Quality-Monitoring-System
# 🌬️ Automated Air Purifier using ESP32, DHT22, and Blynk

## 📋 Project Overview

This project is a **smart air quality monitoring system** built using an **ESP32 microcontroller**, **DHT22 sensor**, **gas sensor simulation**, and **Blynk IoT platform**. It monitors environmental parameters like temperature, humidity, and gas levels and classifies the air quality. The data is displayed locally on an LCD and remotely through the Blynk mobile app. An LED is also used to alert users if air quality is bad.

---

## 🧰 Components Used

| Component          | Description                                 |
|-------------------|---------------------------------------------|
| ESP32              | Microcontroller with built-in Wi-Fi        |
| DHT22 Sensor       | Measures temperature and humidity           |
| Potentiometer      | Simulates gas concentration (analog input) |
| I2C LCD 16x2       | Displays temperature, humidity, gas level   |
| LED                | Alerts user for bad air quality             |
| Blynk App          | Mobile app for real-time monitoring         |
| Wi-Fi Connection   | Used to connect ESP32 to Blynk cloud        |

---

## ⚙️ How It Works

1. **Sensors Read Data**  
   - DHT22 reads temperature and humidity.
   - Potentiometer simulates gas sensor values (can be replaced with MQ sensors).

2. **Data Analysis**  
   - Air level is determined by temperature and humidity.
   - Gas level is derived from analog input.
   - Air quality is categorized as `Good` or `Bad`.

3. **Outputs**  
   - **LCD Display**: Cycles through readings and status.
   - **LED Alert**: Turns on if air quality is bad.
   - **Blynk App**: Shows data remotely via virtual pins.

---

## 📱 Blynk Integration

- **Virtual Pins**  
  - V1: Temperature (°C)  
  - V2: Humidity (%)  
  - V3: Gas Value

- Connect to Blynk using:
  - `BLYNK_TEMPLATE_ID`
  - `BLYNK_TEMPLATE_NAME`
  - `BLYNK_AUTH_TOKEN`

---

## 🧠 Air Quality Logic

### Air Level (Temp & Humidity):
| Temperature (°C) | Humidity (%) | Level  |
|------------------|--------------|--------|
| 22–30            | 30–60        | Good   |
| 30–40            | 60–70        | Normal |
| Others           | Others       | Bad    |

### Gas Level:
| Analog Value | Level  |
|--------------|--------|
| 0–1364       | Good   |
| 1365–2730    | Normal |
| 2731+        | Bad    |

### Final Air Quality:
- If **Air** and **Gas** are *Good or Normal*: `Good Air Quality`
- Else: `Bad Air Quality`

---

## 🔧 Circuit Connections

| Component        | ESP32 Pin |
|------------------|-----------|
| DHT22 Data       | GPIO 2    |
| Potentiometer    | GPIO 34   |
| LED              | GPIO 4    |
| LCD (I2C)        | SDA/SCL   |

---

## 🚀 Getting Started

1. Install required libraries in Arduino IDE:
   - `DHT sensor library`
   - `Adafruit Unified Sensor`
   - `LiquidCrystal_I2C`
   - `Blynk` and `BlynkSimpleEsp32`

2. Replace your `BLYNK_AUTH_TOKEN`, Wi-Fi SSID, and password.

3. Upload code to ESP32.

4. Open Blynk app and add:
   - 3 **Value Display Widgets**: V1, V2, V3
   - Customize labels and ranges

5. Power your device and start monitoring!

---

## ✅ Features

- Real-time environment monitoring
- Local and cloud-based data visualization
- LED alert system for air pollution
- Expandable for fan or purifier control

---

## 📦 Future Improvements

- Replace potentiometer with MQ-series gas sensor
- Add automatic purifier control using a relay
- Send push notifications via Blynk
- Data logging or cloud dashboard (e.g., Google Sheets)

---

## 📜 License

This project is open-source and free to use for educational and personal projects.

---

## 🤝 Credits

Created by Arun Perumal  
Built using Arduino, ESP32, and Blynk IoT Platform.

---

