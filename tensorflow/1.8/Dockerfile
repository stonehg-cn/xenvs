FROM python:3.6.6-jessie

LABEL maintainer="Bin Zhao <wo@zhaob.in>"

# copied from tf https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/docker/Dockerfile

# Pick up some TF dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    curl \
    libfreetype6-dev \
    libhdf5-serial-dev \
    libpng12-dev \
    libzmq3-dev \
    pkg-config \
    python \
    python-dev \
    rsync \
    software-properties-common \
    unzip \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN pip --no-cache-dir install \
    Pillow \
    h5py \
    ipykernel \
    jupyter \
    matplotlib \
    numpy \
    pandas \
    scipy \
    sklearn \
    && \
    python -m ipykernel.kernelspec

# Install TensorFlow CPU version from central repo
RUN pip --no-cache-dir install \
    https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.9.0-cp36-cp36m-linux_x86_64.whl

# TensorBoard
EXPOSE 6006
# IPython
EXPOSE 8888

RUN mkdir -p notebooks

WORKDIR "/notebooks"

CMD ["jupyter", "notebook", "--allow-root"]

# Addtions for stonehg
# installing pyltp is slow, we tend to put it in single layer and do not modify it so frequently
RUN pip --no-cache-dir install pyltp

# Temp till move refunc to public domain
RUN pip --no-cache-dir install https://pypi.v87.us/packages/refunc-1.0.50.tar.gz#md5=19b1745b128639a521291ecd158e1b88

RUN pip --no-cache-dir install \
    gensim \
    ibm_watson \
    google-cloud-translate \
    jieba \
    networkx \
    python-Levenshtein \
    textrank4zh \
    tqdm \
    watson_developer_cloud \
    xgboost
