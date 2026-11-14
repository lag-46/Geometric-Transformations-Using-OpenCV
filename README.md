# 04: Image Transformations Using OpenCV
# NAME : PANDEESWARAN N
# REG.NO : 212224230191

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image, such as translation, scaling, shearing, reflection, rotation, and cropping.

## Software Used

- Python
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm

### Step 1: Import Libraries
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2: Load the Image
Read the input image using `cv2.imread()` and display the original image.

### Step 3: Image Translation
- Create a translation matrix.
- Shift the image horizontally and vertically.
- Apply the transformation using `cv2.warpAffine()`.
- Display the translated image.

### Step 4: Image Scaling
- Define scaling factors for width and height.
- Resize the image using `cv2.resize()`.
- Apply bilinear interpolation using `cv2.INTER_LINEAR`.
- Display the scaled image.

### Step 5: Image Shearing
- Create a shearing transformation matrix.
- Apply horizontal and vertical shearing.
- Use `cv2.warpAffine()` to perform the transformation.
- Display the sheared image.

### Step 6: Image Reflection
- Perform image reflection using `cv2.flip()`.
- Apply flipping along both axes.
- Display the reflected image.

### Step 7: Image Rotation
- Calculate the center of the image.
- Create a rotation matrix using `cv2.getRotationMatrix2D()`.
- Rotate the image by 45 degrees.
- Apply the transformation using `cv2.warpAffine()`.
- Display the rotated image.

### Step 8: Image Cropping
- Specify the starting coordinates.
- Define the required width and height.
- Extract the required portion using NumPy array slicing.
- Display the cropped image.



## Program

**Developed By:** PANDEESWARAN N

**Register Number:** 212224230191

**Program File:** `Ex.4.ipynb`

### Step 1: Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2: Load the Image

```python
# Step 1: Load the image
image = cv2.imread('my.jpeg')  # Load the image from file
```

### Step 3: Display the Original Image

```python
# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Original Image")  
plt.axis('off') 
```

### Step 4: Image Translation

```python
# Step 2: Image Translation
tx, ty = 100, 50  # Translation factors (shift by 100 pixels horizontally and 50 vertically)
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  # Translation matrix: 
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))  
```

```python
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')
```

### Step 5: Image Scaling

```python
# Step 3: Image Scaling
fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing
```

```python
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')
```

### Step 6: Image Shearing

```python
# Step 4: Image Shearing
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))
```

```python
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')
```

### Step 7: Image Reflection

```python
# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes
```

```python
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')
```

### Step 8: Image Rotation

```python
# Step 6: Image Rotation
(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation
```

```python
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')
```

### Step 9: Image Cropping

```python
# Step 7: Image Cropping
x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions
```

```python
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
```


## Output

### 1. Original image 

- Original image is displayed.

<img width="398" height="408" alt="image" src="https://github.com/user-attachments/assets/eba41f20-c068-4b0f-8f35-4e43400ad5fa" />


### 2. Image Translation

- Translated image is displayed after shifting.

<img width="350" height="420" alt="image" src="https://github.com/user-attachments/assets/7582611d-f827-4479-be1a-793e2d435780" />


### 3. Image Scaling

- Scaled image is displayed with the specified scaling factors.

<img width="582" height="311" alt="image" src="https://github.com/user-attachments/assets/f5526d9f-7a10-4c24-8922-392272c44ea5" />


### 4. Image Shearing

- Horizontally and vertically sheared images are displayed.

<img width="355" height="412" alt="image" src="https://github.com/user-attachments/assets/b0653a04-e4aa-4f39-b84c-0c84cdb08ebb" />


### 5. Image Reflection

- Reflected image is displayed after flipping along both axes.

<img width="387" height="427" alt="image" src="https://github.com/user-attachments/assets/8404e0a3-b099-4123-8775-6797d68d2e41" />


### 6. Image Rotation

- Rotated image is displayed at an angle of 45 degrees.

<img width="352" height="403" alt="image" src="https://github.com/user-attachments/assets/fa4c2825-fe0c-4851-81ae-18bff972aed1" />


### 7. Image Cropping
- Cropped portion of the image is displayed.

<img width="443" height="417" alt="image" src="https://github.com/user-attachments/assets/3a7c0170-643a-4c64-ac8d-23d82b4a5a4a" />


## Result

Thus, various geometric transformations such as image translation, scaling, shearing, reflection, rotation, and cropping were successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
