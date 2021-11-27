# EHM-GPU-Acceleration

This repository contains the source code and documentation of the Image Search Engine for Digital History:GPU acceleration project. It is part of the Engineering Historical Memory research, contributing to a multilingual and transcultural approach to decode-encode the treasure of human experience and transmit it to the next generation of world citizens.

## Files

* '''main.py''' - main file to run. The baseline of the file contains:
    * D2-Net feature detection and description;
    * Descriptors matching baseline with brute-force algorithm in a Kernel function;
    * RANSAC function to evaluate the matches.
