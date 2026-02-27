# Face Detection

A collection of Python scripts demonstrating image processing and computer vision techniques using [OpenCV](https://opencv.org/).

## Prerequisites

- Python 3.x
- [OpenCV](https://pypi.org/project/opencv-python/) (`opencv-python`)
- [NumPy](https://numpy.org/)
- [scikit-learn](https://scikit-learn.org/) (only required for `face8.py`)

## Installation

```bash
pip install opencv-python numpy scikit-learn
```

## Project Structure

```
face detection/
├── assets/
│   ├── face.jpg
│   ├── images.png
│   ├── shoe.PNG
│   └── soccer_practice.jpg
├── model/
│   ├── haarcascade_eye.xml
│   └── haarcascade_frontalface_default.xml
├── face.py
├── face2.py
├── face3.py
├── face4.py
├── face5.py
├── face6.py
├── face7.py
└── face8.py
```

## Scripts Overview

| Script | Description |
|--------|-------------|
| `face.py` | Reads an image, resizes it, rotates it 90° clockwise, saves the result, and displays it. |
| `face2.py` | Demonstrates pixel-level image manipulation by copying a region of interest to another location. |
| `face3.py` | Captures live webcam feed and creates a 4-panel mirror effect using frame rotation and tiling. |
| `face4.py` | Draws geometric shapes (lines, rectangle, circle) and text over a live webcam feed. |
| `face5.py` | Performs real-time blue color detection from a webcam feed using HSV color space masking. |
| `face6.py` | Detects image corners using `goodFeaturesToTrack` and draws connecting lines between all detected corners. |
| `face7.py` | Performs template matching on a static image using all available OpenCV matching methods. |
| `face8.py` | Detects faces and eyes in real time from a webcam using Haar Cascade classifiers. |

## Usage

Navigate to the `face detection` directory and run any script with Python:

```bash
cd "face detection"
python face.py
```

For scripts that use the webcam (`face3.py`, `face4.py`, `face5.py`, `face8.py`), press **`q`** to quit the live window.

> **Note:** `face8.py` uses absolute paths for the Haar cascade XML files. Update the paths at the top of the script to match your local environment, or use the relative paths to the `model/` directory included in this repository.

## Features Covered

- Image reading, resizing, and rotation
- Pixel-level image manipulation
- Live webcam capture and display
- Drawing shapes and text on frames
- HSV color space and color masking
- Corner detection (`goodFeaturesToTrack`)
- Template matching
- Haar Cascade face and eye detection

## Resume Highlight

**Face Detection | Python, OpenCV, NumPy**  
- Developed a face detection system using **Python** and **OpenCV**, applying classical computer vision (e.g., **Haar Cascade-based detection**) to identify and localize faces.  
- Built an end-to-end pipeline with **NumPy**-based frame processing: image/video input handling, grayscale conversion, and real-time **bounding box** rendering.  
- Tested across varying lighting conditions and camera angles using **webcam/video stream** input to validate consistent detection results.

**Tech Stack:** Python, OpenCV, NumPy  

## License

This project is open source and available for educational purposes.
