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





















