---
title: "Sim-to-Real: Synthetic Data Pipeline for CV"
description: "An automated Blender pipeline that generates synthetic 3D training data for YOLO object detection — and a deep dive into diagnosing why synthetic-only accuracy doesn't transfer to the real world."
timestamp: 2026-06-04
tags: ["Python", "Computer Vision", "Machine Learning", "PyTorch", "Blender"]
githubUrl: "https://github.com/princySpatel/sim_to_real_blender"
---

*Status: Core sim-to-real gap closed — real-world accuracy went from 0 detections to 0.84 mAP50, using zero real training photos.*

![YOLO Synthetic Detection Output](/images/simtoreal3.jpg)
![YOLO Synthetic Detection Output](/images/simtoreal2.png)
![YOLO Synthetic Detection Output](/images/simtoreal1.png)

*Testing the YOLO model on physical objects after training it exclusively on synthetically generated 3D data.*

## Overview

This project tackles the "sim-to-real domain gap" with a completely automated synthetic data generation pipeline for training Computer Vision models. To eliminate manual data labeling, I built a custom **Python add-on within Blender** that procedurally renders training images while auto-generating YOLO-format bounding box labels — randomizing 3D object rotation, camera geometry, materials, and lighting on every frame.

The interesting part wasn't building the pipeline — it was discovering that a model scoring **0.986 mAP50** on synthetic validation data produced **zero detections** on real photos, and then systematically figuring out why.

## Technical Architecture

The pipeline uses custom mathematical scripting (not standard export tools) to project 3D mesh data into 2D bounding boxes. Training runs on a localized **PyTorch + CUDA** environment on an RTX GPU using **Ultralytics YOLOv8**.

## Diagnosing the Sim-to-Real Gap

* **Checkpoint archaeology.** With multiple past training runs on hand, I ran every checkpoint against the same real photos and compared results. This isolated YOLO's `scale` augmentation as a bigger factor in real-world transfer than epoch count or model size — but it only got the model to be *selectively* correct, not reliably so.
* **The co-occurrence bug.** Reading back through the Blender generation script surfaced the real root cause: the two target objects were never rendered together in the same frame. The model had literally never learned to tell them apart in a shared scene — exactly the situation every real test photo put it in. Fixed by rewriting the generator to render both objects together roughly a third of the time, with guaranteed non-overlapping placement and camera framing that adapts to keep both in frame.
* **Material and lighting were too narrow.** Reflective objects (metal scissors) transferred far worse than matte ones (a plastic highlighter) — added roughness/metallic randomization and a softer multi-light setup to close that gap.
* **Background diversity was the single biggest lever.** The synthetic backgrounds were almost entirely one wood texture. Adding real photographed backgrounds *and* a procedurally generated background mode (solid colors, gradients, noise — generated directly in Blender, no stock images needed) closed most of the remaining gap.

## Results

Measured with a proper `mAP50` evaluation on real photos (not just eyeballing predictions):

| Stage | Real-world mAP50 |
|---|---|
| **Baseline pipeline** | **0 detections** |
| **+ co-occurrence rendering + materials** | **0.45** |
| **+ background diversity** | **0.84** |
| **Synthetic-domain ceiling** | **0.99** |

*Full write-up, code, and every intermediate experiment: [github.com/princySpatel/sim_to_real_blender](https://github.com/princySpatel/sim_to_real_blender)*
