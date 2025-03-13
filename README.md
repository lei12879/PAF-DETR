# PAF-DETR: Enhancing UAV Image Detection with Partial Attention and Dynamic Feature Integration
Official code of 'PAF-DETR: Enhancing UAV Image Detection with Partial Attention and Dynamic Feature Integration'
## Abstract
With its superior maneuverability and flexibility, the Unmanned Aerial Vehicle(UAV) is able to effortlessly tackle various complex scenarios and challenges. However, due to their small size, limited information, and severe occlusion, the subtle features and semantic information of small objects in UAV images are prone to being lost. This paper proposes Partial Attention Fusion-based Detection Transformer(PAF-DETR)  tailored specifically for enhancing small object detection in UAV images, which employs Partial Attention Fusion module to capture potential small object regions, enhances feature connections through the integration of Feature Alignment Module and CSP-Rep fusion module, and incorporates Dynamic Upsampling module. First, the extracted features from the backbone are input into Attention-Driven Context-Aware Encoder and Auxiliary Branch. Second, within the encoder, attention-based internal scale interaction mechanism is specifically applied to the highest-level feature. Then, a bidirectional fusion strategy is adopted to fuse high-level semantic details with low-level features, while dynamically refining sampling points through Dynamic Upsampling module. Additionally, it propagates the detailed information from low-level feature to high-level feature. Third, Feature Alignment Module in the Auxiliary Branch employs Dynamic Upsampling module to align the features obtained from the backbone's last three stages, and CSP-Rep fusion module injects them into the corresponding features processed by the encoder. Finally, the decoder and head generate precise category probabilities and bounding box coordinates as the final detection predictions. The PAF-DETR-50 excels on the VisDrone dataset, achieving a mAP50-95 of 31.3\% and a mAP50 of 52\%, showcasing its potency in small object detection.
##  Installation
We use  `python=3.10,pytorch=2.0.1,cuda=11.7`. Other versions may also be available.

Please follow the instructions to install both PyTorch and TorchVision dependencies. Installing both PyTorch and TorchVision with CUDA support is needed.

Clone the repository locally and install with
```
git clone https://github.com/lei12879/PAF-DETR.git
cd PAF-DETR
```
## Example conda environment setup

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
##  Usage
### Data Download


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



### Training 
To train PAF-DETR on ViaDrone2019 dataset run:
```
python tools/train.py -c configs/pafdetr/pafdetr_r18vd_visdrone.yml
```
To train PAF-DETR on TinyPerson dataset run:
```
python tools/train.py -c configs/pafdetr/pafdetr_r18vd_tinyperson
```


###  Testing
```
python tools/train.py -c path/to/config -r path/to/checkpoint --test-only
```

## Citation
If you use `PAF-DETR`  in your work, please use the following BibTeX entries:
```
@article{lei2024pafdetr,
  title     = {PAF-DETR: Enhancing UAV Image Detection with Partial Attention and Dynamic Feature Integration},
  author    = {Lei, Huan and Ren, Lingfei and Wu, Ze and Yang, Wenyuan},
  journal   = {The Visual Computer},
  note      = {Submitted for Review}
}
```
