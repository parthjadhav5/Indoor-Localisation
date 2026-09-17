# 📍 Indoor Localization Using BLE and KNN

An **indoor localization system** that uses **Bluetooth Low Energy (BLE)** beacons and **RSSI (Received Signal Strength Indicator)** fingerprinting to determine the user's indoor location using a **K-Nearest Neighbors (KNN)** machine learning model.

## 🚀 Project Overview

GPS-based positioning is often unreliable indoors due to signal attenuation and obstruction. This project provides an alternative indoor positioning approach by using BLE beacon signal strengths.

Multiple ESP32 devices are configured as BLE beacons and an ESP32 scanner collects the RSSI values from these beacons. The collected RSSI fingerprint is processed and passed to a machine learning model to predict the user's location.

The system was tested across different indoor locations such as **Room 101, Room 102, and Corridor**.

## ✨ Features

* 📡 BLE-based indoor positioning
* 📶 RSSI fingerprinting
* 🤖 KNN-based location prediction
* 🔌 ESP32-based BLE beacon and scanner system
* 🐍 Python-based machine learning pipeline
* 📊 Model evaluation using accuracy and confusion matrix
* 🔄 Real-time RSSI data acquisition
* 🌐 Web-based interface for demonstrating localization results

## 🏗️ System Architecture

```text
             BLE Beacon A
                  │
             BLE Beacon B
                  │
             BLE Beacon C
                  │
                  ▼
          ┌─────────────────┐
          │   ESP32 Scanner │
          └────────┬────────┘
                   │
              RSSI Values
                   │
                   ▼
          ┌─────────────────┐
          │ Data Processing │
          │ & Preprocessing │
          └────────┬────────┘
                   │
                   ▼
          ┌─────────────────┐
          │   KNN Model     │
          └────────┬────────┘
                   │
                   ▼
          ┌─────────────────┐
          │ Location        │
          │ Prediction      │
          └─────────────────┘
```

## 🛠️ Technologies Used

### Hardware

* ESP32 BLE Beacons
* ESP32 Scanner

### Software

* Python
* Arduino IDE
* Jupyter Notebook / Python environment

### Libraries & Frameworks

* Scikit-learn
* NumPy
* Pandas
* Matplotlib
* Seaborn

### Machine Learning

* K-Nearest Neighbors (KNN)
* Random Forest for model comparison

## 📡 How It Works

### 1. BLE Beacon Deployment

Multiple ESP32 boards are configured as BLE beacons. Each beacon broadcasts a unique BLE identifier.

Example:

```text
Beacon A
Beacon B
Beacon C
```

The beacons are placed at known positions inside the building.

### 2. RSSI Collection

An ESP32 scanner continuously scans for nearby BLE advertisements and records the RSSI value received from each beacon.

A sample fingerprint may look like:

```text
Beacon A    Beacon B    Beacon C    Location
  -48         -67         -72        Room 101
  -61         -45         -70        Room 102
  -58         -59         -48        Corridor
```

RSSI values vary depending on the distance between the scanner and each beacon.

### 3. Data Preprocessing

The collected RSSI data is processed before being provided to the machine learning model.

Processing includes:

* Removing invalid readings
* Handling missing values
* Organizing RSSI values into feature vectors
* Preparing labelled training data
* RSSI smoothing where required

### 4. KNN Classification

The RSSI values from the scanner form the feature vector used by the KNN classifier.

For example:

```text
RSSI = [-52, -61, -74]
```

The KNN model compares this fingerprint with previously collected fingerprints and determines the most similar location.

### 5. Location Prediction

The trained model predicts the current indoor location:

```text
RSSI Fingerprint
       ↓
      KNN
       ↓
Predicted Location
       ↓
Room 101 / Room 102 / Corridor
```

## 📊 Results

The KNN-based localization system achieved an accuracy of approximately:

### **93.42%**

Model performance was evaluated using:

* Accuracy
* Confusion Matrix
* Prediction results

A **Random Forest** model was also evaluated for comparison with the KNN classifier.

> The reported accuracy depends on the dataset, beacon placement, RSSI fluctuations, and test conditions.

## 📁 Project Structure

```text
Indoor-Localization-BLE-KNN/
│
├── Arduino/
│   ├── Beacon_A/
│   ├── Beacon_B/
│   └── Beacon_C/
│
├── Scanner/
│   └── ESP32_Scanner/
│
├── Dataset/
│   └── RSSI_Dataset.csv
│
├── ML/
│   ├── preprocessing.py
│   ├── knn_model.py
│   └── model_comparison.py
│
├── Results/
│   ├── confusion_matrix.png
│   └── results.txt
│
├── Website/
│   └── ...
│
└── README.md
```

## ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/Indoor-Localization-BLE-KNN.git
cd Indoor-Localization-BLE-KNN
```

Install the required Python libraries:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn
```

## ▶️ Running the Machine Learning Model

Run the KNN model:

```bash
python ML/knn_model.py
```

For model comparison:

```bash
python ML/model_comparison.py
```

The program processes the RSSI fingerprints and predicts the corresponding indoor location.

## 🌐 Hosted Project

The interactive web interface for this project is hosted online.

### 🔗 Live Demo

https://indoorloc.onrender.com/

```text
https://indoorloc.onrender.com/
```


## 🎯 Applications

The system can be adapted for:

* 🏢 Indoor navigation
* 🏫 Campus/building navigation
* 🏥 Hospital localization
* 🏭 Industrial environments
* 🛒 Shopping malls
* 📦 Asset tracking
* 👥 Personnel tracking

## 🔮 Future Improvements

Possible improvements include:

* Increasing the number of BLE beacons
* Collecting larger real-world RSSI datasets
* Implementing advanced RSSI filtering
* Comparing KNN with other localization algorithms
* Using deep learning for localization
* Improving real-time prediction
* Adding a floor-plan-based visualization
* Supporting multi-floor indoor localization
* Deploying the complete system as a mobile application

## 👨‍💻 Project Highlights

* Designed an ESP32-based BLE localization system
* Implemented RSSI fingerprinting for indoor positioning
* Developed a KNN machine learning model for location classification
* Compared multiple machine learning approaches
* Achieved approximately **93.42% classification accuracy**
* Integrated hardware-based data acquisition with a Python ML pipeline

## 📜 License

This project is intended for educational and research purposes.
