### MaskStomata: Generalised instance segmentation of stomata for Microscope Images

### Prerequisites:

Matterport implementation of Mask-RCNN: https://github.com/matterport/Mask_RCNN

Tensorflow >=1.5.1 (Tensorflow 1.5.1 recommended. April 2020)

Keras > 2.0.8 (Keras 2.1.5 recommended. April 2020)

# Getting Started:

Instructions are provided assuming a Google Colab environment. More advanced users can set-up the code in their own python environment
following the same instructions.

### 1. Using this repository for inference

Following folder structure is recommended for inference tasks.
```
.
|--inference_stomata.ipynb
|--mask_rcnn_stomata.h5
|--test
    |--image01.jpg
    |--image02.jpg
    |--...jpg
|--results
``` 
Instructions on ```inference_stomata.ipynb``` provide guidance on setting-up and running the code in Google Colab environment. The procedure is similar if the code is set-up in a local machine or a cloud computing instance.

The code will generate results for the images contained in the ```test``` folder, and will save the data in the ```results``` folder. All output images along with a ```.csv``` will be saved in this folder.

### 2. Fine tuning the default model for a specific microscope dataset (Transfer Learning)

Following folder structure is recommended for transfer learning tasks.
```
.
|--transfer_learning_stomata.ipynb
|--mask_rcnn_stomata.h5
|--images
    |--train
        |--image01.jpg
        |--image02.jpg
        |--...
        |--via_region_data.json
    |--val
        |--image01.jpg
        |--image02.jpg
        |--...
        |--via_region_data.json    
``` 





