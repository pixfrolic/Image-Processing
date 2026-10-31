# Image Processing and Pattern Recognition (IPP) — Practical Files

**Course:** Image Processing and Pattern Recognition (IPP)  
**Programme:** PGDM — Big Data Analytics / AI & Data Science  
**Batch:** 2025–2027  
**Author:** Adarsh Yede  
**Roll Number:** 20251003  

---

## About the Project

This repository contains two practical files developed for the **Image Processing and Pattern Recognition (IPP)** course. The practicals demonstrate fundamental image processing techniques and advanced image analysis experiments using Python and popular computer vision libraries.

The repository includes Jupyter notebooks, implementation code, visual outputs, observations, and ready-to-submit reports.

The experiments cover image manipulation, edge detection, noise analysis, lossless compression, JPEG-style compression artifacts, texture segmentation, and leaf disease segmentation.

> **Reproducibility:** The reported numerical results correspond to the sample images, parameters, and implementations used in the experiments. Practical File 2 uses fixed random seeds to support reproducibility.

## Contents

| Practical File | Assignment | Description | Notebook |
|---|---|---|---|
| Practical File 1 | Assignment 2 | 10 image processing basics problems using OpenCV, Pillow, and Matplotlib, with code and explanations | `Practical_File_1_IPP.ipynb` |
| Practical File 2 | Assignment 3 | 6 experiments covering edge detection, noise sensitivity, compression, JPEG artifacts, texture segmentation, and disease segmentation | `Practical_File_2_IPP.ipynb` |

---

# Practical File 1 — Image Processing Basics

**Objective:** To understand and implement fundamental image processing operations using Python libraries.

### Experiments

| No. | Problem | Key Functions / Techniques |
|---:|---|---|
| 1 | Read and display an image in a window titled "Original Image" | `cv2.imread()`, `cv2.imshow()` |
| 2 | Display image height, width, channels, and data type | `img.shape`, `img.dtype` |
| 3 | Convert a colour image to grayscale and save it as `output_gray.jpg` | `cv2.cvtColor()`, `cv2.imwrite()` |
| 4 | Open and display a PNG image using Pillow | `PIL.Image.open()`, `Image.show()` |
| 5 | Resize an image to 50% of its original width and height | `cv2.resize()`, `INTER_AREA` |
| 6 | Crop the central 200 × 200 pixel region and display it using Matplotlib | NumPy slicing, `plt.imshow()` |
| 7 | Rotate an image 90 degrees clockwise | `cv2.rotate()` |
| 8 | Flip an image horizontally | `cv2.flip(img, 1)` |
| 9 | Convert an RGB image to HSV and display the H, S, and V channels separately | `cv2.cvtColor()`, `cv2.split()` |
| 10 | Calculate Mean Squared Error (MSE) between two grayscale images | NumPy, `float64` |

### Learning Outcomes

- Understand image loading, display, and storage.
- Identify image dimensions, colour channels, and data types.
- Perform grayscale conversion, resizing, cropping, rotation, and flipping.
- Understand RGB and HSV colour spaces.
- Calculate image similarity using Mean Squared Error.

**Notebook:** `notebooks/Practical_File_1_IPP.ipynb`

---

# Practical File 2 — Image Processing Experiments

**Objective:** To investigate image processing algorithms and evaluate their performance through quantitative metrics and visual analysis.

## Experiment 1: Comparative Edge Detection

**Methods:** Sobel, Laplacian, and Canny edge detection.

**Key observations:**
- Canny detected approximately 5.8% edge pixels in long segments, with a median segment length of 33 pixels.
- Sobel and Laplacian produced predominantly short edge fragments on the tested image.

**Learning outcome:** Understand the differences between gradient-based edge detection methods and the Canny edge detector.

## Experiment 2: Noise Sensitivity and Preprocessing

**Methods:** Gaussian noise, salt-and-pepper noise, Gaussian filtering, and median filtering.

**Key observations:**
- Laplacian's response to noise increased approximately 4.2 times, compared with 2.2 times for Sobel under the tested conditions.
- Median filtering improved Sobel's edge F-score from 0.536 to 0.966 under salt-and-pepper noise.

**Learning outcome:** Understand how noise affects edge detection and how preprocessing filters can improve image analysis.

## Experiment 3: Run-Length Encoding (RLE) vs. Huffman Coding

**Methods:** Custom implementations of RLE and Huffman coding, with decoding verification.

**Key observations:**
- For a synthetic poster with large, uniform regions, RLE achieved approximately 90.1% size reduction, compared with 73.6% for Huffman coding.
- For a raw noisy scan, RLE increased the encoded size by approximately 52%, while Huffman coding achieved approximately 6.4% size reduction.

