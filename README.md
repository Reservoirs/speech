<h4> Please create environment with Python 3.9.16 </h4>

## Install thease package
```
pip install wget
apt-get install sox libsndfile1 ffmpeg
pip install text-unidecode
pip install Cython
pip install --upgrade --no-cache-dir gdown
```
Install NeMo
```
python -m pip install git+https://github.com/Reservoirs/NeMo.git@r1.15.0#egg=nemo_toolkit[asr]
```
Install TorchAudio
```
pip install torchaudio -f https://download.pytorch.org/whl/torch_stable.html
```
install LM library
```
pip install pyctcdecode
pip install https://github.com/kpu/kenlm/archive/master.zip
```
## Clone speech repository
```
git clone https://github.com/Reservoirs/speech.git
cd speech/Nemo
```
## Usage
For only Transcription
```
from nemo_service import NemoService
myservice = NemoService(path='sample.wav',language='DE')
result = myservice.run()

print(result.keys()) #{fulltext,time_stamps,confidence}
print(result['fulltext'])
```

For diarization
```
from nemo_service import NemoService
myservice = NemoService(path='sample.wav',language='DE',diarization=True,number_speaker=3,export_srt=True)
result = myservice.run()

print(result.keys()) #{fulltext,time_stamps,confidence,diarize}
print(result['diarize'])
```
For identification
```
from nemo_service import NemoService

myservice = NemoService(path='sample.wav',language='DE',diarization=True,\\
identification=True,number_speaker=4,\\
members=['@DAVID','@JACK','@TOM'],register='register.obj,export_srt=True)

result = myservice.run()

print(result.keys())
print(result['diarize'])
```
How create register.obj
```
speakers={'@DAVID':'DAVID.wav','@JACK':'JACK.wav','@TOM':'TOM.wav'}
import pickle
with open('register.obj', 'wb') as fp:
  pickle.dump(speakers, fp)
```
