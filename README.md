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
You will need to download the [Carla dataset](https://drive.google.com/file/d/1lk8rdDiApqFKKBsl5mO6jIze1b6PwMct/view?usp=sharing) and organize it in the following way. The path of the dataset is `./dataset/Carla_own/`.
```
├── Carla
    ├── testing
    ├── training
```
Provide the log path and the dataset path in the file `config.py`:
```
Carla_own_dataset_root = "./dataset/Carla_own/"
log_dir = "./logs"
```

## Generate Attack Patch
Run the following code to launch BADPatch on Monodepth2:
```
python main.py\
    --model_name monodepth2 \
    --attack_method blackbox \
    --n_iter 200 \
    --trail 25 \
    --test_name monodepth2
```
You can change the MDE model with the option `--model_name` and change the attack method with the option `--attack_method`.

## Weather and Distance Test
Run the following code to test the attack performance under different `weather` conditions.
```
python weather_test.py
```
Run the following code to test the attack performance under different `distance` conditions.
```
python distance_test.py
```
By adjusting `attack_name`, `model_name`, and `weather`, the attack performance of different methods can be evaluated across various MDE models and weather conditions.




