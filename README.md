# Fall Detection System

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green)
![YOLO](https://img.shields.io/badge/Model-Tiny--YOLO-orange)
![Status](https://img.shields.io/badge/Status-Active-success)

## 📌 Overview
This project implements a real-time **Human Fall Detection System** using Computer Vision and Deep Learning techniques. It utilizes **Tiny-YOLO** for robust person detection and **AlphaPose** for skeletal pose estimation to analyze human movements and identify fall events.

The system is designed to monitor video feeds (such as CCTV or webcams) and trigger an alert when a fall is detected, making it highly applicable for elderly care and automated surveillance systems.

## ⚙️ Architecture & Methodology
The pipeline follows a multi-stage approach to ensure accuracy and speed:

1.  **Input Acquisition:** Frames are captured from a video file or live camera feed.
2.  **Person Detection (Tiny-YOLO):** The system first identifies humans in the frame using the Tiny-YOLO model (optimized for speed).
3.  **Pose Estimation (AlphaPose):** Keypoints (joints) are extracted from the detected human bounding boxes.
4.  **Fall Logic:** The system analyzes the aspect ratio of the bounding box and the velocity of keypoints.
    * *Logic:* If the angle of the torso changes rapidly from vertical to horizontal and remains there, a "Fall" is registered.

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Object Detection:** Tiny-YOLO (v3/v4)
* **Pose Estimation:** AlphaPose / OpenPose
* **Libraries:**
    * OpenCV (`cv2`)
    * PyTorch / TensorFlow
    * NumPy
    * Pandas

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone [https://github.com/Yashi5769/fall-detection.git](https://github.com/Yashi5769/fall-detection.git)
cd fall-detection
```
### 2. Install Dependencies
Ensure you have Python installed. Install the required libraries:

```bash
pip install -r requirements.txt
```

### 3. Download Weights
Download the pre-trained weights for Tiny-YOLO and place them in the `weights/` folder.
* [Download YOLO Weights](https://pjreddie.com/darknet/yolo/)

## 💻 Usage

### Run on Video File
```bash
python main.py --source path/to/video.mp4
```

### Run on Webcam
```bash
python main.py --source 0
```

### Command Line Arguments
* `--source`: Path to video file or `0` for webcam.
* `--conf`: Confidence threshold for detection (default: 0.5).
* `--output`: (Optional) Path to save the processed video.

## 📊 Performance
* **Detection Speed:** Approx. 30 FPS on GPU (varies by hardware).
* **Accuracy:** Capable of distinguishing between lying down (intentional) and falling (rapid unintentional movement).

## 🔮 Future Scope
* Integration with GSM module to send SMS alerts.
* Improving detection accuracy in low-light conditions.
* Migrating to lighter models for Edge Device (Raspberry Pi) deployment.
