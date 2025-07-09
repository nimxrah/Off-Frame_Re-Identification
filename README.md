# Off-Frame_Re-Identification

# 🏃‍♂️ Football Player Detection & Tracking

This project performs **real-time object detection** and **multi-object tracking (MOT)** on a 15-second football match video. It assigns consistent and unique player IDs — even when players leave and re-enter the frame (to some extent) — using **YOLOv8** and **Deep SORT**.

## 📌 Features
- 🎯 Detects players using [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- 🔁 Tracks players using [Deep SORT](https://github.com/nwojke/deep_sort)
- 🎥 Outputs annotated video with bounding boxes and player IDs
- 🧠 Supports tracking even when players briefly leave and re-enter the frame
- ⚙️ Easily upgradable to **BoT-SORT** or **OC-SORT** for improved off-frame re-identification

---

## 📁 Folder Structure
├── tracked_frames/ # Saved annotated frames (temp)
├── input.mp4 # Your input football video
├── output_fixed.mp4 # Final output video with tracked players
├── tracking_script.ipynb # Main Python script
└── README.md # This file

---

## 🛠 Requirements

Run in [Google Colab](https://colab.research.google.com/) or a Python environment with:

pip install ultralytics opencv-python deep_sort_realtime imageio imageio-ffmpeg
🚀 Run the Project (Colab Recommended)
Upload input.mp4 (your football video)

Run the main script:
from google.colab import files
uploaded = files.upload()  # Upload input.mp4

# After upload, run the detection & tracking script
# (see `tracking_script.py`)
Download your output:
files.download("output_fixed.mp4")

🧠 Tracking Logic (Deep SORT)
Deep SORT assigns consistent IDs using:
Motion prediction (Kalman filter)
Appearance similarity (embedding model)

We tune the tracker with:
max_age=90 – remembers identities longer
Bounding box size filter to avoid crowd noise

⚠️ Known Limitations
If a player leaves the frame too long, identity may be reassigned.

Deep SORT alone is limited in re-identification beyond ~3 seconds.

💡 Advanced: Upgrade to Better Trackers
Tracker	Pros	GitHub Link
BoT-SORT	Best re-ID for re-entering players	BoT-SORT
OC-SORT	Better for camera motion	OC-SORT
FairMOT	End-to-end detector+tracker	FairMOT

📬 Contact
Made with ❤️ for sports analytics, tracking, and computer vision.
