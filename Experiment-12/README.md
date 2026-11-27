
# EXPERIMENT 12 : PROJECT - FACE DETECTION WITH HAAR CASCADES

## NAME : Hari Prasath E

## REG NO : 212225040107

## AIM:

To write a Python program using OpenCV to perform the following image manipulations:

i) Extract ROI from an image.

ii) Perform face detection using Haar Cascades in static images.

iii) Perform eye detection in images.

iv) Perform face detection with labels in real-time video from webcam.

## SOFTWARE REQUIRED:

- Anaconda - Python 3.11
- OpenCV library (`opencv-python`)
- Matplotlib library (`matplotlib`)
- Jupyter Notebook
- Haar Cascade Classifiers

## ALGORITHM:

### I) Load and Display Images

**Step 1:** Import necessary packages such as `cv2` and `matplotlib.pyplot`.

**Step 2:** Load the input image using `cv2.imread()`.

**Step 3:** Convert the image from BGR to RGB and grayscale using `cv2.cvtColor()`.

**Step 4:** Display the image using `plt.imshow()`.

### II) Extract Region of Interest (ROI)

**Step 1:** Convert the image into RGB format.

**Step 2:** Extract the required region using NumPy slicing.

**Step 3:** Display the original image and extracted ROI using `plt.subplot()` and `plt.imshow()`.

### III) Load Haar Cascade Classifiers

**Step 1:** Load the face cascade XML file using `cv2.CascadeClassifier()`.

**Step 2:** Load the eye cascade XML file using `cv2.CascadeClassifier()`.

### IV) Perform Eye Detection in Images

**Step 1:** Detect faces using `face_cascade.detectMultiScale()` to locate the eye region.

**Step 2:** Extract the upper portion of each detected face.

**Step 3:** Detect eyes using `eye_cascade.detectMultiScale()`.

**Step 4:** Draw green rectangles around the detected eyes using `cv2.rectangle()`.

**Step 5:** Display the eye detection result using Matplotlib.

### V) Perform Face Detection in Images

**Step 1:** Use `face_cascade.detectMultiScale()` to detect faces in the grayscale image.

**Step 2:** Draw green rectangles around detected faces using `cv2.rectangle()`.

**Step 3:** Convert the processed image from BGR to RGB.

**Step 4:** Display the face detection result using `plt.imshow()`.

### VI) Perform Face Detection on Real-Time Webcam Video

**Step 1:** Capture video from the webcam using `cv2.VideoCapture(0)`.

**Step 2:** Continuously read frames from the webcam.

**Step 3:** Convert each frame into grayscale using `cv2.cvtColor()`.

**Step 4:** Apply `face_cascade.detectMultiScale()` to detect faces.

**Step 5:** Draw green rectangles around detected faces using `cv2.rectangle()`.

**Step 6:** Display the label "Face Detected" using `cv2.putText()`.

**Step 7:** Convert the frame from BGR to RGB and display it using Matplotlib.

**Step 8:** Release the video capture and close the display when the webcam is interrupted.

## PROCEDURE:

1. Open Anaconda Navigator and launch Jupyter Notebook.
2. Create a new Python notebook.
3. Import OpenCV and Matplotlib libraries.
4. Load the input image `hari.png`.
5. Load the Haar Cascade face and eye classifiers.
6. Extract and display the Region of Interest (ROI).
7. Perform eye detection in the input image.
8. Perform face detection in the input image.
9. Execute real-time face detection using the webcam.
10. Observe and verify the output images.

## PROGRAM:

The complete Python program is available in the Jupyter Notebook.

**Input Image:** `hari.png`



## CODE 
```

import cv2
import matplotlib.pyplot as plt

# Load image
img = cv2.imread('hari.png')

if img is None:
    raise FileNotFoundError("Image not found! Check hari.png filename.")

# Convert image to grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Load Haar Cascade classifiers
face_cascade = cv2.CascadeClassifier(
    cv2.data.haarcascades + 'haarcascade_frontalface_default.xml'
)

eye_cascade = cv2.CascadeClassifier(
    cv2.data.haarcascades + 'haarcascade_eye_tree_eyeglasses.xml'
)

if face_cascade.empty() or eye_cascade.empty():
    raise RuntimeError("Haar Cascade files could not be loaded!")


# --------------------------------------------------
# 1. REGION OF INTEREST (ROI) EXTRACTION
# --------------------------------------------------

# Convert BGR to RGB
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Extract ROI
roi = rgb[100:300, 100:300]

# Display original image and ROI
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(roi)
plt.title("Extracted ROI")
plt.axis('off')

plt.show()


# --------------------------------------------------
# 2. EYE DETECTION
# --------------------------------------------------

# Read image
eye_img = img.copy()

# Detect faces to locate eyes
faces = face_cascade.detectMultiScale(
    gray,
    scaleFactor=1.1,
    minNeighbors=6,
    minSize=(100, 100)
)

# Detect eyes inside each face
for (x, y, w, h) in faces:

    face_gray = gray[y:y+h, x:x+w]

    # Extract upper portion of face
    upper_face = face_gray[0:int(h * 0.55), :]

    eyes = eye_cascade.detectMultiScale(
        upper_face,
        scaleFactor=1.05,
        minNeighbors=5,
        minSize=(25, 15)
    )

    # Draw rectangles around detected eyes
    for (ex, ey, ew, eh) in eyes:
        cv2.rectangle(
            eye_img,
            (x + ex, y + ey),
            (x + ex + ew, y + ey + eh),
            (0, 255, 0),
            2
        )

# Convert BGR to RGB
eye_img = cv2.cvtColor(eye_img, cv2.COLOR_BGR2RGB)

# Display eye detection output
plt.figure(figsize=(8, 8))
plt.imshow(eye_img)
plt.title("Eye Detection")
plt.axis('off')
plt.show()


# --------------------------------------------------
# 3. FACE DETECTION
# --------------------------------------------------

# Detect faces
faces = face_cascade.detectMultiScale(
    gray,
    scaleFactor=1.1,
    minNeighbors=5
)

face_img = img.copy()

# Draw rectangles around detected faces
for (x, y, w, h) in faces:
    cv2.rectangle(
        face_img,
        (x, y),
        (x + w, y + h),
        (0, 255, 0),
        2
    )

# Convert BGR to RGB
face_img = cv2.cvtColor(face_img, cv2.COLOR_BGR2RGB)

# Display face detection output
plt.figure(figsize=(8, 8))
plt.imshow(face_img)
plt.title("Face Detection")
plt.axis('off')
plt.show()
```

## OUTPUT:

### 1. Region of Interest (ROI) Extraction
<img width="1022" height="510" alt="image" src="https://github.com/user-attachments/assets/b73c3835-9f47-4799-85f3-6f28df5f868a" />

### 2. Eye Detection
<img width="600" height="622" alt="image" src="https://github.com/user-attachments/assets/edc460b7-a420-4ad2-b490-b356d4dc8c21" />

### 3. Face Detection
<img width="595" height="625" alt="image" src="https://github.com/user-attachments/assets/ab667a3d-ee9f-4ef0-a8f4-df31bf20b556" />

## RESULT:

Thus, the Python program for extracting the Region of Interest, detecting faces and eyes using Haar Cascade classifiers, and performing real-time face detection using OpenCV and Matplotlib was executed successfully.
