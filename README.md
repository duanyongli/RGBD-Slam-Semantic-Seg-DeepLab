# Slam combined with semantic segmentation method to remove movable objects

We implement common slam techniques to reconstruct the RGB-d mapping. Since the method can't deal with movable objects, we are trying to use semantic segmentation method to remove those objects during mapping (person, cat, car, bus ...). The semantic segmentation library used is [DeepLab-V2](https://bitbucket.org/aquariusjay/deeplab-public-ver2) [VGG-16](http://liangchiehchen.com/projects/DeepLabv2_vgg.html) based model. 

## Result
The result of common technique of slam:
![alt tag](1)

The result of method combined with deeplab:
![alt tag](2)

The result of technique using deep learning method is heavily based on the accuracy of machine learning model. For example, here we can see that we can't remove all of person in the scene but we can remove his last configuration. This is because the DeepLab can recognize this person in the last one while for previous key frames, it can't because the patch of this person is too small.
![alt tag](2)

## Installation

The package is based on [OpenCV 3.3](http://opencv.org/opencv-3-3.html), [g2o](https://github.com/RainerKuemmerle/g2o) and [DeepLab-V2](https://bitbucket.org/aquariusjay/deeplab-public-ver2). The installation process can be found on those links. 

Compilation of DeepLab is the same as compiling process as [Caffe](http://caffe.berkeleyvision.org/). Please compile the deeplab package provided in the repository.

After install all of above packages, please copy `g2o` and `DeepLab` cmake file in to directory`slam_deeplab/cmake_modules/`. Then, compile the package by standard cmake process:

`mkdir build`
`cd build`
`cmake ..`
`make`s


## Experiment

`bin/slam` is for common method.
`bin/slamDP` is for learning based method.