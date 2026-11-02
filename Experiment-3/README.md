
# Histogram Equalization Using OpenCV

## Name: Hari Prasath E  
## Reg No: 212225040107

---

## AIM

To write a Python program using OpenCV to perform histogram equalization on grayscale and color images to improve image contrast.

## Software Required

- Anaconda – Python 3.7
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy (`numpy`)
- Matplotlib (`matplotlib`)

## Algorithm

1. Import the required libraries.
2. Read and display the grayscale image.
3. Plot the histogram of the original grayscale image.
4. Apply histogram equalization using `cv2.equalizeHist()`.
5. Display the equalized grayscale image and its histogram.
6. Read the color image and convert it from BGR to HSV color space.
7. Apply histogram equalization to the Value (V) channel.
8. Convert the image back to BGR color space.
9. Display the original color image, equalized image, and their histograms.

## Program

### 1. Import Libraries and Display the Original Grayscale Image

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('gray.png', cv2.IMREAD_GRAYSCALE)

plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.show()
```

### 2. Display the Original Image Histogram

```python
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Image Histogram')
plt.show()
```

### 3. Apply Histogram Equalization

```python
img_eq = cv2.equalizeHist(img)

plt.imshow(img_eq, cmap='gray')
plt.title('Equalized Image')
plt.show()
```

### 4. Display the Equalized Image Histogram

```python
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Histogram')
plt.show()
```

### 5. Perform Histogram Equalization on a Color Image

```python
img = cv2.imread('color.png', cv2.IMREAD_COLOR)

img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])

img_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)
```

### 6. Display Color Images and Histograms

```python
plt.figure(figsize=[12, 10])

plt.subplot(221)
plt.imshow(img[:, :, ::-1])
plt.title('Original Color Image')

plt.subplot(222)
plt.imshow(img_eq[:, :, ::-1])
plt.title('Equalized Image')

plt.subplot(223)
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Histogram')

plt.subplot(224)
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Histogram Equalized')

plt.show()
```

# Output

## The following results are obtained by executing the program:

# 1. Original grayscale image.
<img width="706" height="485" alt="image" src="https://github.com/user-attachments/assets/e6970ac6-18af-4a7d-b116-417188bc45d7" />

# 2. Histogram of the original grayscale image.
<img width="757" height="546" alt="image" src="https://github.com/user-attachments/assets/b3b86975-017b-400a-93be-21a0dbaac188" />

# 3. Equalized grayscale image with improved contrast.
<img width="745" height="487" alt="image" src="https://github.com/user-attachments/assets/c2419291-acda-4998-b87a-636ab667dc16" />

# 4. Histogram of the equalized grayscale image.
<img width="733" height="552" alt="image" src="https://github.com/user-attachments/assets/25c97937-70cd-4c2b-abce-518707fb789f" />

# 5. Original color image & Equalized color image & Original and equalized color image histograms.
<img width="1065" height="787" alt="image" src="https://github.com/user-attachments/assets/e4de3950-c444-4379-a74e-6ce516fd0117" />

# Result

Thus, histogram equalization was performed on grayscale and color images using OpenCV. The grayscale image was equalized directly, while the color image was processed by equalizing the Value (V) channel in HSV color space.
