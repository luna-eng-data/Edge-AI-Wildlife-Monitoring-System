# Eco-Sentinel: Edge AI Wildlife Monitoring System

**Project: Green AI & Computer Vision (DIA6)**

## Project Overview
Wildlife monitoring in remote areas relies on satellite-connected camera traps. Traditional systems transmit every single image to the cloud, which results in high energy consumption, high financial costs, and data overload for rangers.

This project, **Eco-Sentinel**, is a lightweight deep learning classification system designed for Edge Computing. By filtering images locally on the camera using **MobileNetV2**, the system only transmits critical alerts (human presence), significantly reducing the carbon footprint of wildlife surveillance.

## 1. Context and Problem
### The Human-Wildlife Conflict
As human populations expand into wildlife habitats, conflicts increase. Early warning systems are essential for conservation and safety.

### The Green AI Challenge
Current monitoring solutions are not sustainable:
*   **Energy Waste:** Transmitting high-resolution images via satellite drains batteries quickly.
*   **Carbon Footprint:** Data transmission and cloud storage contribute to digital pollution.
*   **Latency:** Rangers waste time analyzing empty images or non-threatening animals.

## 2. Methodology

### Model Architecture: MobileNetV2
We chose **MobileNetV2** instead of heavier object detection models (like YOLO) to prioritize energy efficiency.
*   **Transfer Learning:** We used weights pre-trained on ImageNet and froze the base layers to minimize training energy (Non-trainable params: ~2.2M).
*   **Lightweight:** The final model size is small (<10MB), making it suitable for deployment on small devices like Raspberry Pi.

### Training Strategy
To ensure the model is robust against real-world conditions (bad lighting, hidden animals), we applied specific **Data Augmentation** techniques:
*   Random rotations (10%)
*   Contrast and brightness adjustments
*   Horizontal flips

### Dataset
The dataset was aggregated from Kaggle sources to create a binary classification task:
*   **Class 0 (Animals):** Images of Buffalo, Elephant, Rhino, and Zebra.
*   **Class 1 (Humans):** Images of persons in outdoor environments.
All images were resized to 224x224 pixels.

## 3. Results

The model was evaluated on a test set of images it had never seen before.

### Technical Performance
*   **Global Accuracy:** 99%
*   **Recall on Humans:** 96%
    *   This is the most important metric for security. It means the system successfully detects 96 out of 100 intruders.
*   **Precision on Humans:** 99%
    *   This means false alarms are extremely rare.

### Environmental Impact Simulation
We ran a simulation to compare our "Edge AI" system against a traditional "Send-All" system.
*   **Bandwidth Reduction:** ~74%
    *   Instead of sending all images, the system only sent the images containing humans.
*   **Impact:** This massive reduction leads to lower satellite costs and a smaller digital carbon footprint.

## 4. Repository Structure
*   `notebooks/`: Contains the Jupyter notebook for training and evaluation.
*   `src/`: Source code for data processing.
*   `requirements.txt`: List of Python dependencies.

## 5. Scientific References
This project is based on the following research papers:

1.  **Sandler, M., et al. (2018).** *MobileNetV2: Inverted Residuals and Linear Bottlenecks.* CVPR.
    *   Validates the choice of a lightweight architecture for mobile devices.
2.  **Norouzzadeh, M. S., et al. (2018).** *Automatically identifying, counting, and describing wild animals in camera-trap images with deep learning.* PNAS.
    *   Validates the need for automated filtering in wildlife conservation.

---
*Project developed for the DIA6 Green AI Module - December 2025.*
