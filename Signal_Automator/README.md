
# 🚦 Zone-Based Traffic Wait Time Estimation with YOLOv8

This project detects and counts vehicles in a defined polygon zone within a traffic video and dynamically estimates the ideal wait time for that lane based on vehicle density. It uses **YOLOv8** for object detection and **Supervision** for polygon-based zone counting.

---

## 📌 Overview

- Custom polygon zone is defined on an intersection lane
- Vehicles inside the zone are detected and counted per frame
- Based on the final count, a wait time is assigned:
  - **< 10 vehicles** → wait `20s`
  - **10–39 vehicles** → wait `40s`
  - **≥ 40 vehicles** → wait `60s`
- Output video is generated with visual overlays for:
  - Detected vehicles
  - Polygon zone
  - Frame-by-frame annotations

---

## 📂 Input & Output

**Input:**
- Video: `Signal.mp4` (traffic footage)

**Output:**
- Annotated video: `signal-result.mp4`
- Console printout:
Time taken to process video: 4.01 seconds
Count: 35, Wait: 40


---

## 🧠 How It Works

1. Load YOLOv8 model (`yolov8s.pt`)
2. Define a polygon zone using coordinate points
3. Run inference on each frame
4. Use Supervision to track and count vehicles inside the polygon
5. Store final count and determine optimal wait time using predefined thresholds
6. Save annotated video with all visual cues

---
