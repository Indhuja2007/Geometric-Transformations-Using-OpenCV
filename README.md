# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program And Output

### Developed By: 
**Name: INDHUJA.K**  
### Register No: 212225040133


---
## Import Libraries and Read Image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("space.jpeg")
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img)
plt.title("Original Image")
plt.axis("off")
plt.show()
```
<img width="397" height="520" alt="image" src="https://github.com/user-attachments/assets/0e648724-2526-4416-9637-3429c355ff32" />

## Image Translation
```
rows, cols = img.shape[:2]

M = np.float32([[1, 0, 50],
                [0, 1, 80]])

translated = cv2.warpAffine(img, M, (cols, rows))

plt.subplot(1, 2, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(translated)
plt.title("Translated Image")
plt.axis("off")

plt.show()
```
<img width="646" height="392" alt="image" src="https://github.com/user-attachments/assets/fcec2c9e-18dc-4f0f-9e03-be118529f24a" />

## Image Scaling
```
small = cv2.resize(img, None, fx=0.5, fy=0.5)
large = cv2.resize(img, None, fx=2, fy=2)

plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(small)
plt.title("Downscaled Image")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(large)
plt.title("Upscaled Image")
plt.axis("off")

plt.show()
```
<img width="1151" height="442" alt="image" src="https://github.com/user-attachments/assets/c8ed6957-cdbb-409c-a1fc-20561bb68422" />

## Image Shearing
```
rows, cols = img.shape[:2]

M1 = np.float32([[1, 0.5, 0],
                 [0, 1, 0]])

M2 = np.float32([[1, 0, 0],
                 [0.5, 1, 0]])

horizontal = cv2.warpAffine(img, M1, (cols, rows))
vertical = cv2.warpAffine(img, M2, (cols, rows))

plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(horizontal)
plt.title("Horizontal Shearing")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(vertical)
plt.title("Vertical Shearing")
plt.axis("off")

plt.show()
```
<img width="1153" height="432" alt="image" src="https://github.com/user-attachments/assets/49b3c41c-1383-4ca7-afd8-7ab9586c4337" />

## Image Reflection (Flipping)
```
horizontal = cv2.flip(img, 1)
vertical = cv2.flip(img, 0)
both = cv2.flip(img, -1)

plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.imshow(horizontal)
plt.title("Horizontal Flip")
plt.axis("off")

plt.subplot(2, 2, 3)
plt.imshow(vertical)
plt.title("Vertical Flip")
plt.axis("off")

plt.subplot(2, 2, 4)
plt.imshow(both)
plt.title("Both Axes Flip")
plt.axis("off")

plt.show()
```
<img width="668" height="657" alt="image" src="https://github.com/user-attachments/assets/90e9fb65-6a8b-4801-a3a5-76916542f1cb" />

## Image Rotation
```
rows, cols = img.shape[:2]
center = (cols // 2, rows // 2)

M1 = cv2.getRotationMatrix2D(center, 45, 1)
M2 = cv2.getRotationMatrix2D(center, 90, 1)

rotated45 = cv2.warpAffine(img, M1, (cols, rows))
rotated90 = cv2.warpAffine(img, M2, (cols, rows))

plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(rotated45)
plt.title("45 Degree Rotation")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(rotated90)
plt.title("90 Degree Rotation")
plt.axis("off")

plt.show()
```
<img width="927" height="352" alt="image" src="https://github.com/user-attachments/assets/fdfdaf7d-db05-4665-be36-f99369795d08" />

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
