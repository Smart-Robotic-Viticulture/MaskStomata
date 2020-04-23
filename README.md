### MaskStomata: Generalised Stomata Detection in Microscope Images

### Prerequisites:

Matterport implementation of Mask-RCNN: https://github.com/matterport/Mask_RCNN

Tensorflow >=1.5.1 (pre-tensorflow 2.0 is recommended)

Keras > 2.0.8 (Keras 2.1.5 recommended)

# Getting Started:

Instructions are provided assuming a Google Colab environment. More advanced users can set-up the code in their own python environment
following the same instructions.

### 1. Using this repository for inference

Following folder structure is recommended for inference tasks.
```
.
|--inference_stomata.ipynb
|--mask_rcnn_stomata.h5
|--Test
    |--image01.jpg
    |--image02.jpg
    |--...jpg
|--Results
``` 

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





