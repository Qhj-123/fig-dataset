# **Benchmark dataset on feeding intensity of the pearl gentian grouper**

Welcome to the repository of [Benchmark dataset on feeding intensity of the pearl gentian grouper(Epinephelus fuscoguttatus♀×E. lanceolatus♂)](https://doi.org/10.1016/j.aqrep.2025.102641)



## The construction workflow of benchmark dataset





In this study, we proposes a workflow for constructing a benchmark dataset. Firstly, we construct an image segmentation subset to train the deep learning semantic segmentation network. Secondly, we compare various clustering methods and determine the optimal number of clusters. In the end, we established a benchmark dataset for the assessment of grouper feeding intensity.

**Highlights**

1. Real-world scenario data: We collected images of fish feeding in high-density recirculating aquaculture environments. 

2. Benchmark dataset: We constructed a benchmark dataset for the assessment of pearl gentian grouper feeding intensity.

3. Deployment network: We proposed an improved lightweight network based on MobileNetV3.



## Data download

To download the processed FIG data, please follow these steps:https://www.kaggle.com/datasets/qinhaijing/pic-grouper

## Workflow for constructing a benchmark dataset

### Training Image segmentation model

1.The dataset is  VOC.

The content to be prepared includes input images and labels
The input image is .jpg image, no need to fix the size, it will automatically resize before passing in the training.
The grayscale image will be automatically converted to RGB image for training, no need to modify yourself. If the suffix of the input image is not jpg, you need to batch convert it to jpg before starting training.Labeled as png images, no fixed size required, automatically resize before passing in training.The value of each pixel of the label is the category to which the pixel belongs.

2.Training process.

The loss value during training will be saved in the loss_%Y_%m_%d_%H_%M_%S folder in the logs folder. The trained weight files are saved in the logs folder.

3.Predict process.

​	3.1 run predict.py

​		mode='predict' , input you need to predict folder name. You can get predicted png pictures.

​	3.2 run get_miou.py

​		miou_mode = 0, it indicates the entire miou calculation process, including obtaining prediction results and calculating miou.

### Clustering method

4.Cluster process

The fish_area.csv file stores data on predicted fish clustering areas.

### Training improved feeding intensity assessment model

5.The dataset is 

MobileNetV3-SE.pth is training optimal model data.

Dataset is fishdata , including four kinds of classification , 'strong','medium','week','none'.
