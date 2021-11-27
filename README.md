# EHM-GPU-Acceleration

This repository contains the source code and documentation of the Image Search Engine for Digital History:GPU acceleration project. It is part of the Engineering Historical Memory research, contributing to a multilingual and transcultural approach to decode-encode the treasure of human experience and transmit it to the next generation of world citizens.

## Files

This section contains the documentation of the source code of this repository. Some content is based on external repositories and referenced accordingly.
* ```main.py``` - main file to run. The baseline of the file contains:
    * D2-Net feature detection and description;
    * Descriptors matching baseline with brute-force algorithm in a Kernel function;
    * RANSAC function to evaluate the matches.
* ```test.py``` - modified from main file to run RANSAC function in parallel. There is a bug in function ```find_inliers```, which is expected to be fixed in the future.
* ```lib``` - folder containing the library files, which are copied from the [D2-Net](https://github.com/mihaidusmanu/d2-net.git) repository.
* ```models``` - folder containing the pre-trained model files, which are copied from the [D2-Net](https://github.com/mihaidusmanu/d2-net.git) repository.
* ```input``` - folder containing four datasets and a script used to generate the dataset list. The dataset inputted to the search engine can be selected by the variable ```DATABASE``` in the main file.
    * ```1068 small``` contains 1068 images which is resized to the smaller size such that the existing search engine can process them.
    * ```1068 large``` contains 1068 images with original size which are large scales. The search engine has implemented a preprocessing function to resize the large images. It is needed to prove the resize function of search engine with this dataset.
    * ```1668``` contains 1668 images which is used for the old image search engine developed by the bechelor students. It can be used to test the performance of improved search engine.
    * ```3276``` contains 3276 images which is the mixture of existing datasets and other unrelated images.
    * ```generate_dataset_file.py``` - the scipt to generate the dataset file. It can detect all images in target folder can list them in a csv file which can be used for image searcheng by the engine.
* ```output``` - folder cotaining results obtained from ```1668``` dataset and ```1068 small``` dataset. The recall and precision are calculated so that the recall-precision curves are presented. The time consumed by each stage is also counted.
* ```requirements.txt``` - dependencies required for running main file. The dependencies can be easily installed using the package installer pip.

## Image search engine baseline

To use image search engine developed in this project, this section explains the baseline of search engine and illustrate how to use this respository.
* Run ```generate_dataset_file.py``` to generate dataset list for new dataset. The new dataset should be put in ```input``` folder and the location of dataste list is inside the dataset folder.
* Run ```main.py``` to extract feature keypoints and descriptors and perform matching. The ```start_extracting``` function contains keypoints detection and description using D2-Net, while the ```start_matching``` matches feature descriptors. If there have already been keypoints and descriptors for each image in tested dataset, the ```start_extracting``` function can be commanded and only run ```start_matching```.

## Determine threshold

The match of descriptors are evaluated by RANSAC so that the number of inliers are obtained to present how similar two images are. Two images are believed to be matched if the number of inliers is more than the threshold. The precision-recall curve is drawn to find the best threshold which gives the highest possible precision and tolerated recall. In this project, the threshold is determined to be 210 based on the matching result of ```1668``` dataset. This threshold is then tested on ```1068 small``` dataset.
