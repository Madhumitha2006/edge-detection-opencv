# edge-detection-opencv
## Aim
To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** MADHU MITHA v
- **Register No:** 2305002013 
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
 image = cv2.imread('heidi.png')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  # Sobel in x direction
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  # Sobel in y direction
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  # Combine both directions
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')

laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')

canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')

image = cv2.imread("heidi.png")

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

plt.imshow(canny_edges, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')

roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

roberts_x_edge = cv2.filter2D(gray, -1, roberts_x)
roberts_y_edge = cv2.filter2D(gray, -1, roberts_y)
roberts = cv2.magnitude(roberts_x_edge.astype(np.float32),
                        roberts_y_edge.astype(np.float32))
plt.imshow(canny_edges, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')  

```

## Output
<img width="406" height="514" alt="image" src="https://github.com/user-attachments/assets/febfb8a2-a349-4934-98c8-7b264d1994a6" />

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  
<img width="397" height="540" alt="image" src="https://github.com/user-attachments/assets/58e49401-31eb-475a-a553-a67754a00917" />

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges
  <img width="377" height="512" alt="image" src="https://github.com/user-attachments/assets/7236d91d-59e1-43e1-a88c-773a8dff0143" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise
  <img width="379" height="528" alt="image" src="https://github.com/user-attachments/assets/5b07bf5f-b1ed-44d4-b37c-655a71245f9e" />

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes
  <img width="389" height="520" alt="image" src="https://github.com/user-attachments/assets/7a622219-4a67-449a-a895-897d2ec2086e" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  
<img width="377" height="509" alt="image" src="https://github.com/user-attachments/assets/b021e4e8-00b5-40d7-a080-bad96c9b67d4" />

---

## Result
Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
