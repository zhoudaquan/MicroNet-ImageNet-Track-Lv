# MicroNet-ImageNet-Track-Lv

## Introduction
This repo contains the code for the model compression chanllenge Hosted at [NeurIPS 2019](https://micronet-challenge.github.io/scoring_and_submission.html) regarding the ImageNet classification track.

## Backbone model and compression methods
The compression method is mainly based on the paper [NES](https://openreview.net/forum?id=HyxjOyrKvr) where we apply the transformation on the fully connected 1x1 convolution layers with a compression ratio of 2x. Besides, we also apply group convolution on SE blocks to further reduce the parameter number and the computation complexity. During the whole quantization process, no quantization is performed and no specialized hardware support is needed.

The resulting model specification is as below:

Parameter number: 3.11M

FLOPs: 440M

MicroNet Score: 0.507

ImageNet Top1 Classification Acc: 74.962%

As a result, we are eligible to use the free 16-bit quantization gift and thus the model parameter number is reduded to 1.55M and the FLOPs is reduced to 460M * 0.75 as all the multiplications are as quantized to 16 bits also.

Thus, the total score is calculated as 1.55M/6.9M + 330M/1170M = 0.507

## evaluation
To evaluate the model, simply load the model in the efficientnet_quant folder and resume the checkpoint named 75_model by running the bash file run_validate.sh.

bash run_validate.py

To run the file, one needs to modify the data path to the imagenet data folder.
