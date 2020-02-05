# docker build -t poramansfrend/deep-notebooks:ubuntu18.04-cuda10.1-cudnn7-tf-notebook https://github.com/juliandefreitas/notebooks.git#master:ubuntu18.04/gpu/cuda10.1-cudnn7/tf-notebook
# docker run -it --rm --user root poramansfrend/deep-notebooks:ubuntu18.04-cuda10.1-cudnn7-tf-notebook 
# docker run -it --rm --user root poramansfrend/deep-notebooks:ubuntu16.04-cuda10.0-cudnn7-pytorch-v1.0-notebook nvidia-smi
# docker run -it --rm --shm-size=2G -p 8889:8888 poramansfrend/deep-notebooks:ubuntu16.04-cuda10.0-cudnn7-pytorch-v1.0-notebook

# > sudo nvidia-docker build -t cocoflow/tensorflow-1.0x-notebook:ubuntu16.04-cuda10.0-cudnn7 https://github.com/ColinConwell/Notebooks.git#master:ubuntu16.04/cuda10.0-cudnn7/tensorflow-1.0x-notebook

FROM poramansfrend/base-notebook:ubuntu18.04-cuda10.1-cudnn7

USER root
WORKDIR $HOME

# ==============================================================
#  Tensorflow 1.15*
# ==============================================================

# ==============================================================
#  Updates & Upgrades
# ==============================================================

RUN pip install --upgrade pip \
  && conda update conda

RUN pip install --upgrade numpy

# ==============================================================
#  Install Machine Learning Packages
# ==============================================================

RUN apt-get update && \
    apt-get install -y --no-install-recommends ffmpeg && \
    rm -rf /var/lib/apt/lists/* 

RUN conda install --quiet --yes \
    'beautifulsoup4' \
    'conda-forge::blas=*=openblas' \
    'bokeh' \
    'cloudpickle' \
    'cython' \
    'dask' \
    'dill' \
    'h5py' \
    'hdf5' \
    'ipywidgets' \
    'matplotlib-base' \
    'numba' \
    'numexpr' \
    'pandas' \
    'patsy' \
    'protobuf' \
    'pymc3' \
    'scikit-image' \
    'scikit-learn' \
    'scipy' \
    'seaborn' \
    'sqlalchemy' \
    'statsmodels' \
    'sympy' \
    'vincent' \
    'xlrd' \
    && conda clean --all -f -y

RUN pip install opencv-python keras tensorflow==1.15 tensorflow_hub pydot

RUN sudo apt update && \
    sudo apt install graphviz

WORKDIR /home/$NB_USER/work/
USER $NB_USER