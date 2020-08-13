### MaskStomata: Generalised instance segmentation of stomata for Microscope Images

Developed by Hiranya Jayakody. April 2020.

Smart Robotics Viticulture Group, UNSW, Sydney.


This repository provides the code for a robust stomata detection and instance segmentation method for microscope images of plant leaves. Follow the instructions in Section 1 to test the code on your own dataset.

### Package Dependencies:

Matterport implementation of Mask-RCNN: https://github.com/matterport/Mask_RCNN

Tensorflow >=1.5.1 (Tensorflow 1.5.1 recommended. April 2020)

Keras > 2.0.8 (Keras 2.1.5 recommended. April 2020)

# Getting Started:

Instructions are provided assuming the code is run on the Google Colab environment. More advanced users can set-up the code in their own python environment following the same instructions.

### 0. Download the stomata detector model

Contact hiranya.jayakody@unsw.edu.au to get access to the trained model.

### 1. Using this repository for inference

The following folder structure is recommended for inference tasks.
```
.
|--stomata_inference.ipynb
|--mask_rcnn_stomata.h5
|--images
    |--test
        |--image01.jpg
        |--image02.jpg
        |--...jpg
    |--results
``` 
Instructions on ```inference_stomata.ipynb``` provide guidance on setting-up and running the code in Google's Colab environment. The same procedure applies if the code is set-up in a local machine or a cloud computing instance.

The code will generate results for the images contained in the ```test``` folder, and will save the data in the ```results``` folder. All output images along with a ```results.csv``` file (which contains all metrics) will be saved in this folder.

### 2. Fine tuning the default model for a specific microscope dataset (Transfer Learning)

Average performance may be expected for the default stomata model when the input dataset consists of low-quality images. In such cases, researchers may opt to fine-tune the Mask-RCNN model, using transfer learning techniques.

The following folder structure is recommended for transfer learning tasks.
```
.
|--transfer_learning_stomata.ipynb
|--mask_rcnn_stomata.h5
|--images
    |--train_original
        |--image01.jpg
        |--image02.jpg
        |--...
        |--via_region_data.json
    |--val_original
        |--image01.jpg
        |--image02.jpg
        |--...
        |--via_region_data.json
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
|--logs
```

To start the process, save the labelled train and validation data in ```train_original``` and ```val_original``` folders. The image data in these folders will be prepared for machine learning through ```image_converter.ipynb```.

#### 2.1 Preparing training data

All training and validation data re converted to a 3-channel grayscale colorspace before training, with the aim of removing any biases in the colorspace. ```image_converter.ipynb``` is used to achieve this goal for new training and validation data.

First, save the labelled train and validation data in ```train_original``` and ```val_original``` folders. Follow the instructions in ```image_converter.ipynb```. The resulting training and validation images will be saved in the ```images/train``` and ```images/val``` folders. Make sure you copy over the corresponding ```via_region_data.json``` files from ```train_original``` and ```val_original``` to ```images/train``` and ```images/val``` folders

#### 2.2 Image labelling

VGG Image Annotator (VIA-2.0.8 or higher) is used for labelling training images. Download the browser based annotation tool [here](http://www.robots.ox.ac.uk/~vgg/software/via/).

1. Open VIA tool.
2. Go to **Project>Add local files** and add all images from the ```train``` folder.
3. Select **polygon region shape** from **Region Shape** section.
4. Mark stomata regions by left clicking along the stomata boundary. Press Enter to complete the loop.
5. To save the project, go to **Project>Save** and provide a project name.
6. To save the annotation values, go to **Annotation>Export Annotations(as json)** and save the file as ```via_region_data.json``` inside the train folder. Annotations must be saved for training.
7. Follow steps 1-6 for validation dataset as well.

![via_interface](assets/via_interface.jpg)

#### 2.3 Training Process

Instructions on ```transfer_learning_stomata.ipynb``` provide guidance on setting-up and running the code in the Google Colab environment. The procedure is similar if the code is set-up in a local machine or a cloud computing instance. Training in Google Colab will take extensive time. Using a dedicated machine with GPU capability is recommended for this step.

Make sure all the folder paths are setup correctly before executing the training process. Advanced users can modify additional parameters such as Anchor size for optimum performance.

The new model will be saved in the ```logs``` directory. Keep note of the ```MEAN_PIXEL``` value generated prior to training. This value is later needed for inference.

Inference with the new model can be done with ```inference_stomata.ipynb```. Make sure to modify ```MEAN_PIXEL``` value to match the value generated during training.

### 3. Publications

### 4. Citing this work

Hiranya Samanga Jayakody, Paul Petrie, Hugo de Boer et al. A Generalised Approach for High-throughput Instance Segmentation of Stomata in Microscope Images, 05 June 2020, PREPRINT (Version 1) available at Research Square [+https://doi.org/10.21203/rs.3.rs-33223/v1+]

Contact hiranya.jayakody@unsw.edu.au for latest citation information.







