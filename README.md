# Automatic-number-plate-recognition-with-Yolov9-and-EasyOCR
This project is an end-to-end Automatic Number Plate Recognition (ANPR) system that uses YOLOv9 for vehicle and number plate detection and OCR (Optical Character Recognition) for extracting text from license plates. It is designed to work with videos or images and is capable of detecting and recognizing number plates with high accuracy.



🎥 Demo Output:
https://drive.google.com/drive/u/0/folders/1BFw765zc6s7N01JFRufRRUFrOBr6oKGL







🚘 Automatic Number Plate Recognition (ANPR) using YOLOv9 and OCR
This project implements an Automatic Number Plate Recognition (ANPR) pipeline using YOLOv9 for license plate detection and OCR (EasyOCR) for extracting text from the plates. It supports both image and video inputs and is built to work efficiently with real-world traffic footage.

🔧 Features
✅ YOLOv9-based number plate detection (trained on custom dataset)

✅ OCR using EasyOCR for recognizing license plate characters

✅ Video and image inference

✅ Output visualization with bounding boxes and recognized text

✅ Works on multiple vehicles simultaneously

🧪 Demo
Input	Detection + OCR
car.mp4	
multicar.mp4	Multi-vehicle number plate extraction
traffic.mp4	Plate detection in traffic scenes

📁 Project Structure

├── yolov9/                 # Cloned YOLOv9 repo
├── weights/               # YOLOv9 pre-trained weights
├── runs/                  # Output: results, models, images
├── anpr.py                # Script for detection + OCR
├── car.mp4                # Sample video
├── traffic.mp4            # Sample video
├── multicar.mp4           # Sample video
└── README.md              # This file


🚀 Installation
# Clone YOLOv9 and install dependencies
git clone https://github.com/SkalskiP/yolov9.git
cd yolov9
pip install -r requirements.txt
pip install roboflow easyocr

📦 Dataset
This project uses a custom dataset labeled for number plates, downloaded via Roboflow.
from roboflow import Roboflow
rf = Roboflow(api_key="your-api-key")
project = rf.workspace("bithal").project("anpr2-syxl7-r7mcf")
dataset = project.version(1).download("yolov9")


🏋️ Training
python train.py \
--batch 16 --epochs 25 --img 640 --device 0 --min-items 0 --close-mosaic 15 \
--data ANPR2-1/data.yaml \
--weights weights/gelan-c.pt \
--cfg models/detect/gelan-c.yaml \
--hyp hyp.scratch-high.yaml

✅ Evaluation
python val.py \
--img 640 --batch 32 --conf 0.001 --iou 0.7 --device 0 \
--data ANPR2-1/data.yaml \
--weights runs/train/exp4/weights/best.pt


📌 Requirements
Python 3.8+

PyTorch ≥ 2.0

OpenCV

Roboflow

EasyOCR

YOLOv9

tqdm

📈 Results
Precision: ~0.94

Recall: ~0.95

mAP@0.5: ~0.98

🤖 Applications
Smart traffic monitoring

Highway toll automation

Vehicle parking and access control

Law enforcement and surveillance
