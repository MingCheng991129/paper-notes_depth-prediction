
## Geometry-Aware Symmetric Domain Adaptation for Monocular Depth Estimation

### Abstract

GASDA: to explore the labels in the synthetic data and epipolar geometry in the real data jointly. This model achieves better image style transfer and generates high-quality depth maps.

[github](https://github.com/sshan-zhao/GASDA)

### Introduction

existing problems(corresponding solutions): 
- not that many ground truths (unsupervised learning)
- some model performs well in synthetic data but fails in real data (domain adapation techniques)
- may cause distortions (stereo pairs produce additional constraints on the possible depth predictions)

**contributions of this paper:**
- **We propose an end-to-end domain adaptation framework for monocular depth estimation. (generate high-quality results for both image style translation and depth estimation)**

- **training the monocular depth estimator using: ground truth depth in the synthetic domain + epipolar geometry in the real domain**

- **performs well on KITTI and Make3D.**

### Related Work

#### Monocular Depth Estimation





