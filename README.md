# Classical Vision: Robust Object Detection

A from-scratch implementation of classical computer vision techniques for **template-based and feature-based object detection** using Python and NumPy.

The project explores the pipeline from low-level image processing to object localization, with a focus on understanding and implementing the underlying algorithms rather than relying on high-level computer vision APIs.

---

## Pipeline

```text
                         CLASSICAL COMPUTER VISION
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
             IMAGE PROCESSING             OBJECT DETECTION
                    │                           │
          ┌─────────┴─────────┐          ┌──────┴──────┐
          │                   │          │             │
      Filtering           Features   Template      Feature
          │                   │        Matching      Matching
          │                   │          │             │
    ┌─────┴─────┐       ┌────┴────┐     │       ┌─────┴─────┐
    │           │       │         │     │       │           │
 Gaussian    Median   Keypoints  Descriptors   Matching  Geometry
    │           │       │         │     │       │           │
 Sobel      Harris     Scale     Local │       Ratio     Consensus
                      Space     Features│       Test         │
                                         │                    │
                                         └─────────┬──────────┘
                                                   │
                                                   ▼
                                           OBJECT LOCALIZATION
```

---

## Image Processing

Implementation of fundamental image-processing operations using NumPy:

- 2D convolution
- Gaussian and median filtering
- Sobel edge detection
- Harris corner detection
- PSNR and SSIM
- Peak detection

These operations form the foundation for the subsequent object-detection pipelines.

---

## Template-Based Detection

Objects are localized using **Normalized Cross-Correlation (NCC)**.

```text
Template + Scene
       │
       ▼
 Integral Image
       │
       ▼
      NCC
       │
       ▼
 Score Map
       │
       ▼
 Peak Detection
       │
       ▼
 Non-Maximum Suppression
       │
       ▼
 Object Locations
```

The implementation includes:

- Integral images for efficient local statistics
- Normalized cross-correlation
- Peak detection
- Non-maximum suppression
- Multi-scale template matching

Experiments investigate robustness to noise, occlusion, grayscale conversion, masking, and scale changes.

---

## Feature-Based Detection

A second detection pipeline uses local image features:

```text
Image
  │
  ▼
Scale-Space
  │
  ▼
Keypoints
  │
  ▼
Dominant Orientation
  │
  ▼
Local Descriptors
  │
  ▼
Descriptor Matching
  │
  ▼
Geometric Consensus
  │
  ▼
Object Localization
```

The implementation includes:

- Scale-space keypoint detection
- Dominant orientation estimation
- Local feature descriptors
- Descriptor matching
- Ratio-based matching
- Geometric consensus for object localization

---

## Template vs Feature Matching

| | Template Matching | Feature Matching |
|---|---|---|
| Representation | Image appearance | Local features |
| Matching | Dense | Sparse |
| Scale | Multi-scale search | Scale-space |
| Rotation | Limited | Orientation-aware |
| Localization | Correlation peaks | Geometric consensus |

The project uses experiments to study the strengths, limitations, and failure cases of both approaches.

---

## From-Scratch Implementation

Core computer vision algorithms are implemented using **NumPy** instead of directly relying on high-level implementations.

Key concepts include:

- Convolution and filtering
- Edge and corner detection
- Integral images
- Normalized cross-correlation
- Multi-scale detection
- Scale-space features
- Local descriptors
- Feature matching
- Geometric localization

---

## Technologies

- **Python**
- **NumPy**
- **OpenCV**
- **Matplotlib**

---

## Applications

The techniques explored in this project are relevant to:

- Object localization
- Image matching
- Visual inspection
- Feature correspondence
- Geometric estimation
- Robotic perception

---

## Author

**Harshada Kale**

BTech Student | Robotics | Computer Vision | Machine Learning
