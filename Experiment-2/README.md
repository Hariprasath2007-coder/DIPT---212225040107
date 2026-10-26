
# Image Capture and Video Processing Using OpenCV
# Name : Hari Prasath E
# Reg No : 212225040107
---

## Aim

To write a Python program using OpenCV to capture an image from the webcam and perform the following operations:

1. Write the frame as a JPG file
2. Display the video
3. Display the video by resizing the window
4. Rotate and display the video

---

## 🛠️ Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)

---

## ⚙️ Algorithm

### Step 1:
Import the required libraries, including OpenCV, Matplotlib, `clear_output`, and `time`.

### Step 2:
Initialize the webcam using `cv2.VideoCapture(0)`, capture a frame, and save it using `cv2.imwrite()`.

### Step 3:
Read the saved image and display the captured frame using Matplotlib.

### Step 4:
Capture and display 50 video frames by converting each frame from BGR to RGB.

### Step 5:
Resize each captured video frame to `(100, 150)` and display the resized frames.

### Step 6:
Rotate each captured video frame by 90 degrees clockwise and display the rotated frames.

### Step 7:
Release the webcam after completing each operation.

---

# Ex. No. 02

## i) Write the frame as JPG file

```python
import cv2
import matplotlib.pyplot as plt
from IPython.display import clear_output
import time

cap = cv2.VideoCapture(0)
ret, frame = cap.read()

if ret:
    cv2.imwrite("yt banner.png", frame)

cap.release()

captured_image = cv2.imread('yt banner.png')

plt.imshow(captured_image[:,:,::-1])
plt.title('Captured Frame')
plt.axis('off')
plt.show()
```

## ii) Display the video

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break
    frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis('off')
    plt.show()
    time.sleep(0.05)

cap.release()
```

## iii) Display the video by resizing the window

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break
    resized_frame = cv2.resize(frame, (100, 150))
    frame_rgb = cv2.cvtColor(resized_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis('off')
    plt.show()
    time.sleep(0.05)

cap.release()
```

## iv) Rotate and display the video

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break
    rotated_frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
    frame_rgb = cv2.cvtColor(rotated_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis('off')
    plt.show()
    time.sleep(0.05)

cap.release()
```

---

# Output

## i) Write the frame as JPG file
<img width="711" height="560" alt="image" src="https://github.com/user-attachments/assets/26bfb573-8b42-443e-9777-c3bd361f3836" />

## ii) Display the video
<img width="686" height="527" alt="image" src="https://github.com/user-attachments/assets/1de4a074-517d-4dcd-a52c-04848604cbdb" />

## iii) Display the video by resizing the window
<img width="361" height="542" alt="image" src="https://github.com/user-attachments/assets/f58bb157-e170-4c3a-a7fe-0e83214e6d0f" />

## iv) Rotate and display the video
<img width="415" height="537" alt="image" src="https://github.com/user-attachments/assets/fa6ca7db-069c-4dee-bc06-73b052047f05" />

---

# Result

Thus, a frame was captured from the webcam and saved, and video processing operations such as displaying, resizing, and rotating the frames were performed using OpenCV and Python.
