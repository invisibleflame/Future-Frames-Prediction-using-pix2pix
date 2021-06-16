# Future-Frames-Prediction-using-pix2pix

This repository contains implementation of future frames prediction using a 3D unet GAN taking a sequence of 7 frames and giving an output of the corresponding 7 frames.

The code is written in Python 3.7 using tensorflow, and trained on Intel(R) Xeon(R) CPU @ 2.20GHz with Nvidia Tesla T4 15GB GPU

## Generator
The architecture is a 3D U-Net with skip connections, in which downsampling layers are made from Conv3D and upsampling from conv3Dtranspose, which takes input a series of 7 images of size (256 X 256 X 3) and outputs a series of 7 images of size (256 X 256 X 3). Encoder layers convert images into latent space of size (1 X 1 X 512). Decoder layers  upsamples the series of images to original shape. L1 loss is used to the generator along with the Gan loss. 

<img src="/results/genmodel.png"/>


## Discriminator
It takes the series of images given as output by the GAN and the target output series. It concatenates the both and then uses Conv3D with batch normalisation to downsample the sequences. After that the binary cross entropy is used to find the discriminator loss.  

## Training

Currently the training takes approximately 3300 seconds on the above mentioned device configuration, while using a batch size of 4. 

Link to data used: https://drive.google.com/drive/folders/1kZwg82ANdirnviPJjOKSAXN-GixH7fmN?usp=sharing

## Results

Inputs:

<img src="/results/1.png" width="128"/> <img src="/results/2.png" width="128"/> <img src="/results/3.png" width="128"/> <img src="/results/4.png" width="128"/> <img src="/results/5.png" width="128"/> <img src="/results/6.png" width="128"/> <img src="/results/7.png" width="128"/>
<!-- ![image](/results/1.png) ![image](/results/2.png) ![image](/results/3.png) ![image](/results/4.png) ![image](/results/5.png) ![image](/results/6.png)  ![image](/results/7.png) -->

Outputs: 

<img src="/results/8.png" width="128"/> <img src="/results/9.png" width="128"/> <img src="/results/10.png" width="128"/> <img src="/results/11.png" width="128"/> <img src="/results/12.png" width="128"/> <img src="/results/13.png" width="128"/> <img src="/results/14.png" width="128"/>

With a PSNR of 29.88, the model has beaten the cvpr 2019 paper for the same (<a href='https://openaccess.thecvf.com/content_CVPR_2019/papers/Kwon_Predicting_Future_Frames_Using_Retrospective_Cycle_GAN_CVPR_2019_paper.pdf' target="_blank"> Click Here</a>)

<center>Made with ❤ by Bhuvan Aggarwal and Omkar Ghugarkar</center>
