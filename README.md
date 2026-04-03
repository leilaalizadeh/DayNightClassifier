# Day-Night Image Classifier (99.37% Accuracy)

This repository contains a high-performance image classification system that distinguishes between **Day** and **Night** images using **pure Image Processing** techniques. By leveraging OpenCV and color space analysis, this project achieves **99.37% accuracy** without the use of any Machine Learning algorithms.

## 🚀 The Challenge
Standard brightness analysis (averaging pixel values) often fails when night images contain bright street lights or day images are overcast. To achieve 99% accuracy, this implementation uses a multi-feature approach to evaluate both intensity and specific color distributions.

## 🛠️ How it Works
The classifier uses a two-stage feature extraction process:

1.  **Average Brightness (V-Channel):**
    * The image is converted from RGB to **HSV** color space.
    * The **Value (V)** channel is isolated to calculate the average brightness across the entire image.
2.  **Hue Filtering (Blue/Green Masks):**
    * Daytime sky and environments often contain specific blue/green hues that are absent or significantly different in night photography.
    * A custom mask (`cv2.inRange`) is applied to detect the percentage of these specific color ranges (Hue 87-118).
3.  **Dual-Threshold Logic:**
    * The final classification is determined by a refined logic:
        * **Brightness Threshold:** `94.67`
        * **Color Percentage Threshold:** `0.7`
    * If both conditions are met, the image is classified as **Day (1)**; otherwise, it is **Night (0)**.

## 📊 Performance
* **Methodology:** Zero Machine Learning (Heuristic-based Computer Vision).
* **Accuracy:** **99.375%** (based on 1 misclassified image out of 160 in the test set).
* **Frameworks:** OpenCV, NumPy, Matplotlib.

## 📁 Project Structure
* `load_dataset()`: Imports and labels the raw image data from directory structures.
* `standardize()`: Resizes images to a uniform 600x1100 resolution for consistent analysis.
* `avg_brightness()`: Extracts the V-channel average from the HSV color space.
* `colors_green_blue()`: Calculates the presence of specific sky/outdoor color tones.
* `estimate_label()`: The core classifier function that predicts the class based on the tuned thresholds.

## 💻 Usage
1. Update the `image_dir_training` and `image_dir_test` paths in the notebook to point to your dataset.
2. Run the cells to process the images, extract features, and view the final accuracy report.




