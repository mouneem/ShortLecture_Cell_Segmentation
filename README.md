# Short Lecture: Introduction to Cell Segmentation with Python

This repository contains a series of Python notebooks for a short lecture on cell segmentation. The notebooks guide the user from the fundamentals of digital images, through "old-school" classical computer vision techniques (like thresholding and watershed), and finally to modern, deep-learning-based methods (Cellpose and StarDist).

The final notebook demonstrates a complete analysis pipeline: segmenting a real-world histology image and extracting quantitative, single-cell data for downstream analysis.

## Notebooks

The lecture is broken down into four key notebooks, designed to be run in order:

### 1. `1.Creating_an_Image.ipynb`
* **Concept:** What is a digital image?
* **Covers:** The fundamentals of how images are represented as matrices (pixels). It explores color channels (RGB vs. grayscale), bit-depth (8-bit vs. 16-bit), and introduces color deconvolution (`rgb2hed`) for separating stains in histology images.

### 2. `2.Segmentation_Thresholding.ipynb`
* **Concept:** The simplest segmentation method and its main problem.
* **Covers:** An interactive `ipywidgets` slider to demonstrate basic intensity thresholding on a `cells3d` nuclei image. This notebook clearly highlights the primary failure of this method: **merged, touching objects**.

### 3. `3.Segmentation_Watershed.ipynb`
* **Concept:** The "classic" solution for splitting merged objects.
* **Covers:** An interactive notebook that implements the full marker-controlled watershed pipeline (Threshold -> Distance Transform -> Find Peaks -> Watershed). It shows how this successfully separates the touching nuclei from the previous notebook.

### 4. `4.Advanced_Cellpose_and_Stardist.ipynb`
* **Concept:** Modern, deep-learning-based solutions and their applications.
* **Covers:** This is the capstone notebook, divided into three parts:
    1.  **Modern Solutions (on `cells3d`):** Introduces **Cellpose** and **StarDist** with interactive sliders to adjust their parameters (`diameter`, `flow_threshold`, `prob_thresh`, `nms_thresh`). This provides a direct comparison to the "classic" methods from notebooks 2 & 3 on the *same data*.
    2.  **Real-World Application (on `immunohistochemistry`):** Shows how to apply StarDist's pre-trained `'2D_versatile_he'` model to a complex H&E (hematoxylin and eosin) stained image, achieving robust segmentation where classic methods fail.
    3.  **Downstream Analysis:** The key "so what?" section. It uses the segmentation mask as a "cookie cutter" to extract quantitative data (`area`, `shape`, `intensity`) for every single cell, converts it to a **pandas DataFrame**, and generates publication-ready plots (histograms, spatial scatter plots).

---

## Setup & Installation

To run these notebooks, you'll need a Python environment with several scientific and deep-learning packages.

1.  **Create a virtual environment** (optional, but highly recommended):
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

2.  **Install the required packages:**
    ```bash
    pip install jupyterlab matplotlib ipywidgets
    pip install scikit-image scipy scikit-learn
    pip install pandas seaborn
    pip install cellpose
    pip install stardist
    pip install "numpy<2.0"  # StarDist/Numba has issues with NumPy >= 2.0
    ```
    **Note:** Cellpose and StarDist may require PyTorch or TensorFlow. Please follow their official installation guides if you encounter issues.

---

## How to Run

1.  Clone this repository:
    ```bash
    git clone [https://github.com/mouneem/ShortLecture_Cell_Segmentation.git](https://github.com/mouneem/ShortLecture_Cell_Segmentation.git)
    cd ShortLecture_Cell_Segmentation
    ```

2.  Activate your virtual environment (if you made one):
    ```bash
    source venv/bin/activate
    ```

3.  Launch Jupyter Lab:
    ```bash
    jupyter lab
    ```

4.  Open `1.Creating_an_Image.ipynb` to start the lecture.

---

## Credits

This lecture and its associated notebooks were created by ESSABBAR AbdelMounm **@mouneem**.