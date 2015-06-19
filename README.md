# Getting Started

## Code (tested on Ubuntu 14.10)

### Install for a new Machine

`sudo apt-get install -y git python-pip python-yaml python-numpy python-scipy python-matplotlib ipython ipython-notebook python-pandas python-sympy python-nose libfreetype6-dev libpng-dev`

### Install General Python deps:

`sudo pip install theano scikit-learn scikit-image`

If `skimage.io` has issues, try: `sudo pop install -U scikit-image`.

### Install Lasange

```
git clone https://github.com/Lasagne/Lasagne.git
cd Lasagne/
pip install -r requirements.txt
sudo python setup.py install
```

### Install pylearn2

```
git clone git://github.com/lisa-lab/pylearn2.git && cd pylearn2/ && sudo python setup.py develop
```

#### Create a [~/.theanorc](http://deeplearning.net/software/theano/library/config.html) file

Ex Contents:

```
[global]
floatX = float32
device = gpu0

```

[Override with another device via](http://deeplearning.net/software/theano/library/config.html): `THEANO_FLAGS='device=gpu0'` prefix. Get a list of gpus via: `nvidia-smi -L`.

### Clone Code from ciresan and theanet

`git submodule update --init --recursive`

## Data

### Install

`sudo apt-get install -y p7zip-full graphicsmagick`

### Download & Unpack Data

Download from [kaggle](https://www.kaggle.com/c/diabetic-retinopathy-detection/data?trainLabels.csv.zip) (maybe with w3m), run to unpack:

`7z x train.zip.001`

Place these images into `data/train/orig`

Place `trainLabels.csv` into `data/train`

### Preparing Data for the Network

#### Full Size Originals -> Smaller Originals (~2 hours)

(Ex) This will create 3 batchfiles for graphicsmagick to output 256x256 pngs:

```
mkdir data/train/cent_crop_256
python data/create_resize_batchfiles.py data/train/orig/ data/train/cent_crop_256/ 2 256 3
```

Then follow the on screen directions, which will list what commands to run to process the images cataloged in the generated batchfiles.

#### Standardization

... Coming soon

## The Network

### Training the network

`python -m my_code.VGGNet`

# Running tests

`make test`

# Getting Help

- [SO](http://stackoverflow.com/questions/tagged/neural-network)
- [DataScience Beta](http://datascience.stackexchange.com/questions/tagged/deep-learning)
- [CrossValidated](http://stats.stackexchange.com/questions/tagged/deep-learning)
