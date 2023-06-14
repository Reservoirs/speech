# speech
install thease package

!pip install wget
!apt-get install sox libsndfile1 ffmpeg
!pip install text-unidecode
!pip install Cython
!pip install --upgrade --no-cache-dir gdown

# ## Install NeMo
#BRANCH = 'r1.15.0'
!python -m pip install git+https://github.com/Reservoirs/NeMo.git@r1.15.0#egg=nemo_toolkit[asr]
## Install TorchAudio
!pip install torchaudio -f https://download.pytorch.org/whl/torch_stable.html

## install LM library
!pip install pyctcdecode
!pip install https://github.com/kpu/kenlm/archive/master.zip
