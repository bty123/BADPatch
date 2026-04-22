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
cd ~
git clone <repo_url> BADPatch
cd BADPatch
```
Prepare the target MDE networks (Monodepth2, DepthHints, Lite-Mono, SQLdepth, MiDaS, DepthAnything v2) following their official instructions and put them in the directory of `DepthNetworks`. Download their official pretrained model weights into a sub-folder named models inside each network's directory `(e.g., DepthNetworks/monodepth2/models)`.<br>
The directories should be organized as:
```
BadPart
├── DepthNetworks
    ├── depth-hints
    ├── monodepth2
    ├── PlaneDepth
    ├── SQLdepth
├── FlowNetworks
    ├── flow_models
        ├── pretrained
```
