# Image Transformations Using OpenCV
# Name : Hari Prasath E
# Reg No : 212225040107

---

## AIM

To write a Python program using OpenCV to perform image transformations such as translation, scaling, shearing, reflection, rotation, and cropping.

---

## Software Required

- Anaconda - Python 3.7
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy (`numpy`)
- Matplotlib (`matplotlib`)

---

## Algorithm

### Step 1:
Import the required libraries and load the image using OpenCV. Display the original image.

### Step 2:
Perform image translation by shifting the image horizontally by 100 pixels and vertically by 50 pixels.

### Step 3:
Perform image scaling using the scaling factors `fx = 5.0` and `fy = 2.0`.

### Step 4:
Perform image shearing using a shearing matrix with a factor of 0.5.

### Step 5:
Reflect the image using the OpenCV `cv2.flip()` function.

### Step 6:
Rotate the image by 45 degrees around its center.

### Step 7:
Crop a region of the image starting at coordinates (100, 100), with a width of 200 pixels and a height of 150 pixels.

### Step 8:
Display the transformed images.

---

# Ex. No. 04

## 1. Load and Display the Original Image

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('wp img.jpeg')

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')
plt.show()
```

## 2. Image Translation

```python
tx, ty = 100, 50

M_translation = np.float32([[1, 0, tx], [0, 1, ty]])

translated_image = cv2.warpAffine(
    image,
    M_translation,
    (image.shape[1], image.shape[0])
)

plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))
plt.title("Translated Image")
plt.axis('off')
plt.show()
```

## 3. Image Scaling

```python
fx, fy = 5.0, 2.0

scaled_image = cv2.resize(
    image,
    None,
    fx=fx,
    fy=fy,
    interpolation=cv2.INTER_LINEAR
)

plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))
plt.title("Scaled Image")
plt.axis('off')
plt.show()
```

## 4. Image Shearing

```python
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])

sheared_image = cv2.warpAffine(
    image,
    shear_matrix,
    (image.shape[1], image.shape[0])
)

plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))
plt.title("Sheared Image")
plt.axis('off')
plt.show()
```

## 5. Image Reflection

```python
reflected_image = cv2.flip(image, 2)

plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))
plt.title("Reflected Image")
plt.axis('off')
plt.show()
```

## 6. Image Rotation

```python
(height, width) = image.shape[:2]

angle = 45

center = (width // 2, height // 2)

M_rotation = cv2.getRotationMatrix2D(center, angle, 1)

rotated_image = cv2.warpAffine(
    image,
    M_rotation,
    (width, height)
)

plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))
plt.title("Rotated Image")
plt.axis('off')
plt.show()
```

## 7. Image Cropping

```python
x, y, w, h = 100, 100, 200, 150

cropped_image = image[y:y+h, x:x+w]

plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))
plt.title("Cropped Image")
plt.axis('off')
plt.show()
```

---

# Output

## i) Original Image
<img width="700" height="558" alt="image" src="https://github.com/user-attachments/assets/4eefb0e3-9b5d-432d-9a2b-7161392c1ea0" />

## ii) Translated Image
<img width="702" height="558" alt="image" src="https://github.com/user-attachments/assets/975ab5ac-ef0c-4ba4-b271-3d4080b8036f" />

## iii) Scaled Image
<img width="727" height="260" alt="image" src="https://github.com/user-attachments/assets/9e646af9-d153-4998-90ec-f620483c5d7d" />

## iv) Sheared Image
<img width="696" height="550" alt="image" src="https://github.com/user-attachments/assets/d500ab55-c5f7-46f0-ad42-484142921032" />

## v) Reflected Image
<img width="697" height="556" alt="image" src="https://github.com/user-attachments/assets/1d132b6c-40f5-40a1-a234-e48fce9f61c9" />

## vi) Rotated Image
<img width="707" height="557" alt="image" src="https://github.com/user-attachments/assets/ba98161f-836a-49fc-9c6b-5a3aa76075aa" />

## vii) Cropped Image
<img width="696" height="547" alt="image" src="https://github.com/user-attachments/assets/2450848e-ea9d-4b5e-a65b-008cf77301e8" />

---

# Result

Thus, image transformations including translation, scaling, shearing, reflection, rotation, and cropping were performed using OpenCV and Python.
