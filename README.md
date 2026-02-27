# Face Detection

A collection of Python scripts demonstrating fundamental computer vision techniques using OpenCV, progressing from basic image manipulation to real-time face and eye detection with Haar cascade classifiers.

## Key Features

- Image loading, resizing, rotation, and saving to disk
- Live pixel-level region copying (ROI manipulation)
- Real-time webcam frame tiling and mirroring
- Webcam-based drawing of geometric shapes and text overlays
- HSV color-space masking for object isolation by color in live video
- Corner feature detection (Shi-Tomasi) on static images
- Multi-method template matching to locate a sub-image within a larger scene
- Real-time face and eye detection using pre-trained Haar cascade classifiers

## Tech Stack / Dependencies

| Library        | Purpose                                         |
|----------------|-------------------------------------------------|
| Python 3.x     | Runtime                                         |
| OpenCV (`cv2`) | All image processing and computer vision tasks  |
| NumPy          | Array operations on image data                  |

No third-party model training is required. All detection uses pre-trained XML classifiers bundled in the `model/` directory.

## Prerequisites

- Python 3.7 or higher
- A webcam (required by `face3.py`, `face4.py`, `face5.py`, and `face8.py`)

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/Aditbise/Face-Detection.git
   cd "Face-Detection/face detection"
   ```

2. Install dependencies:

   ```bash
   pip install opencv-python numpy
   ```

## Project Structure

```
Face-Detection/
└── face detection/
    ├── assets/
    │   ├── face.jpg              # Sample portrait image used by face.py and face2.py
    │   ├── images.png            # Small image used for corner detection (face6.py)
    │   ├── shoe.PNG              # Template image used for template matching (face7.py)
    │   └── soccer_practice.jpg   # Source image for template matching (face7.py)
    ├── model/
    │   ├── haarcascade_eye.xml                   # Pre-trained Haar cascade for eye detection
    │   └── haarcascade_frontalface_default.xml   # Pre-trained Haar cascade for frontal face detection
    ├── face.py    # Image load, resize, rotate, and save
    ├── face2.py   # Pixel region copy (ROI manipulation)
    ├── face3.py   # Live webcam: 2x2 tiled frame display
    ├── face4.py   # Live webcam: shape and text overlay
    ├── face5.py   # Live webcam: blue color isolation via HSV mask
    ├── face6.py   # Static image: Shi-Tomasi corner detection
    ├── face7.py   # Static image: multi-method template matching
    └── face8.py   # Live webcam: real-time face and eye detection
```

## How to Run

All scripts must be run from within the `face detection/` directory so that relative paths to `assets/` and `model/` resolve correctly.

```bash
cd "Face-Detection/face detection"
```

### Static image scripts

| Script     | Description                                                                                    | Output                                                              |
|------------|------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| `face.py`  | Loads `assets/face.jpg`, rotates it 90 degrees clockwise, and saves the result                | Window displays the rotated image; `new_img.jpg` is written to disk |
| `face2.py` | Copies a pixel region from one location to another within the image                           | Window displays the modified image                                  |
| `face6.py` | Detects Shi-Tomasi corners and draws connecting lines between them                            | Window displays detected corners on `assets/images.png`             |
| `face7.py` | Runs six template-matching methods on `soccer_practice.jpg` to locate `shoe.PNG`             | Six successive windows; press any key to advance to the next method |

```bash
python face.py
python face2.py
python face6.py
python face7.py
```

Press any key while a window is focused to close it and proceed.

### Live webcam scripts

The following scripts open the default camera (device index `0`). Press **q** to quit.

| Script     | Description                                                                              |
|------------|------------------------------------------------------------------------------------------|
| `face3.py` | Displays a 2x2 tiled and mirrored view of the webcam feed                               |
| `face4.py` | Overlays diagonal lines, a rectangle, a filled circle, and text on the webcam feed      |
| `face5.py` | Isolates blue-colored objects from the webcam feed using HSV color masking               |
| `face8.py` | Detects faces (blue bounding box) and eyes (green bounding box) in real time            |

```bash
python face3.py
python face4.py
python face5.py
python face8.py
```

## Example Usage

```bash
# Navigate to the scripts directory
cd "Face-Detection/face detection"

# Rotate a sample image and save the result
python face.py
# Expected: a window opens showing the rotated image; new_img.jpg is created in the current directory

# Locate a shoe in a soccer photo using template matching
python face7.py
# Expected: six windows open sequentially, each showing a rectangle around the detected shoe location;
#           press any key to advance between methods

# Run real-time face and eye detection via webcam
python face8.py
# Expected: a window opens showing the webcam feed with blue rectangles around detected faces
#           and green rectangles around detected eyes; press q to quit
```

## Model and Data Files

### Haar Cascade Classifiers (`model/`)

The XML files in `model/` are pre-trained Haar cascade classifiers distributed with OpenCV. They are already included in this repository and do not need to be downloaded separately.

If you need to obtain them independently, the originals are in the OpenCV GitHub repository:

- `haarcascade_frontalface_default.xml`: https://github.com/opencv/opencv/blob/master/data/haarcascades/haarcascade_frontalface_default.xml
- `haarcascade_eye.xml`: https://github.com/opencv/opencv/blob/master/data/haarcascades/haarcascade_eye.xml

Place any downloaded files in the `face detection/model/` directory before running `face8.py`.

### Sample Images (`assets/`)

All sample images are bundled in the `assets/` directory and require no additional downloads.

## Limitations and Future Improvements

**Limitations**

- Haar cascade classifiers are sensitive to lighting conditions, face angle, and occlusion. Detection accuracy drops for non-frontal or partially occluded faces.
- Webcam scripts default to device index `0`; systems with multiple cameras may need to change `cv2.VideoCapture(0)` to the correct index.
- The color-mask script (`face5.py`) is hardcoded to isolate blue objects and requires manual HSV threshold adjustment for other colors.
- Scripts do not accept command-line arguments; input paths and camera index are hardcoded.

**Possible Future Improvements**

- Replace Haar cascades with a DNN-based detector (e.g., OpenCV's `dnn` module with a pre-trained SSD or YOLO model) for improved accuracy and pose robustness.
- Add command-line argument parsing to all scripts for configurable input paths and camera index.
- Consolidate individual scripts into a single entry-point with mode selection flags.
- Add a `requirements.txt` for reproducible environment setup.

## License

No license is specified in this repository.

## Resume Highlights

- Built a series of self-contained computer vision scripts in Python using OpenCV, covering image I/O, geometric transformations, ROI manipulation, HSV color-space segmentation, corner detection, template matching, and real-time Haar cascade detection.
- Implemented real-time simultaneous face and eye detection from a live webcam feed using pre-trained XML classifiers, drawing separate bounding boxes for each detected region at interactive frame rates.
- Applied multi-method template matching across all six OpenCV similarity metrics to locate a sub-image within a larger scene and compared the output of each method.
- Demonstrated live color-based object segmentation by converting webcam frames to HSV color space and applying a binary mask to isolate a specific hue.
- All scripts are self-contained with no model training required; Haar cascade classifiers are bundled directly in the repository.
