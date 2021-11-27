# EHM-GPU-Acceleration

This repository contains the source code and documentation of the Image Search Engine for Digital History:GPU acceleration project. It is part of the Engineering Historical Memory research, contributing to a multilingual and transcultural approach to decode-encode the treasure of human experience and transmit it to the next generation of world citizens.

## Files

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

## Determine threshold

