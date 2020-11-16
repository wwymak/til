# Installing tensorflow v2.x

Unlike pytorch, tensorflow does not have an 'official' conda install package. Currently, it's installation instructions for GPU (using pip install) is [here](https://www.tensorflow.org/install/gpu)

However, you **must** follow the software requirements listed at https://www.tensorflow.org/install/gpu#software_requirements for the gpu to be detected. Rather than messing up your system cudnn etc, my installation process is:

1. create new conda env with python3.7 (`conda create -n tensorflow-2.2 python=3.7`)
1. install cudatoolkit with conda (`conda install -c anaconda cudatoolkit=10.1`)
1. install cudnn with conda (`conda install -c nvidia cudnn=7.6`)
1. install tensorflow with pip (`pip install tensorflow==2.2`)
