I'm not the author of the code, just did minor code fixes. 
I want this on my git solely not to have to debug it again.


In order to run and generate your own sentences:

open *rnn_theano.py*

Uncomment commented lines and run it. This will tokenize and save X, Y and the dictionaries for the vocabulary into a pickle file *save.p*.

For following runs, comment the first section of the code again. (You don't have to tokenize and create the dicts everytime.)

Modify your *generate_sentence()* func for extra fun.


**[Please read the blog post that goes with this code!](http://www.wildml.com/2015/09/recurrent-neural-networks-tutorial-part-2-implementing-a-language-model-rnn-with-python-numpy-and-theano/)**

### Jupyter Notebook Setup

System Requirements:

- Python, pip
- (Optional) [virtualenv](https://virtualenv.pypa.io/en/latest/)

To start the [Jupyter Notebook](https://jupyter.org/index.html):

```bash
# Clone the repo
git clone https://github.com/dennybritz/rnn-tutorial-rnnlm
cd rnn-tutorial-rnnlm

# Create a new virtual environment (optional, but recommended)
virtualenv venv
source venv/bin/activate

# Install requirements
pip install -r requirements.txt
# Start the notebook server
jupyter notebook
```

### Setting up a CUDA-enabled GPU instance on EC2:

```bash
# Install build tools
sudo apt-get update
sudo apt-get install -y build-essential git python-pip libfreetype6-dev libxft-dev libncurses-dev libopenblas-dev  gfortran python-matplotlib libblas-dev liblapack-dev libatlas-base-dev python-dev python-pydot linux-headers-generic linux-image-extra-virtual
sudo pip install -U pip

# Install CUDA 7
wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1410/x86_64/cuda-repo-ubuntu1410_7.0-28_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1410_7.0-28_amd64.deb
sudo apt-get update
sudo apt-get install -y cuda
sudo reboot

#Install requirements
cd nn-theano
sudo pip install -r requirements.txt

# Set Environment variables
export CUDA_ROOT=/usr/local/cuda-7.0
export PATH=$PATH:$CUDA_ROOT/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CUDA_ROOT/lib64
export THEANO_FLAGS=mode=FAST_RUN,device=gpu,floatX=float32
# For profiling only
export CUDA_LAUNCH_BLOCKING=1

# Startup jupyter noteboook
jupyter notebook
```

To start a public notebook server that is accessible over the network you can [follow the official instructions](http://jupyter-notebook.readthedocs.org/en/latest/public_server.html#notebook-public-server).
