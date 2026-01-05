# Face Recognition Attendance System

This project is a **Face Recognition Attendance System** implemented in Python, designed to track employee attendance in real-time using face recognition. It works in **Google Colab** and uses the webcam to capture employee faces, generate embeddings, and mark attendance automatically.

---

## Features
- **Register Employees:** Capture face photos and store unique Employee IDs with embeddings.
- **Mark Attendance:** Recognize faces via webcam and log attendance with date, time, and confidence percentage.
- **Show Attendance:** Display sorted attendance records from `attendance.csv`.
- **Delete Employee / All Data:** Remove individual employees or clear all records and face images.
- **Embeddings Display:** Shows 128-dimensional face vectors for registered and detected faces.
- **Timezone Support:** Attendance timestamps are adjusted for **Asia/Karachi (UTC+5)**.

---

## How It Works
1. **Register Employee**
   - Captures employee face using webcam.
   - Computes **128-dimensional embeddings** using a pre-trained **ResNet CNN** model.
   - Saves the face image and unique Employee ID.
   - Checks for duplicates by comparing embeddings with existing employees.

2. **Mark Attendance**
   - Captures live photo of the person.
   - Extracts embeddings from the detected face.
   - Compares embeddings with registered faces using **Euclidean distance**.
   - Marks attendance in `attendance.csv` with date, time, Employee ID, name, and confidence score.
   - Only allows **one attendance per day per employee**.

3. **Show Attendance**
   - Displays attendance records sorted by date and time.

4. **Delete Employee / All Data**
   - Removes the selected employee’s records and face images.
   - Can delete all data at once, including images and CSV file.

---

## Machine Learning Concepts
- **Model:** Pre-trained **ResNet Convolutional Neural Network** (used in `face_recognition` library).
- **Type of Learning:** Supervised learning (multi-class classification).
- **Problem Type:** Face recognition → **multi-class classification** (each registered employee is a class).
- **Embeddings:** Each face is represented as a 128-dimensional vector (feature representation).
- **Distance Metric:** Euclidean distance between embeddings to find the closest match.
- **Confidence Score:** Calculated as `(1 - distance) * 100` to show recognition certainty.
- **No training required in your code:** The ResNet model is pre-trained on large face datasets (like VGGFace2 / CASIA-WebFace).

---

## Limitations
- Accuracy depends on **lighting, camera quality, and face orientation**.
- Can struggle with **identical twins, masks, hats, or glasses**.
- Google Colab runtime is **temporary**; all data in runtime storage is lost unless saved externally.
- Only allows **one attendance entry per employee per day**.

---

## Use Cases
- **Employee Attendance System** for offices or schools.
- **Access Control** for doors or secured areas.
- **Event Management** for logging participant attendance automatically.
- **Real-time monitoring** in organizations without manual entry.

---

## Dependencies
- Python 3.x
- Libraries: `face_recognition`, `opencv-python`, `numpy`, `pandas`, `IPython.display`, `uuid`, `shutil`, `pytz`

---
