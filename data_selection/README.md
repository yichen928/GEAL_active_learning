## Data Selection with GEAL

We introduce how to select training samples with GEAL in this file. These selected samples can be used for the training of downstream task models.

### Data Preparation

+ **PASCAL VOC**

  You can download both PASCAL VOC 2007 and PASCAL VOC 2012 from the [official website](http://host.robots.ox.ac.uk/pascal/VOC/index.html). 

### Pre-trained Model

We use the ViT-Small model pre-trained with DINO framework for data selection. You may directly download the [checkpoint](https://dl.fbaipublicfiles.com/dino/dino_deitsmall16_pretrain/dino_deitsmall16_pretrain_full_checkpoint.pth) from their official repo: [facebookresearch/dino](https://github.com/facebookresearch/dino).

### Directory Structure

Please put the files in the following structure:

```
|--GEAL_active_learning
|	|--data_selection
|		|--data
|			|--VOCdevkit
|				|--VOC2007
|					|--Annotations
|					|--JPEGImages
|					|--ImageSets
|				|--VOC2012
|					|--Annotations
|					|--JPEGImages
|					|--ImageSets
|		|--pretrain
|			|--dino_deitsmall16_pretrain_full_checkpoint.pth
```

### Select Data Samples

+ **PASCAL VOC**

  You can select data samples with the following command. It will generate two splits in `VOCdevkit/VOC2007/ImageSets/Main` and `VOCdevkit/VOC2012/ImageSets/Main`.

  ```
  python voc_dense_kmeans.py --selected 3000
  ```

  The selected sample number can be specified through `--selected_num`  argument. 

### Train Task Model with Selected Samples

+ **PASCAL VOC**

  Please following our [instruction](../downstream/detection/README.md) for downstream object detection task.
