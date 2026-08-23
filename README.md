# Experiment 6
# Edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

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
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2:
Load an image using `cv2.imread()`.
```
image = cv2.imread("place.jpeg")

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")
plt.show()
```

### Step 3:
Convert the image to grayscale.
```
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(gray, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")
plt.show()
```

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.
```
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)

sobel = cv2.magnitude(
    sobel_x.astype(np.float32),
    sobel_y.astype(np.float32)
)

plt.imshow(sobel, cmap="gray")
plt.title("Sobel Edge Detection")
plt.axis("off")
plt.show()
```


### Step 5:
Apply **Prewitt operator** using custom kernels.
```
prewitt_x = np.array([
    [-1, 0, 1],
    [-1, 0, 1],
    [-1, 0, 1]
])

prewitt_y = np.array([
    [-1, -1, -1],
    [0, 0, 0],
    [1, 1, 1]
])

prewitt_x_edge = cv2.filter2D(gray, cv2.CV_64F, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, cv2.CV_64F, prewitt_y)

prewitt = cv2.magnitude(
    prewitt_x_edge.astype(np.float32),
    prewitt_y_edge.astype(np.float32)
)

plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt Edge Detection")
plt.axis("off")
plt.show()
```


### Step 6:
Apply **Roberts operator** using custom kernels.
```
roberts_x = np.array([
    [1, 0],
    [0, -1]
], dtype=np.float32)

roberts_y = np.array([
    [0, 1],
    [-1, 0]
], dtype=np.float32)

roberts_x_edge = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
roberts_y_edge = cv2.filter2D(gray, cv2.CV_32F, roberts_y)

roberts = cv2.magnitude(
    roberts_x_edge,
    roberts_y_edge
)

plt.imshow(roberts, cmap="gray")
plt.title("Roberts Edge Detection")
plt.axis("off")
plt.show()
```

### Step 7:
Apply **Laplacian operator** using OpenCV.
```
laplacian = cv2.Laplacian(gray, cv2.CV_64F)

plt.imshow(np.abs(laplacian), cmap="gray")
plt.title("Laplacian Edge Detection")
plt.axis("off")
plt.show()
```

### Step 8:
Apply **Canny edge detector** using OpenCV.
```
canny = cv2.Canny(gray, 50, 150)

plt.imshow(canny, cmap="gray")
plt.title("Canny Edge Detection")
plt.axis("off")
plt.show()
```

### Step 9:
Display all edge-detected images for comparison.
```
plt.figure(figsize=(15, 10))

plt.subplot(2, 3, 1)
plt.imshow(gray, cmap="gray")
plt.title("Grayscale")
plt.axis("off")

plt.subplot(2, 3, 2)
plt.imshow(sobel, cmap="gray")
plt.title("Sobel")
plt.axis("off")

plt.subplot(2, 3, 3)
plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt")
plt.axis("off")

plt.subplot(2, 3, 4)
plt.imshow(roberts, cmap="gray")
plt.title("Roberts")
plt.axis("off")

plt.subplot(2, 3, 5)
plt.imshow(np.abs(laplacian), cmap="gray")
plt.title("Laplacian")
plt.axis("off")

plt.subplot(2, 3, 6)
plt.imshow(canny, cmap="gray")
plt.title("Canny")
plt.axis("off")

plt.tight_layout()
plt.show()
```

---

## Developed By

- **Name:** Madhan M
- **Register No:** 212225040213

---

## Output

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  

<img width="334" height="476" alt="image" src="https://github.com/user-attachments/assets/0a945067-1613-44ba-bc5c-59336f577311" />


###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

<img width="255" height="387" alt="image" src="https://github.com/user-attachments/assets/278a181b-1392-4002-ba55-632dfa1746d3" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  

<img width="253" height="381" alt="image" src="https://github.com/user-attachments/assets/bc9d1301-47d6-4f56-ae31-11519cd16ad7" />


###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

<img width="265" height="382" alt="image" src="https://github.com/user-attachments/assets/c7472fe2-1801-4bcf-98b6-f7a597d71fea" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

<img width="276" height="388" alt="image" src="https://github.com/user-attachments/assets/bd936be7-0878-4267-860e-d67b1cc27aba" />



---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.


<img width="615" height="491" alt="image" src="https://github.com/user-attachments/assets/1dca487f-62b9-4918-9e62-857eb1be4fee" />
