<div align="center">
<h1>Proposal-guide Multi-Scale Radar and Vision Fusion for 3D Object Detection</h1>
</div>

## News
The code will be released once the paper is published.

## 1. Introduction

This repository is an official implementation of our paper [Proposal-guide Multi-Scale Radar and Vision Fusion for 3D Object Detection](). This repository contains pytorch training code, evaluation code and pre-trained models.

## 2. Getting Started
### 2.1 Setup Enviroment
Our code is built based on [RayDN](https://github.com/LiewFeng/RayDN) and [StreamPETR](https://github.com/exiawsh/StreamPETR). Please follow [StreamPETR](https://github.com/exiawsh/StreamPETR) to [setup enviroment](https://github.com/exiawsh/StreamPETR/blob/main/docs/setup.md) step by step.

### 2.2 Prepare Data
- Download nuScenes
Download the [nuScenes dataset](https://www.nuscenes.org/login?prevpath=download&prevhash=) to data/nuscenes
- Creating infos file
We modify data preparation in StreamPETR, which addtionally creates tracking information for training
```bash
python tools/create_data_nusc.py --root-path data/nuscenes --out-dir data/nuscenes/pkl/prv --extra-tag nuscenes2d --version v1.0 --use-radar True 
```

### 2.3 Training and Inference
You can train the model following:
```bash
CUDA_VISIBLE_DEVICES=0 python tools/train.py projects/configs/main/prv_nus_r50_h256_w704_main.py --work-dir data/logs/ 
```
You can evaluate the detection model following:
```bash
CUDA_VISIBLE_DEVICES=0 python tools/test.py projects/configs/main/prv_nus_r50_h256_w704_main.py ckpt/prv_nus_r50_h256_w704_main.pth --eval=bbox
```

## 3. Acknowledgements
We thank these great works and open-source codebases:
[RayDN](https://github.com/LiewFeng/RayDN), [StreamPETR](https://github.com/exiawsh/StreamPETR), [PETR](https://github.com/megvii-research/PETR), [DETR3D](https://github.com/WangYueFt/detr3d), [MMDetection3d](https://github.com/open-mmlab/mmdetection3d), 



