FROM ubuntu:18.04

MAINTAINER Andrey Tolmachev <sonulen@gmail.com>

ENV TZ=Europe/Moscow

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt update && apt -y --quiet --no-install-recommends install \
    build-essential \
    ca-certificates \
    apt-utils \
    locales \
    locales-all \
    git \
    && apt -y upgrade \
    && apt-get -y autoremove \
    && apt-get clean autoclean

RUN locale-gen en_US.UTF-8 && dpkg-reconfigure locales

RUN apt -y install  python3-dev \
    python3-pip \
    python3-tk && \
    apt -y autoremove && apt -y autoclean

RUN pip3 install pymavlink

ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='en_US.UTF-8'

