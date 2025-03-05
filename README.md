# PAF-DETR: Enhancing UAV Image Detection with Partial Attention and Dynamic Feature Integration

This code is based on [RT-DETR](https://github.com/lyuwenyu/RT-DETR.git).
## Setup
```
pip install -r requirements.txt
```
##  Usage
### Data Download
All datasets can be downloaded from the following links. 

[VisDrone2019](https://github.com/VisDrone/VisDrone-Dataset.git)

[TinyPerson](https://universe.roboflow.com/chris-d-dbyby/tinyperson)

### Training 
#### Training  on the VisDrone dataset
```
python tools/train.py -c configs\rtdetrv2\pafdetr_r18vd_visdrone.yml
```
####  Training  on the TinyPerson dataset
```
python tools/train.py -c configs\rtdetrv2\pafdetr_r18vd_tinyperson.yml
```

##  Testing
```
python tools/train.py -c path/to/config -r path/to/checkpoint --test-only
```
### Train custom data

set `remap_mscoco_category: False`. This variable only works for ms-coco dataset.
