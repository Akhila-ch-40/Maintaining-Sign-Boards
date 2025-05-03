# 🚗 Traffic Sign Detection and Vehicle Control in CARLA

This project simulates autonomous vehicle behavior in the CARLA simulator using real-time traffic sign detection. A YOLOv8 object detection model identifies traffic signs (e.g., STOP, SPEED LIMIT), and the vehicle adjusts its behavior accordingly. The simulation also displays a live driver's camera view using Pygame.

---

## 📁 Project Structure

* 'Code'-Contains the Code 'main.py' adn the 'requirements.txt'
* 'Images'- Cantains the images of the respective work of the project
* 'Model' - Contains 'yolov8n.pt' model used for the project
* 'Readme'- Info of the Project

---

## 🛠 Requirements

Make sure you have the following installed in your Python environment:

```bash
pip install carla pygame numpy torch ultralytics
```

### Additional Requirements:

* **CARLA Simulator** (version ≥ 0.9.13): Download from [CARLA GitHub](https://github.com/carla-simulator/carla).
* **CUDA** (optional): For faster inference with YOLOv8 if a GPU is available.
* **Python ≥ 3.7**

---

## 📦 Pretrained Models Used

### 🧠 YOLOv8n

* **Model File**: `yolov8n.pt`
* **Source**: Provided by [Ultralytics](https://github.com/ultralytics/ultralytics)
* **Purpose**: Detects traffic signs (e.g., STOP, SPEED LIMIT) in real time from RGB camera input.

The script loads the model via:

```python
model = YOLO("yolov8n.pt")
```

---

## 🎮 Features

* Autonomous vehicle follows lanes using waypoint-based steering.
* Live camera feed processed with YOLOv8 for traffic sign detection.
* Recognizes STOP signs and applies brakes.
* Adjusts speed based on detected SPEED LIMIT signs.
* Handles traffic lights (brakes on red light).
* Spawns dynamic traffic and signs at random locations.
* Displays real-time view via Pygame.
* Stops simulation after 2 minutes.

---

## 🧪 How It Works

1. **CARLA Setup**:

   * Connects to CARLA server.
   * Spawns the ego vehicle, random traffic, and signs (STOP + SPEED LIMIT).
   * Attaches an RGB camera to the vehicle.

2. **YOLOv8 Inference**:

   * Each frame from the camera is passed to the YOLOv8 model.
   * Detects bounding boxes and class labels for signs.

3. **Vehicle Control**:

   * Adjusts speed to match SPEED LIMIT signs.
   * Brakes fully for STOP signs.
   * Obeys traffic light states.

4. **Visualization**:

   * Pygame shows the driver’s view.
   * Logs detection and action events in the terminal.

---

## ▶️ Run Instructions

1. **Start CARLA Simulator**:

   ```bash
   ./CarlaUE4.sh
   ```

2. **Run the Python Script**:

   ```bash
   python Main.py
   ```

The simulation runs for 2 minutes and stops automatically.

---
 
## 🧼 Cleanup

All actors (vehicles, sensors, signs) are properly destroyed at the end of the simulation to prevent memory leaks.

---

## 📌 Notes

* The detection is basic and uses the small `yolov8n` model. For better accuracy, replace with `yolov8s.pt`, `yolov8m.pt`, etc.
* You must ensure the CARLA world includes the sign assets referenced in the script.
* Detection relies on YOLO classes; retraining may be needed for precise sign classification.

