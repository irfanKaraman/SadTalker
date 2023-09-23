# SadTalker

1.Install Anaconda, Python and git.
Anaconda
<--
sudo apt-get update
cd /tmp
apt-get install wget
wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh
sha256sum Anaconda3-2022.05-Linux-x86_64.sh
bash Anaconda3-2022.05-Linux-x86_64.sh
# check
conda info
conda --version
# update conda
conda update conda
conda update anaconda
-->

Python
<-- 
sudo apt-get update
sudo apt install python
-->


git clone https://github.com/OpenTalker/SadTalker.git

cd SadTalker 

conda create -n sadtalker python=3.8

conda activate sadtalker

pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu113

conda install ffmpeg

pip install -r requirements.txt

### Coqui TTS is optional for gradio demo. 
### pip install TTS

2. download models
   bash scripts/download_models.sh

3. start
 ## you need manually install TTS(https://github.com/coqui-ai/TTS) via `pip install tts` in advanced.
python app_sadtalker.py

bash webui.sh

4. memory SWAP set script
   # disable the use of swap
<--
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
-->

