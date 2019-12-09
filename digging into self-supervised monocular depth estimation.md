### digging into self-supervised monocular depth estimation

####  abstract

This paper proposes:

1. a minimum reprojection loss (robust)
2. a full-resolution multi-scale sampling method (reduce visual artifacts)
3. auto-tasking loss (ignore training pixels that violate camera motion assumptions)

#### introduction

##### problem

The problem of using stereo pairs and monocular video:

- monocular: 

need to estimate the egomotion between temporal image pairs

- stereo:

make the camera-pose estimation a one-time offline calibration, but may cause issues related to occlusion and texture-copy artifacts

##### solutions

This paper proposes three innovations:

- an appearance matching loss (to solve the problem of occluded pixels)
- an auto-masking approach (ignore pixels where no relative camera motion is observed)
- a multi-scale appearance matching loss (a reduction in depth artifacts)

#### related work

##### supervised depth estimation

The ground truth depth is challenging to acquire.

##### self-supervised monocular training

The network has to estimate the camera pose between frames.

Recent approaches have also begun to close the performance gap between monocular and stereo-based self-supervision.

##### appearance based loss

It can improve the depth estimation performance compared to simple pairwise pixel differences.

The combination of appearance based loss and an error fitting term has also been used.

#### method

##### self-supervised training

problem: there are many possible incorrect depths.

solution: 1. enforce smoothness in the depth maps.          2. compute photo-consistency on patches when solving for per-pixel depth via global optimization
          
**Our solution: formulate our problem as the minimization of a photometric reprojection error when training.**

- **As for stereo training, we solve for camera pose and depth simultaneously to minimize L<sub>p</sub>.**
- **As for monocular training, we use two frames temporally adjacent to I<sub>t</sub> as source frames.**

##### improved self-supervised depth estimation

This paper proposed several methods to close the gap between monocular models and best fully-supervised models.

###### per-pixel minimum reprojection loss

problem: 1. out-of-view pixels  2. occluded pixels

existing solution: use average (cannot solve the second problem)

our solution: use minimum (can solve both)

###### auto-masking stationary pixels

When the camera is static and the object is moving, we introduce a per-pixel mask *μ* to the loss.

###### multi-scale estimation

problem: local optimal 

existing solution: compute the photometric error on images at the resolution of each decoder.
This method will create holes in the image and will complicate the task for depth network.

our solution: instead of computing the photometric error, we do the following process: 1. upsample the lower resolution depth maps to the input image resolution. 2. reproject, resample  3. compute the error at this higher input resolution.

**Note that the weights pretrained on ImageNet will lead to higher accuracy.**

**We use reflection padding instead of zero padding, which leads the reduction of the border artifacts.**


































