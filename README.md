# Deep Multimodal Fusion by Channel Exchanging

By Yikai Wang, Wenbing Huang, Fuchun Sun, Tingyang Xu, Yu Rong, Junzhou Huang.

## Dependencies

```
python>=3.6
pytorch>=1.0.0
opencv-python>=4.0
scikit-learn>=0.20.2
```

## Datasets

For semantic segmentation task on NYUDv2 ([offical dataset](https://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html)), we provide a link to download the dataset [here](https://drive.google.com/drive/folders/1mXmOXVsd5l9-gYHk92Wpn6AcKAbE0m3X?usp=sharing). The provided dataset is originally preprocessed in this [repository](https://github.com/DrSleep/light-weight-refinenet), and we add depth data in it.

For image-to-image translation task, a link to download dataset is [taskonomy-sample-model-1](https://github.com/alexsax/taskonomy-sample-model-1.git).

Please modify the data paths in the codes, where we add comments 'Modify data path'.


## Semantic segmentation


First, 
```
cd semantic_segmentation
```
Training script for segmentation with RGB and Depth input, the default setting uses RefineNet (ResNet101),
```
python main.py --gpu 0 -c checkpoint_name  # or --gpu 0 1 2
```
Evaluation script,
```
python main.py --gpu 0 --resume path_to_pth --evaluate  # optionally use --save-img to visualize results
```

Pretrained models on NYUDv2 with ResNet101 and ResNet152 are provided as follows, where single-scale performance is measured by pixel accuracy, mean accuray, and mean IoU:


| Backbone |  ResNet101  |  ResNet152  |
|:-----------:|:-----------:|:-----------:|
| Performance | 76.2 / 62.8 / 51.1 | 77.0 / 64.4 / 51.6 |
| Download |[Google Drive](https://drive.google.com/drive/folders/1wim_cBG-HW0bdipwA1UbnGeDwjldPIwV?usp=sharing)|[Google Drive](https://drive.google.com/drive/folders/1DGF6vHLDgBgLrdUNJOLYdoXCuEKbIuRs?usp=sharing)|


## Image-to-image translation

First, 
```
cd image2image_translation
```
Training script, an example of translation from Shade (2) and Texture (7) to RGB (0) (could reach 62~63 FID score),
```
python main.py --gpu 0 --img-types 2 7 0
```
This script will auto-evaluate on the validation dataset every 5 training epochs. Predicted images will be automatically saved.

For training with other modalities, the index for each img-type is described in Line 70 of ```main.py```.


## Citation
If you find our work useful for your research, please cite the following paper.
```
@inproceedings{wang2020cen,
  title={Deep Multimodal Fusion by Channel Exchanging},
  author={Wang, Yikai and Huang, Wenbing and Sun, Fuchun and Xu, Tingyang and Rong, Yu and Huang, Junzhou},
  booktitle = {Advances in Neural Information Processing Systems (NeurIPS)},
  year={2020}
}
```
