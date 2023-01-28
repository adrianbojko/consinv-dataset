# ConsInv Dataset

This repository contains the dataset corresponding to the BMVC 2022 paper "Self-Improving SLAM in Dynamic Environments: Learning When to Mask" with train/val/test splits. The paper itself, supplementary materials, poster and video are here: https://bmvc2022.mpi-inf.mpg.de/654/ . **ConsInv dataset includes 150 lossless sequences and over 85,000 pairs of stereo images!**

![ConsInv Dataset](/consinv_dataset.png "ConsInv Dataset")
<div align="center">
<em>ConsInv-Outdoors (top) and ConsInv-Indoors (bottom)</em>
</div>


## Citation

```
    @inproceedings{Bojko_2022_BMVC,
    author    = {Adrian Bojko and Romain Dupont and Mohamed Tamaazousti and Herve Le Borgne},
    title     = {Self-Improving SLAM in Dynamic Environments: Learning When to Mask},
    booktitle = {33rd British Machine Vision Conference 2022, {BMVC} 2022, London, UK, November 21-24, 2022},
    publisher = {{BMVA} Press},
    year      = {2022},
    url       = {https://bmvc2022.mpi-inf.mpg.de/0654.pdf}
    }
```

## Download
**Calibration files** here:
- [Calibration files](https://1drv.ms/u/s!AquWoxc7jCZM1F2rN1wSd0UeA2Df?e=4fLXcj) (5 KB)

**ConsInv-Indoors**  is under [CC BY-NC-SA 4.0 license](https://creativecommons.org/licenses/by-nc-sa/4.0/) and can be downloaded here: 
- [ConsInv-Indoors images](https://1drv.ms/u/s!AquWoxc7jCZM1GLAIe7hG4bUb4RZ?e=OwABhg) (65.3 GB, Onedrive may ask for login, please see the notes)
- [ConsInv-Indoors semantic masks](https://1drv.ms/u/s!AquWoxc7jCZM1GBCjP4HJVT2W_Xi?e=qC1st1) (137 MB), computed with the model from the paper [Learning to Segment Dynamic Objects using SLAM Outliers](https://ieeexplore.ieee.org/abstract/document/9412341).

**ConsInv-Outdoors** is under a *different license, similar to CC BY-NC-SA 4.0*. It requires personal identifying information (*e.g.*, human faces, car registration plates) to be removed when content from the database is shared, *e.g.*, in papers or online. To obtain a free access to this subset, please contact us. You can get two anonymized sequences here:
- [ConsInv-Outdoors images (anonymized sample)](https://1drv.ms/u/s!AquWoxc7jCZM1GFTKNiu5NGnQJqd?e=C3ydUk) (3.17GB, Onedrive may ask for login, please see the notes)
- [ConsInv-Outdoors semantic masks (anonymized sample)](https://1drv.ms/u/s!AquWoxc7jCZM1F99Dr3w99WesyTi?e=8hByHF) (18.4 MB), computed with Mask R-CNN.
- **ConsInv-Outdoors images (full)** (97.3 GB): please contact us.
- **ConsInv-Outdoors semantic masks (full)** (383 MB): please contact us.

**TUM RGB-D** semantic masks (16.3 MB) used in our paper and computed with the model from our other paper [Learning to Segment Dynamic Objects using SLAM Outliers](https://ieeexplore.ieee.org/abstract/document/9412341) are available here: 
- [TUM RGB-D semantic masks](https://1drv.ms/u/s!AquWoxc7jCZM1F63AW6vXXSTEAn0?e=CTjCN5).

## Contact
Please contact us at *consinv-dataset{@}bojko.ai* . Alternatively, for issues other than access to ConsInv-Outdoors, you can open a Git issue.

## Notes
### General
- **Onedrive may ask for login with a Microsoft account to download large files**. We have no control over this as it is an imposed abuse protection from Microsoft. You will be able to download files immediately after login; you do **not** need to ask for permissions.
- The dataset is huge due to having 1280x720 stereo lossless PNG files.
- The anonymized ConsInv-Outdoors samples can be used to share images/videos without having to anonymize them.

### Datasets
- The general naming pattern of sequences is `(tr|v|te)_[static_env_|static_cam_]_(easy|hard|veryhard)_*`. *tr*/*v*/*te* respectively indicate training/validation/test sequences. *static_cam* indicates that the camera does not move and *static_env* that no objects move. *easy/hard/veryhard* gives a qualitative estimate of the difficulty of sequences in terms of dynamic motion of both camera and objects.
- We provide monocular and stereo semantic masks for ConsInv-Outdoors. Stereo semantic masks are computed on rectified stereo images.
- *delay.txt* (global delay) / *delay_maskrcnn.txt* (per-class delays, only some sequences) give the frames numbers from which you should start applying semantic masks to get a good baseline without a full Temporal Masking pipeline.
- ConsInv-Outdoors is designed for monocular use and ConsInv-Outdoors for stereo use. Still, we provide stereo images for both as well as IMU data. Please note that IMU data has **not** been used nor checked.
- Some sequences may seem to have a "washed" color. This is normal and due to the camera type (Mynt EYE D1000-120).
- The ground truth has been checked to be consistent with real-world measurements. Still, it was not computed with a motion capture system and may not be perfect. Ground truth files are not provided for static_cam sequences as the camera is static, *i.e.*, the ground truth is a constant zero.
