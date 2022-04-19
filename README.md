# Exploiting Unlabeled Data with Vision and Language Models for Object Detection

Official implementation of [Exploiting unlabeled data with vision and language models for object detection]().

[Project]()

## Installation

Our project is developed on [Detectron2](https://github.com/facebookresearch/detectron2).
Please follow the official installation [instructions](https://github.com/facebookresearch/detectron2/blob/main/INSTALL.md).

## Data Preparation
Download the dataset from [COCO](https://cocodataset.org/#home), and put it in the `datasets/` directory.
Download our pre-generated pseudo-labeled data from [here](https://drive.google.com/drive/folders/1TnoMobCYmjcI_eOPBOJpZZw39tUK6dDx?usp=sharing).

Dataset are organized in the following way:
```bazaar
datasets/
    coco/
        annotations/
            instances_train2017.json
            instances_val2017.json
            open_voc/
                instances_eval.json
                instances_train.json
        images/
            train2017/
                000000000009.jpg
                000000000025.jpg
                ...
            val2017/
                000000000776.jpg
                000000000139.jpg
                ...
        
```


## Evaluation with pre-trained models
Mask R-CNN:
<table><tbody>
<!-- START TABLE -->
<!-- TABLE HEADER -->
<th valign="bottom">Training Method</th>
<th valign="bottom">Novel AP</th>
<th valign="bottom">Base AP</th>
<th valign="bottom">Overall AP</th>
<th valign="bottom">download</th>
<!-- TABLE BODY -->
<!-- ROW: with LSJ -->
 <tr><td align="left"><a href="./configs/coco_openvoc_LSJ.yaml">With LSJ</a></td>
<td align="center">34.4</td>
<td align="center">60.2</td>
<td align="center">53.5</td>

<td align="center"><a href="https://drive.google.com/file/d/18rFQNCvGuJl47onXXZAy1ZaYroctAmEz/view?usp=sharing">model</a></td>
</tr>
<!-- ROW: with out LSJ -->
 <tr><td align="left"><a href="./configs/coco_openvoc_mask_rcnn.yaml">W/O LSJ</a></td>
<td align="center">32.3</td>
<td align="center">54.0</td>
<td align="center">48.3</td>

<td align="center"><a href="https://drive.google.com/file/d/1aqc6tqE14TCMtGk9qafg3aFVAXR-tDvr/view?usp=sharing">model</a></td>
</tr>


</tbody></table>

```bash
python -m train_net.py --config configs/coco_openvoc_LSJ.yaml  --num-gpus=1 --eval-only --resume
```

## Training
Training Mask R-CNN with Large Scale Jitter (LSJ).
```bash 
python train_net.py --config configs/coco_openvoc_LSJ.yaml  --num-gpus=8 --use_lsj
```
Training Mask R-CNN without Large Scale Jitter (LSJ).
```bash 
python train_net.py --config configs/coco_openvoc_mask_rcnn.yaml  --num-gpus=8
```
## Citing VL-PLM
If you use VL-PLM in your work or wish to refer to the results published in this repo, please cite our paper:
```BibTeX

```