**Learning outcome:** Compare lossless compression methods and understand how image characteristics influence compression efficiency.

## Experiment 4: JPEG-Style Compression Artifacts

**Methods:** 8 × 8 Discrete Cosine Transform (DCT) and quantisation at quality settings Q = 90, 50, and 10.

**Results:**

| Quality Setting | PSNR (dB) | SSIM |
|---:|---:|---:|
| 90 | 40.3 | 0.979 |
| 50 | 32.6 | 0.914 |
| 10 | 28.4 | 0.784 |

**Key observation:** Lower quality settings produced greater compression artifacts and reduced image similarity.

**Learning outcome:** Understand the relationship between quantisation strength, image quality, and compression artifacts.

## Experiment 5: GLCM-Based Texture Segmentation

**Methods:** Gray-Level Co-occurrence Matrix (GLCM) features and K-means clustering with three clusters.

**Key observation:**

| Feature Configuration | Adjusted Rand Index (ARI) |
|---|---:|
| Contrast feature alone | 0.574 |
| All three tested features | 0.328 |

**Learning outcome:** Explore texture feature extraction and unsupervised segmentation, including the effect of feature selection on clustering performance.

## Experiment 6: Leaf Disease Segmentation

**Methods:** Intensity, Sobel gradient, local variance, and K-means clustering.

**Key observations:**
- Combining all three features achieved the best reported Dice score of 0.571.
- Local variance was the strongest individual feature among those tested.
- The evaluation used an approximate lesion reference derived from a colour rule rather than hand-labelled ground truth.

**Learning outcome:** Understand feature-based segmentation and evaluate its performance using the Dice coefficient.

**Important limitation:** The Dice, precision, and recall values are indicative because the reference mask is approximate. They should not be interpreted as validated clinical or agricultural diagnostic performance.

**Notebook:** `notebooks/Practical_File_2_IPP.ipynb`

---

# Sample Visualisations

The repository includes visual outputs illustrating key experiments.

| Experiment | Visualisation |
|---|---|
| Edge Detection | Comparison of Sobel, Laplacian, and Canny |
| Noise Sensitivity | Noisy images, filtered images, and edge detection results |
| JPEG Compression | Low-, medium-, and high-quality compression comparisons |
| Texture Segmentation | GLCM feature-based image segmentation |
| Leaf Disease Segmentation | Segmentation using intensity, gradient, and local variance |

Figures used in the repository documentation are stored in the `docs/` directory.

---

# Repository Structure

```text
ipp-practical-files/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   ├── Practical_File_1_IPP.ipynb
│   ├── Practical_File_2_IPP.ipynb
│   ├── flower.jpg
│   ├── scene.jpg
│   ├── sunset.png
│   ├── car.jpg
│   ├── img1.jpg
│   ├── img2.jpg
│   ├── building.jpg
│   └── leaf_disease.jpg
│
├── reports/
│   ├── IPP_Practical_File_1_Kushagra_Mishra.docx
│   ├── IPP_Practical_File_2_Kushagra_Mishra.docx
│   ├── Practical_File_1_IPP.html
│   └── Practical_File_2_IPP.html
│
└── docs/
    └── Figures used in the README
```

**Note:** The report filenames above reflect the supplied repository structure. Rename the Word reports to the correct author name before submission if they are intended for your use.

---

# Installation and Setup

## Prerequisites

Install the following software:

- Python 3.10 or a compatible version supported by the selected library releases.
- Jupyter Notebook.
- Git (optional, for cloning the repository).

The project uses Python libraries for image processing, numerical computing, visualisation, and machine learning.

## Step 1: Clone the Repository

Replace `<your-username>` with your GitHub username.

```bash
git clone https://github.com/<your-username>/ipp-practical-files.git
cd ipp-practical-files
```

Alternatively, download the repository as a ZIP file and extract it.

## Step 2: Create a Virtual Environment

**Windows:**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

## Step 4: Launch Jupyter Notebook

Navigate to the notebooks directory:

```bash
cd notebooks
jupyter notebook
```

Open the required notebook in your browser.

## Step 5: Run the Experiments

1. Open `Practical_File_1_IPP.ipynb` or `Practical_File_2_IPP.ipynb`.
2. Confirm that the required image files are available in the `notebooks/` directory.
3. Select **Run → Run All Cells**.
4. Review the generated outputs, figures, and observations.

### Alternative Execution Environments

The notebooks can also be opened in:

