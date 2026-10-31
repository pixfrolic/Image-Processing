IPP Practical Files: Image Processing and Pattern Recognition
Python Jupyter OpenCV scikit-image
Two practical files for the Image Processing and Pattern Recognition (IPP) course, PGDM (Big Data Analytics / AI & Data Science), Batch 2025-27.


Author
Adarsh Yede
Roll No.
20251003
Every program in this repository was run, and the outputs, figures and numbers in the notebooks and reports are the real results of that run.
Contents


Practical
Assignment
Focus
Format
Practical File 1
Assignment 2
10 image-basics problems (OpenCV, Pillow, Matplotlib), each with code and explanation
Practical_File_1_IPP.ipynb
Practical File 2
Assignment 3
6 experiments: edge detection, noise, compression, JPEG, texture and disease segmentation, with code only plus short observations
Practical_File_2_IPP.ipynb
Practical File 1: Image basics


#
Task
Key functions
1
Read and display an image in a window titled "Original Image"
cv2.imread, cv2.imshow
2
Print height, width, channels and data type
img.shape, img.dtype
3
Colour to grayscale, save as output_gray.jpg
cv2.cvtColor, cv2.imwrite
4
Open and display a PNG with Pillow
PIL.Image.open, show
5
Resize to 50% of width and height
cv2.resize (INTER_AREA)
6
Crop the central 200x200 area, show with Matplotlib
NumPy slicing, plt.imshow
7
Rotate 90 degrees clockwise
cv2.rotate
8
Flip left-to-right
cv2.flip(img, 1)
9
RGB to HSV, display H, S and V separately
cv2.cvtColor, cv2.split
10
Mean Squared Error between two grayscale images
NumPy (float64)
Practical File 2: Experiments


#
Problem
Method
Headline result
1
Comparative edge detection
Sobel, Laplacian, Canny
Canny: 5.8% edge pixels in long segments (median 33 px). Sobel and Laplacian: mostly tiny fragments
2
Noise sensitivity
Gaussian and salt-and-pepper noise; Gaussian and median pre-filters
Laplacian is hit hardest (response up 4.2x vs 2.2x for Sobel). A median filter lifts Sobel's edge F-score under salt-and-pepper noise from 0.536 to 0.966
3
RLE vs Huffman
Own lossless implementations, decoding verified
Flat poster: RLE 90.1% vs Huffman 73.6% reduction. Raw noisy scan: RLE expands by 52%, Huffman saves 6.4%
4
JPEG block artifacts
8x8 DCT + quantisation at Q=90 / 50 / 10
PSNR 40.3 / 32.6 / 28.4 dB, SSIM 0.979 / 0.914 / 0.784
5
GLCM texture segmentation
Per-pixel GLCM features + K-means (k=3)
Contrast alone beats all three features together (ARI 0.574 vs 0.328)
6
Leaf disease segmentation
Intensity + Sobel gradient + local variance, K-means
Best with all three features (Dice 0.571); variance is the strongest single feature
Sample figures
Problem 1: Sobel vs Laplacian vs Canny Edge detection comparison
Problem 2: Noise sensitivity and preprocessing Noise sensitivity
Problem 4: JPEG-style block artifacts (low, medium, high quantisation) JPEG artifacts
Problem 5: GLCM texture segmentation GLCM segmentation
Problem 6: Multi-feature leaf disease segmentation Leaf disease segmentation
Repository structure
ipp-practical-files/
├── README.md
├── requirements.txt
├── notebooks/                     # run these (images must stay in this folder)
│   ├── Practical_File_1_IPP.ipynb
│   ├── Practical_File_2_IPP.ipynb
│   └── flower.jpg, scene.jpg, sunset.png, car.jpg, img1.jpg, img2.jpg,
│       building.jpg, leaf_disease.jpg
├── reports/                       # ready-to-submit versions
│   ├── IPP_Practical_File_1_Kushagra_Mishra.docx
│   ├── IPP_Practical_File_2_Kushagra_Mishra.docx
│   └── Practical_File_1_IPP.html, Practical_File_2_IPP.html
└── docs/                          # figures used in this README
How to run
git clone https://github.com/<your-username>/ipp-practical-files.git
cd ipp-practical-files

python -m venv .venv
.venv\Scripts\activate            # Windows   (macOS/Linux: source .venv/bin/activate)
pip install -r requirements.txt

cd notebooks
jupyter notebook                  # open a notebook, then Run > Run All Cells
You can also open the .ipynb files directly in PyCharm or VS Code, or upload a notebook and its images to Google Colab.
Notes
Practical File 1 begins with a Setup cell that makes cv2.imshow() and Image.show() display inline in Jupyter. If you copy the code into a normal .py script, skip that cell; the code for the problems itself is unchanged.
Run the notebooks from inside notebooks/, because the code reads images by file name ("flower.jpg", "building.jpg", ...).
To use your own pictures, replace a file with one of the same name and re-run. Re-check the observations in Practical File 2, as they quote numbers from the sample images.
Practical File 2 sets random seeds, so re-running reproduces the reported numbers.
To save a notebook as a PDF, open the matching .html from reports/ in a browser and use Print > Save as PDF.
Data and image sources


File(s)
Source
flower.jpg, scene.jpg
Sample images shipped with scikit-learn (sklearn.datasets.load_sample_images)
building.jpg (also used as the car.jpg stand-in)
Sample data from the OpenCV repository
leaf_disease.jpg
Potato early-blight leaf from the PlantVillage dataset (Hughes & Salathe, 2015)
sunset.png, img1.jpg, img2.jpg
Generated by code (synthetic gradient; grayscale copy of the flower image and a blurred, noisy version of it)
Cameraman, scanned page, brick, grass, gravel
Bundled with scikit-image (skimage.data), loaded in the code
Synthetic poster (Problem 3)
Generated in the code
car.jpg is a placeholder because no car photo was supplied; replace it with your own. Please check the original sources for the licence terms of each image before reusing them.
Tech stack
Python, NumPy, SciPy, OpenCV, Pillow, Matplotlib, scikit-image, scikit-learn, Jupyter.
Limitations
Problem 6 has no hand-labelled ground truth. It uses a simple colour rule as an approximate lesion reference, so the reported Dice, precision and recall are indicative, not exact.
Problem 3 uses a synthetic poster for the "large flat regions" case, shown alongside a real scanned page (cleaned and raw).
Results depend on the sample images and parameters chosen; different images will give different numbers.
