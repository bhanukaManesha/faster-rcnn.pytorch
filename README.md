This repository was cloned from an earlier version of [faster-rcnn.pytorch repository](https://github.com/jwyang/faster-rcnn.pytorch). 

It contains scripts to extract FasterRCNN features for CLEVR dataset.

### You can download [extracted features from here](https://drive.google.com/drive/folders/1OuGv2vurat4_V4IQsUoZhC0OeZV7Oh_K?usp=sharing). 
It has two keys:
1. `image_features` of shape `N x num_objects x feature_dims`, contains the image features of 15 objects per image of 2048 dimensions.
2. `box_features` of shape `N x num_objects x 6`, where the 6 dimensions refer to: (x1, y1, x2, y2, width, height). They are normalized to 0 and 1.


### To extract features from CLEVR dataset
1. Compile the library by executing ```make.sh``` inside the ```lib``` directory. Note that I had faced several issues while compiling the library. I used the following setup/modifications, which may be helpful to you too:

    a. It requires Pytorch version: 0.4.0 (Versions 0.4.1 and 1.0 do not work!). You can install the correct dependencies using:
   
   ```conda install pytorch=0.4.0 torchvision -c pytorch```
    
    b. You may have to edit the ```CUDA_ARCH``` variable inside ```lib/make.sh``` to ensure things are compatible with your GPU.

2. Download pre-trained [FasterRCNN model](https://drive.google.com/file/d/1duANFkDhANB0IV3gFonSKG6BiMLPQoWX/view?usp=sharing) to a path, say, to: ```${ROOT}/FasterRCNN/models/res101/clevr```
This model has been trained on training images of CLEVR dataset.

3. Download [objects_count.json](https://raw.githubusercontent.com/erobic/faster_rcnn_1_11_34999/master/objects_count.json) inside ```${ROOT}/CLEVR/faster-rcnn/```

3. Put CLEVR images inside the following directories:

    a. Train images inside ```${ROOT}/CLEVR/images/train```

    b. Val images inside ```${ROOT}/CLEVR/images/val``` 

    c. Test images inside ```${ROOT}/CLEVR/images/test```

4. Execute ```./extract_resnet_features_CLEVR.sh```
This will extract the features to ```${ROOT}/CLEVR/features```

Here is the link to the [original repository](https://github.com/jwyang/faster-rcnn.pytorch).
