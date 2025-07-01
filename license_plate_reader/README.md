# 🚗 License Plate Detection and Recognition with YOLOv8

This project detects vehicles and license plates from video using YOLOv8, associates plates with tracked cars using SORT, and performs OCR to extract license plate numbers. The output is saved in a CSV with structured data for each frame and vehicle.

---

## 📌 Overview

- Detects vehicles using pretrained **YOLOv8n**
- Detects license plates using a **custom-trained YOLOv8 model**
- Tracks vehicles across frames using the **SORT algorithm**
- Crops and binarizes license plate regions
- Uses **EasyOCR** to read text from the plates
- Exports results to `test.csv` with bounding boxes, confidence scores, and recognized text

---

## 🧠 Key Components

### 🔹 Models Used

- `yolov8n.pt`: Pretrained COCO model (for vehicles)
- `best.pt`: Custom-trained license plate detector (YOLOv8 format)
- `EasyOCR`: For reading text from plate crops

### 🔹 Vehicle Classes Detected

Only these COCO classes are considered vehicles:
[2] Car, [3] Motorcycle, [5] Bus, [7] Truck


---

## 📂 Input & Output

### 🎥 Input:
- Video file: `lic.mp4`

### 📄 Output:
- CSV file: `test.csv`, structured as:
{
frame_nmr: {
car_id: {
'car': { 'bbox': [...] },
'license_plate': {
'bbox': [...],
'text': "ABC123",
'bbox_score': 0.93,
'text_score': 0.88
}
}
}

---

## 🛠 How It Works (Pipeline)

1. Load YOLO models
2. Read video frame-by-frame
3. Detect and filter vehicle bounding boxes
4. Track vehicle IDs using SORT
5. Detect license plates
6. Match each plate with the nearest car box
7. Crop, threshold, and OCR the plate
8. Save all info in a structured `.csv`

---
