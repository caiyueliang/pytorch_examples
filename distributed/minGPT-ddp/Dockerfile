FROM nvidia/cuda:11.3.0-cudnn8-devel-ubuntu18.04

RUN apt-get -y update \
    && apt-get -y install curl wget

RUN wget https://www.python.org/ftp/python/3.7.10/Python-3.7.10.tgz
RUN apt-get install -y zlib1g-dev libsqlite3-dev
RUN apt-get install -y libssl-dev openssl libffi-dev

RUN tar -zxvf Python-3.7.10.tgz \
    && cd Python-3.7.10 \
    && ./configure --prefix=/usr/local/python3.7.10 \
    && make \
    && make install \
    && PATH=$PATH:$HOME/bin:/usr/local/python3.7.10/bin

RUN ln -s /usr/local/python3.7.10/bin/python3.7 /usr/bin/python \
    && ln -s /usr/local/python3.7.10/bin/pip3 /usr/bin/pip

RUN pip install pip -U -i https://pypi.tuna.tsinghua.edu.cn/simple/

RUN pip install --default-timeout=3600 torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0 --extra-index-url https://download.pytorch.org/whl/cu113 -i https://pypi.tuna.tsinghua.edu.cn/simple/
