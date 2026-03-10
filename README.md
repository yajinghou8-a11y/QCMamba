# QCMamba: Quality-Aware Cross-Modal Mamba-Attention Fusion for RGB-Infrared Object Detection

<p align="left">
  <a href="#empty"><img src="https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?e&logo=PyTorch&logoColor=white" alt="PyTorch"></a>
  <a href="#empty"><img src="https://img.shields.io/badge/Python-3.8%2B-blue.svg" alt="Python"></a>
  <a href="#empty"><img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License"></a>
  <a href="#empty"><img src="https://img.shields.io/badge/Paper-Submitted-blue.svg" alt="Paper"></a>
</p>

This repository will host the official PyTorch implementation of the paper **"QCMamba: Quality-Aware Cross-Modal Mamba-Attention Fusion for RGB-Infrared Object Detection"**.

## 📢 News & Updates
- **[🔥 Coming Soon]** The complete PyTorch training/evaluation code, dataset configuration files, and pre-trained weights (for DroneVehicle, M3FD, and LLVIP) will be released here upon paper acceptance or shortly after code cleanup. **Please Watch and Star this repository for updates! 🚀**

---

## 💡 Overview

Multispectral object detection leveraging paired visible (RGB) and infrared (IR) imagery is crucial for robust perception across diverse environmental conditions. However, indiscriminate integration of cross-modal features often introduces significant noise when one modality is degraded (e.g., RGB images in low light, or IR images corrupted by thermal crossover). 

To address this challenge, we propose **QCMamba**, a plug-and-play fusion module seamlessly integrated into a dual-stream YOLO backbone. Our central innovation is the establishment of a **cascaded quality-guidance framework**, which dynamically propagates adaptive weights throughout the entire fusion process to assess modality reliability. 

By synergizing **Multi-Scale Scan (MS-Scan)** with **Cross-Attention State-Space (CASS)** modules, QCMamba effectively resolves the critical issue of noise introduction inherent in direct fusion strategies, ensuring that degraded modalities do not pollute the fused representation.

---

## 🏗️ Architecture

QCMamba employs a three-stage cascaded architecture to jointly address quality guidance, scanning diversity, and cross-modal alignment within a unified framework.

<p align="center">
  <img src="assets/architecture.png" alt="QCMamba Architecture" width="90%">
  <br>
  <em>Figure 1: Overall architecture of the proposed dual-stream multispectral detection framework with QCMamba fusion.</em>
</p>

### Key Components:
1. **Quality-Aware Residual Gating (QRG):** Assesses per-position modality reliability and suppresses noise from degraded modalities at the source.
2. **Multi-Scale Scan (MS-Scan):** Combines 6-directional state-space scanning with heterogeneous depthwise convolutions to capture both long-range dependencies and fine-grained local patterns.
3. **Cross-Attention State-Space (CASS):** Synergizes the precise spatial alignment of Cross-Attention with the efficient long-range propagation of Mamba.

---

## 👁️ Visualization: Dynamic Quality Modulation

To intuitively validate the effectiveness of the QRG module, we visualize the feature activation heatmaps under varying illumination conditions.

<p align="center">
  <img src="assets/heatmap.png" alt="Heatmap Visualization" width="80%">
  <br>
  <em>Figure 2: Feature activation heatmaps with and without QRG. The RGB modality is assigned a higher weight in well-lit scenarios (left), whereas the IR modality dominates in low-light conditions (right). White ovals highlight areas of significant cross-modal calibration.</em>
</p>

QRG computes dynamic weights based on cross-modal divergence. This compels the degraded modality to utilize the reliable counterpart as a reference for feature calibration, effectively suppressing background noise and sharply enhancing target representations.

---

## 🏆 Main Results (Preview)

QCMamba demonstrates exceptional architecture-agnostic adaptability. When integrated into six different YOLO generations (YOLOv5s to YOLOv11s), it consistently outperforms standard channel concatenation baselines.

Extensive evaluations confirm QCMamba's superiority over current state-of-the-art methods:
* **DroneVehicle:** `86.3%` mAP50 / `65.0%` mAP50-95
* **M3FD:** `86.6%` mAP50 / `60.3%` mAP50-95
* **LLVIP:** `97.5%` mAP50 / `78.4%` mAP75

*(Detailed tables and pre-trained checkpoints will be provided in the upcoming code release).*

---

## 📖 Citation

If you find our framework or architectural design useful for your research, please consider citing.
