# PAF-DETR: Enhancing UAV Image Detection with Partial Attention and Dynamic Feature Integration

**Official implementation** of  *"PAF-DETR: Enhancing UAV Image Detection with Partial Attention and Dynamic Feature Integration"* .



## 🚀 Highlights
✅ Partial Attention Fusion  enhances semantics for small object recognition.

✅ Auxiliary branch mitigates information loss in cross-scale feature fusion.

✅ Dynamic Upsampling with adaptive feature alignment.

✅ State-of-the-art performance on VisDrone (52.0% mAP50) and TinyPerson (19.0% mAP50).



##  ⚙️Installation
We use  `python=3.10,pytorch=2.0.1,cuda=11.7`. Other versions may also be available. Clone the repository locally and install with
```
git clone https://github.com/lei12879/PAF-DETR.git
cd PAF-DETR
```


## ⚙️Example conda environment setup


### 1. Create environment
```
conda create --name paf_detr python=3.10 -y
conda activate paf_detr
```
### 2. Install pytorch [Previous PyTorch Versions | PyTorch](https://pytorch.org/get-started/previous-versions/)
```
conda install pytorch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 pytorch-cuda=11.7 -c pytorch -c nvidia
```

### 3. Other needed packages
```
pip install -r requirements.txt
```


##  📂Dataset Preparation


-   Download and extract [VisDrone2019](https://github.com/VisDrone/VisDrone-Dataset.git)  train and val images. 
```
path/to/visdrone/
  annotations/  # annotation json files
  train/    # train images
  val/      # val images
```

You can modify config [`img_folder`](https://github.com/lei12879/PAF-DETR/blob/main/configs/dataset/visdrone_detection.yml)[`ann_file`](https://github.com/lei12879/PAF-DETR/blob/main/configs/dataset/visdrone_detection.yml)

- Download and extract [TinyPerson](https://universe.roboflow.com/chris-d-dbyby/tinyperson)  train and val images. 
```
path/to/tinyperson/
  annotations/  # annotation json files
  train/    # train images
  val/      # val images
```
You can modify config [`img_folder`](https://github.com/lei12879/PAF-DETR/blob/main/configs/dataset/tinyperson_detection.yml)[`ann_file`](https://github.com/lei12879/PAF-DETR/blob/main/configs/dataset/tinyperson_detection.yml)


## 🏋️ Training and Testing

### Single-GPU Training
```bash
# VisDrone 
python tools/train.py -c configs/pafdetr/pafdetr_r18vd_visdrone.yml

# TinyPerson 
python tools/train.py -c configs/pafdetr/pafdetr_r18vd_tinyperson
```

### Multi-GPU Distributed Training

```bash
# 4 GPUs example
python -m torch.distributed.launch --nproc_per_node=4 \
    tools/train.py -c configs/pafdetr/pafdetr_r18vd_visdrone.yml 
```
### Testing
```bash
python tools/train.py -c path/to/config -r path/to/checkpoint --test-only
```

## 📜Citation
If you use `PAF-DETR`  in your work, please use the following BibTeX entries:
```
@article{leipafdetr,
  title     = {PAF-DETR: Enhancing UAV Image Detection with Partial Attention and Dynamic Feature Integration},
  author    = {Lei, Huan and Ren, Lingfei and Wu, Ze and Yang, Wenyuan},
  journal   = {The Visual Computer},
  note      = {Submitted for Review}
}
```
