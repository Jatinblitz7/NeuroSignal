# NeuroSignal 

A modular, real-time traffic control system using computer vision to (1) estimate lane-wise vehicle density for adaptive signal timing, and (2) detect and read license plates using YOLOv8 and EasyOCR. Optimized for 30 FPS inference and low GPU usage for edge deployment.

---

## 🧠 Project Overview

This system integrates two independent yet complementary modules:

1. **Traffic Wait Time Decider**  
   Detects and tracks vehicles per lane to dynamically allocate green signal time based on real-time traffic density.

2. **License Plate Recognition System**  
   Detects license plates using a custom YOLOv8 model and extracts alphanumeric text using EasyOCR.

Both modules work independently or in sync, enabling smart, data-driven traffic automation and enforcement.

---

## 🔧 Tech Stack

- **YOLOv8** – Object detection (vehicles, license plates)  
- **ByteTrack** – Vehicle tracking across frames  
- **OpenCV** – Video processing and visual overlays  
- **EasyOCR** – License plate text extraction  
- **Python** – Core logic and system integration

---

## 📦 Modules Breakdown

### 1️⃣ Traffic Wait Time Decider

- Uses YOLOv8 + ByteTrack to count vehicles in each lane
- Divides intersection into zones for per-lane detection
- Calculates optimal signal durations based on density
- Achieved **38% reduction in delay** vs static timers

### 2️⃣ License Plate Detection & OCR

- Custom-trained YOLOv8 model detects license plates
- EasyOCR extracts plate text from preprocessed crops
- Matches plates with vehicles using tracking IDs
- **85% OCR accuracy** on 720p input at **30 FPS**

---

## 🎥 Visual Output

Each frame includes:
- 🟩 Vehicle bounding boxes with tracking IDs  
- 🟥 License plate boxes with recognized text  
- 🧠 Optional overlay of vehicle counts per lane  
- 🪪 Cropped license plate preview above each car

> _(Add images to `./media/` folder and link below)_  
> ![](./media/annotated_frame_example.png)

---

## 📊 Performance Metrics

| Feature                      | Result           |
|-----------------------------|------------------|
| Frame Rate (720p, RTX 3060) | 30 FPS           |
| Vehicle Detection Accuracy  | ~80%             |
| OCR Accuracy (EasyOCR)      | ~85%             |
| Traffic Delay Reduction     | ~38%             |
| GPU Usage                   | < 65% sustained  |

---
