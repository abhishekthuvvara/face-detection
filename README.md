# face-detection
# Real-Time Face Detection using OpenCV

A simple Python script that uses OpenCV's Haar Cascade classifier to detect faces in real time via your webcam feed.

## Features

- Captures live video from your default webcam
- Detects faces in each frame using the Haar Cascade frontal face classifier
- Draws a bounding box around each detected face
- Labels each detection with "Face Detected"
- Press `q` to exit the application

## Requirements

- Python 3.6+
- OpenCV (`opencv-python`)

## Installation

1. Clone or download this repository.
2. Install the required dependency:

```bash
pip install opencv-python
```

## Usage

Run the script from your terminal:

```bash
python face_detection.py
```

- A window titled **"Face Detection using python"** will open, showing your webcam feed with detected faces highlighted.
- Press **`q`** at any time to close the application.

## How It Works

1. **Load the classifier** — Uses OpenCV's pre-trained `haarcascade_frontalface_default.xml` model, bundled with the `opencv-python` package.
2. **Capture video** — Opens the default camera (index `0`) using `cv2.VideoCapture`.
3. **Process each frame**:
   - Converts the frame to grayscale (Haar Cascades perform detection on grayscale images).
   - Runs `detectMultiScale` to locate faces, with tunable parameters:
     - `scaleFactor=1.1` — how much the image size is reduced at each image scale.
     - `minNeighbors=5` — how many neighbors each candidate rectangle should have to retain it.
     - `minSize=(30, 30)` — minimum possible face size to detect.
4. **Draw results** — Draws a green rectangle and label over each detected face.
5. **Display & exit** — Shows the annotated frame in a window and exits cleanly when `q` is pressed or the camera fails.

## Troubleshooting

| Issue | Possible Fix |
|---|---|
| `Error: could not open camera.` | Check that your webcam is connected and not in use by another application. Try changing `VideoCapture(0)` to `VideoCapture(1)` if you have multiple cameras. |
| No window appears | Ensure you're running the script in an environment with GUI support (not a headless server). |
| Poor detection accuracy | Adjust `scaleFactor`, `minNeighbors`, or lighting conditions. Haar Cascades work best in good, even lighting with faces facing the camera. |

## Notes

- Haar Cascade classifiers are fast but less accurate than modern deep-learning-based detectors (e.g., DNN or MTCNN models). For more robust detection, consider upgrading to a DNN-based face detector.
- This script only detects faces; it does not perform face recognition (identifying *who* the face belongs to).

## License

Free to use and modify for personal or educational purposes.
