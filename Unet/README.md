## Unet：Unet: Convolutional Networks for Biomedical Image Segmentation(grouper)

## 
| model | address |
| :----- | :----- |
Unet | https://github.com/bubbliiiing/unet-pytorch  
PSPnet | https://github.com/bubbliiiing/pspnet-pytorch
deeplabv3+ | https://github.com/bubbliiiing/deeplabv3-plus-pytorch

### environment
torch==1.2.0    
torchvision==0.4.0   

### dataset
fig_grouper_address:https://www.kaggle.com/datasets/qinhaijing/pic-grouper

### training steps
1.Put the voc data set I provided into the VOCdevkit.
2.Run train.py for training.
3.Run predict.py for predict,it can segment fish and record their feeding area.

#### matters need attention
1. This paper uses VOC format for training.
2. before training, put the tag file in the SegmentationClass under the VOC2007 folder under the VOCdevkit folder.
3. Before training, put the image file in JPEGImages under VOC2007 folder under VOCdevkit folder.
4. Use voc_annotation.py file to generate corresponding txt before training.
5. Change the num_classes value of train.py to +1.
6. Run train.py to start training.  

### predic steps
1. Follow the training steps
2. In the unet.py file, modify model_path, backbone, and num_classes to correspond to the trained file in the following sections; **model_path corresponds to the weight file under the logs folder **.   
```python
_defaults =
    #-------------------------------------------------------------------#
    "model_path"    : 'model_data/unet_vgg_voc.pth',
    
    #--------------------------------#
    "num_classes"   : 2,
 
    #--------------------------------#
    "backbone"      : "vgg",

    #--------------------------------#
    "input_shape"   : [512, 512],
    #--------------------------------#
 
    #--------------------------------#
    "blend"         : True,
    #--------------------------------#
  
    #--------------------------------#
    "cuda"          : True,
}
```
3. run predict.py, generate forecast pictures and fish area
  
### Assessment steps
1. Set num_classes in get_miou.py to add 1 to the number of predicted classes.
2. Set name_classes in get_miou.py as the categories to be distinguished.
3. Run get_miou.py to get the miou size.

## Reference
https://github.com/ggyyzm/pytorch_segmentation  
https://github.com/bonlime/keras-deeplab-v3-plus
