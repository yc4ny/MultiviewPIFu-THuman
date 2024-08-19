# PIFu: Pixel-Aligned Implicit Function for High-Resolution Clothed Human Digitization
![Teaser Image](https://shunsukesaito.github.io/PIFu/resources/images/teaser.png)

```
@InProceedings{saito2019pifu,
author = {Saito, Shunsuke and Huang, Zeng and Natsume, Ryota and Morishima, Shigeo and Kanazawa, Angjoo and Li, Hao},
title = {PIFu: Pixel-Aligned Implicit Function for High-Resolution Clothed Human Digitization},
booktitle = {The IEEE International Conference on Computer Vision (ICCV)},
month = {October},
year = {2019}
}
```

## Installation
Same environment as the original [PIFu](https://shunsukesaito.github.io/PIFu) repo. 


## Preprocess with THuman2.0/2.1 Dataset

Request access to [THuman Dataset](https://github.com/ytrock/THuman2.0-Dataset) and extract the downloaded dataset. 

1. Run [precomputed radiance transfer (PRT)](https://sites.fas.harvard.edu/~cs278/papers/prt.pdf). 

```
python -m apps.prt_util -i {path_to_unzipped_thuman_data}
```

2. run the following script. Under the specified data path, the code creates folders named `GEO`, `RENDER`, `MASK`, `PARAM`, `UV_RENDER`, `UV_MASK`, `UV_NORMAL`, and `UV_POS`. Note that you may need to list validation subjects to exclude from training in `{path_to_training_data}/val.txt` (this tutorial has only one subject and leave it empty). If you wish to render images with headless servers equipped with NVIDIA GPU, add -e to enable EGL rendering.
```
python -m apps.render_data -i {path_to_rp_dennis_posed_004_OBJ} -o {path_to_training_data} [-e]
```
