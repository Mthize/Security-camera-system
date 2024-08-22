# Real-Time Face and Body Detection with Video Recording

This project implements real-time face and body detection using OpenCV. When a face or body is detected, the program records a video for a specified duration.

## Requirements

- Python 3.x
- OpenCV library

You can install OpenCV using pip if you haven't already:

```bash
pip install opencv-python

Project Structure

The main components of the code are:

	1.	Importing Libraries: The necessary libraries are imported to handle video capturing, face and body detection, and to manage time.
	2.	VideoCapture Initialization: The camera is initialized to capture video frames.
	3.	Cascade Classifiers: Pre-trained Haar Cascade classifiers are loaded for detecting faces and bodies.
	4.	Detection Logic: The main loop checks for the presence of faces and bodies, handles video recording, and displays the video feed.

Code Explanation

Imports

import cv2
import time
import datetime

The code begins by importing the necessary libraries.

Initializing VideoCapture and Cascade Classifiers

cap = cv2.VideoCapture(0)
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_frontalface_default.xml")
body_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_fullbody.xml")

	•	cv2.VideoCapture(0): Initializes the camera for video input.
	•	CascadeClassifier: Loads pre-trained classifiers for face and body detection.

Variables

detection = False
detection_stopped_time = None
timer_started = False
SECONDS_TO_RECORD_AFTER_DETECTION = 5

	•	Flags and timers are defined to manage detection states and recording duration.

Video Writer Initialization

frame_size = (int(cap.get(3)), int(cap.get(4)))
fourcc = cv2.VideoWriter_fourcc(*"mp4v")
out = None

	•	Sets the frame size and codec for the video writer.

Main Loop

while True:
    _, frame = cap.read()
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    faces = face_cascade.detectMultiScale(gray, 1.3, 5)
    bodies = body_cascade.detectMultiScale(gray, 1.3, 5)

	•	The loop reads frames from the camera, converts them to grayscale, and detects faces and bodies.

Detection Logic

if len(faces) + len(bodies) > 0:
    ...
else:
    ...

	•	If faces or bodies are detected, it starts recording. If no detection occurs, it checks if a timer has expired to stop the recording.

Display and Exit Conditions

cv2.imshow("Camera", frame)
if cv2.waitKey(1) == ord('q'):
    break

	•	Displays the video feed and allows the user to exit by pressing ‘q’.

Cleanup

if out:
    out.release()
cap.release()
cv2.destroyAllWindows()

	•	Releases resources when the program ends.

Usage

Run the script, and a window will open displaying the camera feed. The program will start recording when it detects a face or body, and it will stop after a specified duration without detection.

License

This project is open-source, and you are free to modify and use it as needed.


Feel free to modify any sections as per your project's specific needs or additional functionalities!