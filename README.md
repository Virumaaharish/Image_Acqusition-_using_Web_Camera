
Aim:
 
To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.
i) Write the frame as JPG 
ii) Display the video 
iii) Display the video by resizing the window
iv) Rotate and display the video
# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

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
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** VIRUMAA HARISH M
- **Register Number:** 212223230246

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('diptimage.png', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```
### OUTPUT:
(560, 487, 3)

#### 3. Display the image using matplotlib imshow().
```python
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(img_gray,cmap='gray')
plt.show()
```
#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
img=cv2.imread('diptimage.png')
cv2.imwrite('dipt_image.png',img)
```
### OUTPUT:
True

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img=cv2.imread('diptimage.png')
img_rgb = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img)
plt.show()
img.shape
```
#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```
#### 8. Resize the image up by a factor of 2x.
```python
res= cv2.resize(crop,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
```
#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img=cv2.imread('diptimage2.png',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```
### OUTPUT:
(405, 528, 3)

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Apollo 11 Saturn V Launch, July 16, 1969", (300, 700),cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()
```
#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)
```
### OUTPUT:
array([[[ 81, 104, 137],
        [ 82, 105, 137],
        [ 82, 104, 141],
        ...,
        [ 81, 103, 136],
        [ 80, 102, 137],
        [ 80, 103, 137]],

       [[ 81, 103, 139],
        [ 82, 104, 140],
        [ 82, 104, 139],
        ...,
        [ 80, 102, 136],
        [ 80, 103, 137],
        [ 79, 103, 136]],

       [[ 81, 104, 137],
        [ 82, 105, 138],
        [ 82, 105, 137],
        ...,
        [ 80, 102, 136],
        [ 80, 103, 137],
        [ 79, 103, 137]],

       ...,

       [[188, 164, 138],
        [188, 165, 138],
        [186, 166, 137],
        ...,
        [ 71,  60,  57],
        [ 70,  61,  56],
        [ 68,  60,  57]],

       [[187, 165, 137],
        [187, 165, 136],
        [185, 165, 135],
        ...,
        [ 70,  60,  58],
        [ 70,  60,  58],
        [ 68,  58,  55]],

       [[187, 167, 138],
        [186, 166, 137],
        [184, 164, 134],
        ...,
        [ 68,  60,  56],
        [ 68,  59,  54],
        [ 68,  59,  54]]], shape=(405, 528, 3), dtype=uint8)

#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```
#### 14. Read the image ('Boy.jpg').
```python
img =cv2.imread('diptimage3.png',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```
#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```
#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```
#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```

#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
### *i)** Read and Display an Image.
  
 ###  1.Read 'diptimage.jpg' as grayscale and display:
 
  <img width="562" height="515" alt="Screenshot 2025-08-20 002029" src="https://github.com/user-attachments/assets/101c6f5c-311a-4f00-a7ce-2564a4767595" />
  
### 2.Save image as PNG and display:

<img width="639" height="544" alt="Screenshot 2025-08-20 002318" src="https://github.com/user-attachments/assets/27363ba9-7175-4060-b963-0d9655ecd78c" />

### 3.Cropped image

<img width="422" height="537" alt="Screenshot 2025-08-20 002526" src="https://github.com/user-attachments/assets/2b75b960-334a-41dc-b6a5-b2e1215a39ee" />

### 4.Resize and flip Horizontally:

<img width="487" height="495" alt="Screenshot 2025-08-20 002722" src="https://github.com/user-attachments/assets/fa22e53c-74e3-4dbe-a25c-dd0cd8390be7" />

### 5.Read 'diptimage2.jpg' and Display the final annotated image:

<img width="669" height="548" alt="Screenshot 2025-08-20 003759" src="https://github.com/user-attachments/assets/34d466ef-7a0f-4c55-9dcb-aadd1a27e1d6" />


### *ii)** Adjust Image Brightness.
- 
  ### 1.Create brighter and darker images and display:
  
  <img width="817" height="290" alt="Screenshot 2025-08-20 003942" src="https://github.com/user-attachments/assets/9b8da333-e36c-4823-9663-563131470420" />

  ### *iii)** Modify Image Contrast.
- 
  ### 1.Modify contrast using scaling factors 1.1 and 1.2
  
   <img width="823" height="297" alt="Screenshot 2025-08-20 004058" src="https://github.com/user-attachments/assets/7ee052d6-0653-4630-b225-6223d211a62a" />
    
  ### *iv)** Generate Third Image Using Bitwise Operations.
- 
### 1.Split 'Boy.jpg' into B, G, R components and display:

<img width="815" height="292" alt="Screenshot 2025-08-20 004215" src="https://github.com/user-attachments/assets/001bae3b-7de9-473c-9648-a1cbda8704c3" />

### 2.Merge the R, G, B channels and display:

<img width="506" height="527" alt="Screenshot 2025-08-20 004300" src="https://github.com/user-attachments/assets/4f763f28-dc89-4a8a-a1a4-3f0ba48faaa1" />

### 3.Split the image into H, S, V components and display:

<img width="820" height="294" alt="Screenshot 2025-08-20 004406" src="https://github.com/user-attachments/assets/61f39076-c47b-4681-9f8b-d055ea7585a0" />

### 4.Merge the H, S, V channels and display:

<img width="819" height="450" alt="Screenshot 2025-08-20 004523" src="https://github.com/user-attachments/assets/8d5d1de9-2941-4d35-a968-5826db84db00" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.


## Software Used
Anaconda - Python 3.7
## Algorithm
### Step 1:
<br>

### Step 2:
<br>

### Step 3:
<br>

### Step 4:
<br>

### Step 5:
<br>

## Program:
``` Python
### Developed By:
### Register No:

## i) Write the frame as JPG file




## ii) Display the video




## iii) Display the video by resizing the window




## iv) Rotate and display the video









```
## Output

### i) Write the frame as JPG image
</br>
</br>


### ii) Display the video
</br>
</br>


### iii) Display the video by resizing the window
</br>
</br>



### iv) Rotate and display the video
</br>
</br>





## Result:
Thus the image is accessed from webcamera and displayed using openCV.
