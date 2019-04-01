FROM ubuntu:bionic

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    software-properties-common \
    curl \
    python3-distutils \
    language-pack-ko \
    gcc \
    make \
    python3.6-dev

## Install pip3.6
RUN curl -o /tmp/get-pip.py "https://bootstrap.pypa.io/get-pip.py"
RUN python3.6 /tmp/get-pip.py

## Setting language
RUN locale-gen ko_KR.UTF-8
ENV LANG ko_KR.UTF-8
ENV LANGUAGE ko_KR.UTF-8
ENV LC_ALL ko_KR.UTF-8

## Setting timezion
ENV TZ Asia/Seoul

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone
RUN apt-get install -y tzdata
RUN rm /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata

## Clean up
RUN apt-get remove -y software-properties-common \
    && apt-get clean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*