# BADPatch Black-box Adversarial Depth Patch on Monocular Depth Estimation
This is the code implementation of our paper “BADPatch: Black-box Adversarial Depth Patch for Inducing Vehicle Vanishing on Monocular Depth Estimation.”

## Environment Preparation
Create a new conda environment of Python 3.9 called BADPatch:<br>
```
conda create -n BADPatch python=3.9
conda activate BADPatch
```
Install required packages:<br>
* torch==2.4.1
* torchvision==0.19.1
* numpy==2.0.2
* networkx
* timm
* tqdm
* ...

## Code Preparation
Clone this repository to folder `~/BADPatch`
```
git clone https://github.com/bty123/BADPatch
cd BADPatch
```
Prepare the target MDE networks ([Monodepth2](https://github.com/nianticlabs/monodepth2), [DepthHints](https://github.com/nianticlabs/depth-hints), [Lite-Mono](https://github.com/noahzn/Lite-Mono), [SQLdepth](https://github.com/hisfog/SfMNeXt-Impl)) following their official instructions and put them in the directory of `DepthNetworks`. Download their official pretrained model weights into a sub-folder inside each network's directory `(e.g., ./DepthNetworks/monodepth2)`.<br>

Prepare the target MDE networks ([MiDaS](https://github.com/isl-org/MiDaS), [DepthAnything v2](https://github.com/DepthAnything/Depth-Anything-V2/tree/main)) following their official instructions and put them in the directory of `checkpoints`. Download the weights of the official pre-trained model to the `checkpoints` directory `(e.g., ./checkpoints/)`.<br>

The directories should be organized as:
```
BADPatch
├── DepthNetworks
    ├── Monodepth2
    ├── DepthHints
    ├── Lite-Mono
    ├── SQLdepth
├── checkpoints
    ├── ...
```

## Dataset Preparation
You will need to download the `Carla dataset` and organize it in the following way. The path of the dataset is `./dataset/Carla/`.<br>
```
├── Carla
    ├── testing
    ├── training
```





