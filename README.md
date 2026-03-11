# QCMamba: Quality-Aware Cross-Modal Mamba-Attention Fusion for RGB-Infrared Object Detection

<p align="left">
  <a href="#empty"><img src="https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?e&logo=PyTorch&logoColor=white" alt="PyTorch"></a>
  <a href="#empty"><img src="https://img.shields.io/badge/Python-3.8%2B-blue.svg" alt="Python"></a>
  <a href="#empty"><img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License"></a>
  <a href="#empty"><img src="https://img.shields.io/badge/Paper-Submitted-blue.svg" alt="Paper"></a>
</p>

The complete code, dataset configuration files, and pre-trained weights will be released here upon paper acceptance or shortly after code cleanup. **Please Watch and Star this repository for updates! **

---

Multispectral object detection leveraging paired visible (RGB) and infrared (IR) imagery is crucial for robust perception across diverse environmental conditions. However, indiscriminate integration of cross-modal features often introduces significant noise when one modality is degraded (e.g., RGB images in low light, or IR images corrupted by thermal crossover). 

To address this challenge, we propose **QCMamba**, a plug-and-play fusion module seamlessly integrated into a dual-stream YOLO backbone. Our central innovation is the establishment of a **cascaded quality-guidance framework**, which dynamically propagates adaptive weights throughout the entire fusion process to assess modality reliability. 

<p align="center">
  <img src="assets/architecture.pdf" alt="QCMamba Architecture" width="90%">
  <br>
  <em>Figure 1: Overall architecture of the proposed dual-stream multispectral detection framework with QCMamba fusion.</em>
</p>

<p align="center">
  <img src="assets/heatmap.png" alt="Heatmap Visualization" width="80%">
  <br>
  <em>Figure 2: Feature activation heatmaps with and without QRG. The RGB modality is assigned a higher weight in well-lit scenarios (left), whereas the IR modality dominates in low-light conditions (right). White ovals highlight areas of significant cross-modal calibration.</em>
</p>
