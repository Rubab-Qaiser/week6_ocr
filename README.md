# week6_ocr
##  Image Processing & Digit Recognition Pipeline — Summary

This notebook demonstrates a complete pipeline combining **classical image processing** (using OpenCV and NumPy) with **deep learning** (a CNN trained on the MNIST).

---

##  1. Perspective Transformation (Document Rectification)

* Implemented using:

  * `order_points()`
  * `four_point_transform()`

###  Key Idea:

* Detects 4 corner points of a skewed object (e.g., document)
* Reorders them into a consistent format:

  ```
  [top-left, top-right, bottom-right, bottom-left]
  ```
* Applies a **perspective transform** to convert the tilted view into a **straight rectangular (bird’s-eye) view**

###  Outcome:

* Converts angled images into clean, aligned documents
* Forms the **first step of a document scanner system**

---

##  2. Image Deskewing (Rotation Correction)

* Implemented using:

  * `deskew(image)`

###  Key Idea:

* Converts image → grayscale → binary
* Extracts coordinates of foreground pixels
* Uses `minAreaRect` to estimate rotation angle
* Rotates image to correct tilt

###  Outcome:

* Automatically straightens rotated images
* Improves readability and preprocessing for OCR/ML models

---

##  3. Morphological Image Processing

* Operations applied:

  * **Erosion**
  * **Dilation**
  * **Opening**
  * **Closing**

###  Key Idea:

Using a kernel (3×3 matrix) to refine image structure:

| Operation | Purpose                               |
| --------- | ------------------------------------- |
| Erosion   | Removes small noise (shrinks objects) |
| Dilation  | Expands objects, fills gaps           |
| Opening   | Removes small white noise             |
| Closing   | Fills small holes                     |

###  Outcome:

* Cleans noisy images
* Enhances feature quality before feeding into models

---

##  4. Visualization

* Used Matplotlib to:

  * Display original and processed images
  * Compare effects of different operations side-by-side

---

##  5. CNN Model for Digit Recognition (MNIST)

* Trained a **Convolutional Neural Network (CNN)** on the MNIST

###  Key Idea:

* Input: 28×28 grayscale digit images
* CNN learns:

  * Edges → shapes → digit patterns
* Outputs predicted digit (0–9)

###  Outcome:

* Accurate handwritten digit classification
* Demonstrates integration of **image preprocessing + deep learning**

---

##  Overall System Understanding

This project combines:

1. **Geometric correction**

   * Perspective transform
   * Deskewing

2. **Image enhancement**

   * Morphological operations

3. **Intelligent recognition**

   * CNN (MNIST classifier)

---

##  Big Picture



```
Raw Image
   ↓
Perspective Fix
   ↓
Deskewing
   ↓
Noise Removal
   ↓
CNN Classification
   ↓
Final Output
```

---

##  Applications

* Document scanners (CamScanner-like apps)
* OCR preprocessing systems
* Automated form digit recognition
* Bank cheque / handwritten digit detection

---

