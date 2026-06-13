# Centroid Image Clustering

*Unsupervised color quantization and image compression using K-Means clustering from scratch.*

![Build](https://img.shields.io/badge/build-passing-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![Python](https://img.shields.io/badge/python-3.8+-blue)
![Jupyter](https://img.shields.io/badge/jupyter-notebook-orange)

K-Means Image Compressor is a Python-based machine learning pipeline that applies unsupervised clustering to pixel color spaces. By grouping millions of colors into $K$ representative centroids, it performs lossy image compression (vector quantization), reducing the storage footprint while preserving essential visual structures.

---

## 📑 Table of Contents

- [Centroid Image Clustering](#centroid-image-clustering)
  - [Table of Contents](#-table-of-contents)
  - [Features](#-features)
  - [Technology Stack](#-technology-stack)
  - [Demo and Preview](#-demo-and-preview)
  - [Installation](#-installation)
  - [Usage](#-usage)
  - [Configuration](#-configuration)
  - [Testing](#-testing)
  - [License](#-license)
  - [FAQs](#-faqs)
  - [Contact](#-contact)

---

## 🚀 Features

* **K-Means from Scratch**: Pure NumPy implementation of centroid assignment, mean computation, and random initialization.
* **2D Clustering Visualization**: Step-by-step progress plots showing centroid path trajectories and cluster adjustments.
* **Vector Quantization / Compression**: Reconstructs 24-bit RGB images (like `bird_small.png`) using only $K$ clustered centroid colors (e.g., 16 colors/4-bit depth).
* **3D Color Space Rendering**: Generates interactive 3D scatter plots of pixel distributions and their computed centroids in the RGB space.
* **Side-by-Side Comparison**: Renders original and reconstructed images side-by-side to visualize compression efficiency and quality preservation.

---

## 🛠 Technology Stack

* **Language**: Python 3.8+
* **Libraries**:
  * **NumPy**: Matrix operations, Euclidean distance calculations, and dataset reshaping.
  * **Matplotlib**: 2D scatter plots, 3D projections, image rendering, and centroid path drawing.
  * **SciPy**: Ingestion of MATLAB data files (`.mat`) using `scipy.io`.
  * **Jupyter**: Interactive execution environment.

---

## 📊 Demo and Preview

### 1. 2D Clustering Progress
During execution, K-Means plots the movement of centroids at each iteration:

*Visualization showing the black "x" markers (centroids) converging onto the centers of red, green, and blue data point clusters, with black lines illustrating their historical paths.*

### 2. Side-by-Side Image Compression
Compressing `bird_small.png` from a full RGB color space to just 16 colors:

*Left: Original image (128x128 pixels, 24-bit color).*
*Right: Compressed image using K-Means with $K=16$ (only 16 unique colors).*

### 3. 3D Color Centroids Visualization
A 3D visualization of pixel coordinates in R, G, B dimensions along with their corresponding cluster centroids:

*3D scatter plot showcasing the pixel colors in their RGB coordinate space, marked with red "x" symbols at the coordinates of the 16 calculated color centroids.*

---

## 📥 Installation

Follow these steps to set up the project locally:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/jayshah-92/centroid-image-clustering.git
   cd centroid-image-clustering
   ```

2. **Set up a virtual environment** (recommended):
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install the dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   *(If a `requirements.txt` is not available, install them directly)*:
   ```bash
   pip install numpy matplotlib scipy notebook
   ```

4. **Launch the Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

---

## 💻 Usage

1. Open `image_clustering.ipynb` in the Jupyter interface.
2. Run the code cells sequentially from top to bottom.
3. To compress custom images:
   * Place your target image in the root directory.
   * Modify the loading code block inside the notebook to point to your image path:
     ```python
     # Load your own image
     original_img = plt.imread('your_image.png')
     ```
   * Run the K-Means compressor block to compute centroids and render the compressed version.

---

## ⚙️ Configuration

All adjustable parameters and configurations are defined inside the notebook cells:

* **Number of Clusters (`K`)**: Defines the target color palette size.
  ```python
  K = 16  # For 16-color compression
  ```
* **Iterations (`max_iters`)**: Number of times the algorithm runs centroid update loops.
  ```python
  max_iters = 10
  ```
* **Input Dataset**:
  * `data/ex7data2.mat`: 2D spatial dataset for testing K-Means logic.
  * `bird_small.png`: 128x128 RGB test image for color quantization.

---

## 🧪 Testing

To verify the custom K-Means mathematical implementations, you can run the built-in unit tests. The unit tests verify centroid updates and closest centroid lookups:

```python
# Run test cells inside image_clustering.ipynb
from public_tests import *

find_closest_centroids_test(find_closest_centroids)
compute_centroids_test(compute_centroids)
```

**Expected Output**:
```text
All tests passed!
All tests passed!
```

---


## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## ❓ FAQs

**Q: How does K-Means achieve image compression?**
**A**: Instead of storing the full RGB values (24 bits) for every single pixel, we only store the index of the closest centroid color (4 bits for 16 colors) and a small color palette map of 16 RGB values. This represents a significant reduction in the amount of data needed to render the image.

**Q: Why do we use random initialization for centroids?**
**A**: K-Means is prone to converging to local optima depending on the starting location of the centroids. Randomly shuffling dataset points to initialize centroids ensures that running the algorithm multiple times will explore different cluster layouts.

**Q: The compression takes too long for large images. How can I optimize it?**
**A**: Since K-Means calculates distance between every pixel and every centroid, the execution time scales with the number of pixels. Downscale high-resolution images or implement vectorized calculations using mini-batch gradient descents for large inputs.

---

## ✉️ Contact

* **Developer**: Jay Shah
* **GitHub**: [@jayshah-92](https://github.com/jayshah-92)
* **Project Link**: [centroid-image-clustering](https://github.com/jayshah-92/centroid-image-clustering)
