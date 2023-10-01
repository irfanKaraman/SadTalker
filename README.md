# SadTalker

1.Install Anaconda, Python and git.

- Anaconda
```
sudo apt-get update
sudo apt-get install wget
wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh
bash Anaconda3-2022.05-Linux-x86_64.sh
```
reload bash
```
. ~/.bashrc
```

# check---
```
conda info
conda --version
```
# update conda---
```
conda update conda
conda update anaconda
```

- Python (if its not installed already)
```
sudo apt-get update
sudo apt install python3
```

- Git (if its not installed already)
```
sudo apt install git
```

2. SadTalker Installation
   
```
git clone https://github.com/OpenTalker/SadTalker.git

cd SadTalker

conda create -n sadtalker python=3.8

conda activate sadtalker

sudo apt install pip
```
```
pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu113
```
```
conda install ffmpeg
sudo apt install ffmpeg

pip install -r requirements.txt

### pip install TTS (text to speech)
pip install TTS
```

3. download models
```
bash scripts/download_models.sh
```

4. Start SadTalker
```
bash webui.sh
```


# Text-to-Image WebUI
```
sudo apt install wget git python3 python3-venv libgl1 libglib2.0-0
```
```
mkdir Text2Img
cd Text2Img
```
```
wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh
```
```
webui.sh
```


```





























































```
WSL setup for stable UI
# install conda (if not already done)
wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh
chmod +x Anaconda3-2022.05-Linux-x86_64.sh
./Anaconda3-2022.05-Linux-x86_64.sh

# Clone webui repo
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui

# Create and activate conda env
conda env create -f environment-wsl2.yaml
conda activate automatic





for Docker Installation
```
docker run --gpus "all" --rm -v $(pwd):/host_dir wawa9000/sadtalker \
--driven_audio /host_dir/deyu.wav \
--source_image /host_dir/image.jpg \
--expression_scale 1.0 \
--still \
--result_dir /host_dir
```




cd SOMEWHERE_YOU_LIKE
```
bash <(wget -qO- https://raw.githubusercontent.com/Winfredy/OpenTalker/main/scripts/download_models.sh)

export SADTALKER_CHECKPOINTS=/path/to/SadTalker/checkpoints
```

Start the WebUI via ```webui.sh or webui_user.sh```
default method is ```bash webui.sh```


# ERRORS

if you are running on CPU, you need to specific
```
export COMMANDLINE_ARGS="--disable-safe-unpickle"
```


Memory SWAP set script
- disable the use of swap
```
sudo swapoff -a

# create the SWAP file. Make sure you have enough space on the hard disk.
# here is my size, the total size is bs*count B
sudo dd if=/dev/zero of=/swapfile bs=1024 count=136314880 status=progress
# output:
# 139458259968 bytes (139 GB, 130 GiB) copied, 472 s, 295 MB/s
# 136314880+0 records in
# 136314880+0 records out
# 139586437120 bytes (140 GB, 130 GiB) copied, 472.372 s, 296 MB/s

# Mark the file as SWAP space:
sudo mkswap /swapfile
# output:
# Setting up swapspace version 1, size = 130 GiB (139586433024 bytes)
# no label, UUID=25a565d9-d19c-4913-87a5-f02750ab625d

# enable the SWAP.
sudo swapon /swapfile

# check if SWAP is created
sudo swapon --show
# output:
# NAME      TYPE SIZE USED PRIO
# /swapfile file 130G   0B   -2

# Once everything is set, you must set the SWAP file as permanent, else you will lose the SWAP after reboot. Run this command:
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

```
sudo apt update
```