- Visual Studio Code with the Jupyter extension.
- PyCharm with Jupyter Notebook support.
- Google Colab, provided that the notebooks and required image files are uploaded and the paths are configured correctly.

---

# Important Notes

### 1. Image Display in Jupyter

Practical File 1 begins with a setup cell that adapts `cv2.imshow()` and Pillow's `Image.show()` for inline display in Jupyter Notebook.

If you copy the practical code into a standard Python `.py` script, skip the notebook-specific setup cell and use the appropriate native image display functions.

### 2. Image File Paths

Run the notebooks from inside the `notebooks/` directory because the code loads images using relative filenames, such as:

```python
cv2.imread("flower.jpg")
```

If you run a notebook from another directory, update the image paths accordingly.

### 3. Replacing Sample Images

You can replace the supplied sample images with your own images, provided that you retain the expected filenames.

For Practical File 2, replacing images may change the numerical results. Re-run the experiments and update the reported observations whenever necessary.

### 4. Reproducibility

Practical File 2 sets random seeds to make stochastic operations reproducible under the same environment and parameters.

Differences in library versions, image inputs, or implementation details may still affect results.

### 5. Exporting Notebooks to PDF

The HTML reports can be opened in a browser and exported as PDFs.

1. Open the relevant HTML file from `reports/`.
2. Press `Ctrl + P` or select **Print** from the browser menu.
3. Choose **Save as PDF**.
4. Adjust the page layout and margins if required.
5. Save the exported practical file.

---

# Data and Image Sources

| Image / Dataset | Source |
|---|---|
| `flower.jpg`, `scene.jpg` | Sample images distributed with scikit-learn through `sklearn.datasets.load_sample_images` |
| `building.jpg` | Sample data from the OpenCV repository |
| `car.jpg` | Placeholder based on the building image because a separate car photograph was not supplied |
| `leaf_disease.jpg` | Potato early-blight leaf image from the PlantVillage dataset, associated with Hughes and Salathé (2015) |
| `sunset.png`, `img1.jpg`, `img2.jpg` | Generated programmatically, including a synthetic gradient and modified flower-image variants |
| Cameraman, scanned page, brick, grass, and gravel | Sample images distributed with scikit-image through `skimage.data` |
| Synthetic poster | Generated programmatically for the compression experiment |

**Image licensing:** Please verify the original source and applicable licence terms before redistributing any sample images. Attribute third-party datasets and image sources where required.

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming language |
| NumPy | Numerical operations and array manipulation |
| SciPy | Scientific computing |
| OpenCV | Image processing and computer vision |
| Pillow | Image loading and manipulation |
| Matplotlib | Image visualisation and plotting |
| scikit-image | Image processing algorithms and sample datasets |
| scikit-learn | Clustering and machine learning utilities |
| Jupyter Notebook | Interactive development and documentation |

---

# Limitations

- **Edge detection:** Results depend on image content, threshold values, and algorithm parameters.
- **Noise analysis:** Noise sensitivity varies with noise type, intensity, and preprocessing settings.
- **Compression:** Compression performance depends on image complexity and the characteristics of the input.
- **Texture segmentation:** The observed clustering performance depends on the selected GLCM features and K-means configuration.
- **Leaf disease segmentation:** No hand-labelled ground truth is available. An approximate colour-based lesion reference is used for evaluation.
- **Sample images:** The reported numerical results are specific to the selected images and experimental parameters.

These experiments are intended for academic learning and demonstration. The leaf segmentation experiment is not a validated disease diagnosis system.

---

# Learning Outcomes

By completing these practicals, students gain hands-on experience with:

- Fundamental image processing operations.
- Colour spaces and image transformations.
- Edge detection and noise reduction.
- Lossless image compression algorithms.
- JPEG-style transform-based compression.
- Texture feature extraction and image segmentation.
- K-means clustering for image analysis.
- Quantitative evaluation using MSE, PSNR, SSIM, ARI, and Dice scores.
- Reproducible experimentation using Python and Jupyter Notebook.

---

# Academic Information

**Course:** Image Processing and Pattern Recognition (IPP)  
**Programme:** PGDM — Big Data Analytics / AI & Data Science  
**Batch:** 2025–2027  
**Student:** Adarsh Yede  
**Roll Number:** 20251003  

**Purpose:** Academic practical work and demonstration of image processing concepts.

---

## Acknowledgements

This project uses open-source Python libraries and sample images distributed through established computer vision and scientific computing packages. Thanks to the developers and maintainers of OpenCV, Pillow, NumPy, SciPy, Matplotlib, scikit-image, and scikit-learn.

---

**If you find this repository useful for learning image processing, consider starring the repository on GitHub.**
