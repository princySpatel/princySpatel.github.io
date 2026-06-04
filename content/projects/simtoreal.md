---
title: "Sim-to-Real: Synthetic Data Pipeline for CV"
description: "An automated pipeline using a custom Blender Python add-on to generate synthetic 3D data for training YOLO object detection models."
timestamp: 2026-06-04
tags: ["Python", "Computer Vision", "Machine Learning", "PyTorch", "Blender"]
---

*Status: In Active Development & Optimization*

![YOLO Synthetic Detection Output](/images/simtoreal3.jpg)
![YOLO Synthetic Detection Output](/images/simtoreal2.png)
![YOLO Synthetic Detection Output](/images/simtoreal1.png)
*Testing the YOLO model on physical objects after training it exclusively on synthetically generated 3D data.*

## Overview
This project tackles the "sim-to-real domain gap" by engineering a completely automated, synthetic data generation pipeline to train Computer Vision models. To eliminate the bottleneck of manual data labeling, I developed a custom **Python add-on within Blender**. 

This engine procedurally generates training datasets by dynamically randomizing 3D object rotation, camera geometry, and environmental lighting. By synthesizing variance algorithmically, the system produces robust training data designed to train a **YOLO** object detection model to recognize physical, real-world items using strictly simulated environments.

## Technical Architecture
The core of the pipeline relies on custom mathematical scripting rather than standard export tools. To handle the computational load, I configured a localized **PyTorch** environment utilizing **CUDA** to accelerate the training loop directly on an RTX GPU.

* **Custom 3D-to-2D Projection:** Programmed a mathematical algorithm to translate spatial mesh data into precise 2D bounding box coordinates, automatically exporting strictly formatted annotation files for YOLO integration.
* **Procedural Variance:** The Blender script randomizes environments to ensure the model learns the object's core features rather than memorizing a single lighting setup or angle.

## Engineering Challenges Solved
A major focus of this ongoing project has been establishing strict data integrity and debugging complex environmental anomalies:

* **The Bounding Box Geometry Bug:** Early iterations suffered from bounding box expansion due to camera clipping through objects. I resolved this by mathematically recentering the 3D mesh origins and coding a safeguard to intercept and drop corrupted frames before they could poison the dataset.
* **Pipeline Data Leakage:** Debugged a complex model regression issue where YOLO was secretly re-training on poisoned data due to hidden `.cache` files. Purging the environment ensured mathematical accuracy.
* **Bridging the Domain Gap:** The current model successfully detects physical objects on unstructured real-world surfaces (like a messy wooden desk) using raw phone photography. 

*My ongoing work is focused on further optimizing this sim-to-real accuracy and refining the algorithmic variance in the Blender engine.*