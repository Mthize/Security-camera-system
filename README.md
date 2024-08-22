# Face and Body Detection Camera

This project implements a camera system that detects faces and bodies, automatically recording video when detection occurs.

## Installation

1. Ensure you have Python installed on your system.
2. Install the required library:

3. ## Project Structure

The main components of the code are:

1. **Importing Libraries**: The necessary libraries are imported to handle video capturing, face and body detection, and to manage time.
2. **VideoCapture Initialization**: The camera is initialized to capture video frames.
3. **Cascade Classifiers**: Pre-trained Haar Cascade classifiers are loaded for detecting faces and bodies.
4. **Detection Logic**: The main loop checks for the presence of faces and bodies, handles video recording, and displays the video feed.

## Code Explanation

### Imports

```python
import cv2
import time
import datetime

cap = cv2.VideoCapture(0)
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_frontalface_default.xml")
body_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_fullbody.xml")

detection = False
detection_stopped_time = None
timer_started = False
SECONDS_TO_RECORD_AFTER_DETECTION = 5

frame_size = (int(cap.get(3)), int(cap.get(4)))
fourcc = cv2.VideoWriter_fourcc(*"mp4v")
out = None

frame_size = (int(cap.get(3)), int(cap.get(4)))
fourcc = cv2.VideoWriter_fourcc(*"mp4v")
out = None

while True:
    _, frame = cap.read()
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    faces = face_cascade.detectMultiScale(gray, 1.3, 5)
    bodies = body_cascade.detectMultiScale(gray, 1.3, 5)

if len(faces) + len(bodies) > 0:
    ...
else:
    ...

cv2.imshow("Camera", frame)
if cv2.waitKey(1) == ord('q'):
    break

if out:
    out.release()
cap.release()
cv2.destroyAllWindows()

License
This project is open-source, and you are free to modify and use it as needed.
