# 👁️ VisionAI — Giving Sight Through Sound

An AI-powered real-time assistive navigation system for the visually impaired. VisionAI uses deep learning and computer vision to detect obstacles, estimate distances, and deliver adaptive voice-based guidance — enabling safe and independent navigation.

> 📄 Research paper published by Jai Agrawal, Nandini Patil, Bhoomika Babu, Rachit Sinha  
> Department of Computer Science and Engineering (AI), Manipal Institute of Technology, Bengaluru

---

## 🚀 Features

- **Real-time obstacle detection** — YOLOv8 nano model detects people, cars, bicycles, traffic lights, and more
- **Distance estimation** — bounding box geometry calculates how far obstacles are
- **AI navigation engine** — rule-based decision layer generates directional cues like *"Obstacle ahead. Turn slightly right."*
- **Voice feedback** — adaptive TTS output with temporal filters to avoid command overload
- **Cross-platform** — runs on macOS and Windows; portable to Raspberry Pi 4B
- **92.8% detection accuracy** at 12.5 FPS on CPU

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Language | Python 3.12 |
| Object Detection | YOLOv8 (Ultralytics) |
| Image Processing | OpenCV |
| Text-to-Speech | pyttsx3 / OS native TTS |
| Edge Deployment | Raspberry Pi 4B (optional) |

---

## 📊 Performance

| Metric | Result |
|--------|--------|
| Detection Accuracy | 92.8% |
| Average FPS | 12.5 (CPU, Mac M3 16GB) |
| Decision Latency | 0.4 seconds |
| Operational Range | 0.5 – 5 meters |

---

## ⚙️ System Pipeline

```
Camera Input → YOLOv8 Detection → Distance Estimation → AI Decision Engine → Voice Feedback
```

1. Capture frame from live camera
2. Run YOLOv8 inference (confidence: 0.25, IoU: 0.45, max 20 detections/frame)
3. Estimate distance using bounding box geometry
4. Apply rule-based AI logic to determine safe direction
5. Output adaptive audio guidance via TTS

---

## 🔧 Setup & Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/visionai.git
cd visionai

# Create virtual environment
python -m venv venv
venv\Scripts\activate      # Windows
source venv/bin/activate   # macOS/Linux

# Install dependencies
pip install -r requirements.txt

# Run the system
python main.py
```

### requirements.txt includes:
```
ultralytics
opencv-python
pyttsx3
```

---

## 📁 Project Structure

```
visionai/
│
├── main.py                  # Entry point
├── requirements.txt
├── README.md
│
├── models/
│   └── yolov8n.pt           # YOLOv8 nano model
│
├── core/
│   ├── detector.py          # YOLOv8 object detection
│   ├── distance.py          # Distance estimation logic
│   ├── decision_engine.py   # AI navigation decision layer
│   └── audio_feedback.py    # TTS voice output
│
└── utils/
    └── synthetic_data.py    # Offline testing / data generation
```

---

## 📝 How Distance Estimation Works

Distance is calculated using bounding box geometry:

```
D = (f × H_real) / h_box
```

Where:
- `f` = focal length of camera
- `H_real` = real-world height of the object
- `h_box` = height of the detected bounding box in pixels

---

## ⚠️ Limitations

- Performance may degrade in low-light conditions
- Partial occlusion can affect detection accuracy
- Currently optimized for indoor and close-range environments

---

## 🔮 Future Work

- Integrate LiDAR or stereo depth for enhanced spatial awareness
- Add GPS-based outdoor navigation intelligence
- Deploy on wearable smart-glass form factor
- Upgrade to larger YOLO models for higher accuracy

---

## 👨‍💻 Authors

**Jai Agrawal, Nandini Patil, Bhoomika Babu, Rachit Sinha**  
B.Tech CSE (AI), Manipal Institute of Technology, Bengaluru
