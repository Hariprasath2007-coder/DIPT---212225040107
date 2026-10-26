
# Image-Handling-and-Pixel-Transformations-Using-OpenCV 
# NAME : Hari Prasath E
# Reg No : 212225040107

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Draw a line from the top-left to the bottom-right of the image. Draw a circle at the center of the image. Draw a rectangle around a specific region of interest in the image. Add the text "OpenCV Drawing" at the top-left corner of the image.

### Step 3:
Convert the image from RGB to HSV and display it. Convert the image from RGB to GRAY and display it. Convert the image from RGB to YCrCb and display it. Convert the HSV image back to RGB and display it.

### Step 4:
Access and print the pixel value at coordinates (100, 100). Modify a 300x300 region of pixels, starting at (200, 200), to white.

### Step 5:
Resize the original image to half its size and display it.

### Step 6:
Crop a region of interest (ROI) from the image and display it.

### Step 7:
Flip the original image horizontally and display it. Flip the original image vertically and display it.

### Step 8:
Save the final modified image to your local directory.

# Ex. No. 01

#### 1. Read the image ('rk.png') using OpenCV imread().
```python
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('rk.png', cv2.IMREAD_COLOR)
```

#### 2. Convert BGR to RGB.
```python
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img_rgb, cmap='viridis')
plt.title("Original Image")
plt.axis('off')
plt.show()
```

#### 4. Draw a line from the top-left to the bottom-right of the image.
```python
image = cv2.imread('rk.png')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2)

plt.imshow(line_img, cmap='viridis')
plt.title("Image with Line")
plt.axis('off')
plt.show()
```

#### 5. Draw a circle at the center of the image.
```python
image = cv2.imread('rk.png')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

circle_img = cv2.circle(img_rgb, (400, 300), 150, (255, 0, 0), 10)

plt.imshow(circle_img, cmap='viridis')
plt.title("Image with Circle")
plt.axis('off')
plt.show()
```

#### 6. Draw a rectangle around the whole image.
```python
image = cv2.imread('rk.png')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

rectangle_img = cv2.rectangle(img_rgb, (0, 0), (768, 600), (0, 0, 255), 10)

plt.imshow(rectangle_img, cmap='viridis')
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()
```

#### 7. Add the text "OpenCV Drawing" at the top-left corner of the image.
```python
image = cv2.imread('rk.png')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30),
                       cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 0, 0), 2)

plt.imshow(text_img, cmap='viridis')
plt.title("Image with Text")
plt.axis('off')
plt.show()
```

#### 8. Convert the image from RGB to HSV and display it.
```python
image = cv2.imread('rk.png')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
plt.show()

image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
plt.show()
```

#### 9. Convert the image from RGB to GRAY and display it.
```python
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()
```

#### 10. Convert the image from RGB to YCrCb and display it.
```python
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
plt.show()
```

#### 11. Convert the HSV image back to RGB and display it.
```python
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()
```

#### 12. Access and print the pixel value at coordinates (100, 100).
```python
image = cv2.imread('rk.png')
print(image[100, 100])
```

#### 13. Modify a 300x300 region of pixels to white, starting at (200, 200).
```python
image = cv2.imread('rk.png')

image[200:500, 200:500] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
```

#### 14. Resize the original image to half its size.
```python
image = cv2.imread('rk.png')

resized_image = cv2.resize(image, (768 // 2, 600 // 2))

resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

#### 15. Crop a 300x300 region of interest (ROI) starting at (50, 50).
```python
image = cv2.imread('rk.png')

roi = image[50:350, 50:350]

roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

#### 16. Flip the original image horizontally and display it.
```python
image = cv2.imread('rk.png')

flipped_horizontally = cv2.flip(image, 1)

flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()
```

#### 17. Flip the original image vertically and display it.
```python
flipped_vertically = cv2.flip(image, 0)

flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()
```

#### 18. Save the final modified image to your local directory.
```python
cv2.imwrite('final_modified_image.png', image)
```

# Output:
## 1.Read and Display an Image.
<img width="703" height="445" alt="image" src="https://github.com/user-attachments/assets/dfab4648-b9d6-4a6b-989c-d8f2848525f5" />

## 2.Draw a Line, Circle, Rectangle, and Text on the Image.
<img width="702" height="441" alt="image" src="https://github.com/user-attachments/assets/c4fafc16-662f-4801-ba6c-f7dd41667380" />
<img width="700" height="435" alt="image" src="https://github.com/user-attachments/assets/7efe7309-dea0-4454-9555-f1d19949e72b" />
<img width="697" height="437" alt="image" src="https://github.com/user-attachments/assets/34169dd5-99d7-4d60-b4ff-eae969290729" />
<img width="707" height="437" alt="image" src="https://github.com/user-attachments/assets/e7eb8f14-525e-4078-a99b-74cb0acfce66" />

## 3.Convert the Image into HSV, GRAY, and YCrCb Color Spaces.
<img width="707" height="437" alt="image" src="https://github.com/user-attachments/assets/60c2f216-b7a9-4796-978b-16cfc4c93841" />
<img width="706" height="440" alt="image" src="https://github.com/user-attachments/assets/cc946a66-b8b4-40cb-81fe-fa5c0acdea77" />
<img width="711" height="430" alt="image" src="https://github.com/user-attachments/assets/8969d62c-35d1-489f-aa24-390ab222ff54" />

## 4.Access and Modify Pixel Values.
<img width="691" height="441" alt="image" src="https://github.com/user-attachments/assets/5e592bed-61c9-47ae-bc3c-8b3f69592d15" />

## 5.Resize the Image to Half its Size.
<img width="676" height="565" alt="image" src="https://github.com/user-attachments/assets/c1830c7f-e051-4db9-8748-1dad2723c65a" />

## 6.Crop a Region of Interest (ROI).
<img width="538" height="566" alt="image" src="https://github.com/user-attachments/assets/b4ab0c07-3b32-4d37-b17a-b71edac011b8" />

## 7.Flip the Image Horizontally and Vertically.
<img width="700" height="427" alt="image" src="https://github.com/user-attachments/assets/290506fc-9fe3-4d5d-9610-15aa3023eade" />
<img width="705" height="436" alt="image" src="https://github.com/user-attachments/assets/d82d3177-30df-43fe-882f-172c4d03c46e" />

# Result:
Thus, the image was loaded and displayed, drawing operations and color-space conversions were performed, pixel values were accessed and modified, and resizing, cropping, and flipping operations were carried out using OpenCV and Python.
