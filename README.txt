#  AI-Based Real-Time Surveillance System with Suspicious Activity & ID Detection

##  Overview

This project presents an intelligent real-time surveillance system that automatically detects suspicious human activities and verifies identity using ID card detection. The system combines deep learning, computer vision, and web technologies to provide a smart monitoring solution.

It is designed for applications such as:

* Online exam proctoring
* Workplace monitoring
* Secure surveillance environments

---

##  Key Features

*  Real-time suspicious activity detection
*  Deep learning-based sequence modeling (CNN + LSTM)
*  ID card detection using YOLOv5
*  Live video streaming via Flask web interface
*  Automatic email alerts for suspicious behavior
*  User authentication system (Login/Register)
*  Dashboard for monitoring and analysis
*  Anti-spoof detection (screen & video detection)

---

##  System Architecture

The system follows a multi-stage pipeline:

1. Webcam captures live video frames
2. Frames are processed in real-time using two models:

   * Activity Detection Model (MobileNet + LSTM)
   * ID Card Detection Model (YOLOv5)
3. Anti-spoof module checks for screen/video usage
4. Suspicious activity triggers email alert
5. Output is streamed to a Flask-based dashboard

---

##  Models Used

###  Activity Detection Model

* Backbone: MobileNetV2 (feature extraction)
* Sequence Model: LSTM
* Input: Sequence of 25 frames
* Output: Binary classification

  * 0 → Normal
  * 1 → Suspicious

---

###  ID Card Detection Model

* Model: YOLOv5 (custom trained)
* Task: Object detection
* Class: `id_card`

---

##  Anti-Spoof Detection

To prevent cheating or fake inputs, the system detects:

*  Screen presence (brightness + edge analysis)
*  Video playback (motion consistency analysis)

If detected:
→ ID card detection is disabled

---

## 📂 Project Structure
```
project/

├── app.py
├── mobilenet_lstm_generator.h5
├── best.pt
├── users.db

├── README.md
├── requirements.txt

├── weights/
│   └── mobilenet_v2_no_top.h5

├── extracted_frames_all/
│   └── train/
│       ├── normal/
│       └── suspicious/

├── templates/
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   ├── predict.html
│   ├── analysis.html
│   └── about.html

├── static/
```

---

##  Installation

### 1. Clone Repository

```
git clone https://github.com/your-username/surveillance-system.git
cd surveillance-system
```

---

### 2. Install Dependencies

```
pip install -r requirements.txt
```

---

### 3. Set Email Configuration

Use environment variables:

```
set EMAIL_USER=your_email@gmail.com
set EMAIL_PASS=your_app_password
```

---

##  Running the Application

```
python app.py
```

Open browser:

```
http://127.0.0.1:5000
```

---

##  Authentication System

* New users must register
* Login required to access system
* Session-based authentication

---

##  Detection Logic

### Activity Detection

* Frame buffer size: 25
* Sliding window prediction
* Threshold: 0.60

---

### ID Detection

* YOLOv5 detects ID card
* Runs only if:

  * No screen detected
  * No video playback detected

---

##  Email Alert System

Triggered when:

* Suspicious activity confidence exceeds threshold

Includes:

* Confidence score
* Alert message

---

##  Performance

* Training Accuracy: ~97.6%
* Real-time performance: Smooth with GPU support
* Efficient multi-threaded processing

---

##  Limitations

* Requires stable lighting conditions
* CPU-only systems may be slower
* Email alerts depend on network availability

---

##  Future Enhancements

* Face recognition integration
* Cloud deployment (AWS/GCP)
* Multi-camera support
* Mobile app interface

---

##  Technologies Used

* Python
* TensorFlow / Keras
* PyTorch (YOLOv5)
* OpenCV
* Flask
* SQLite

---

##  License

This project is developed for academic and research purposes only.
