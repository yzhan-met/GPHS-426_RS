FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    curl \
    build-essential \
    gfortran \
    python \
    flex \
    libnetcdf-dev \
    libgsl-dev \
    gawk \
    vim \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/ \
  && curl -SL http://www.libradtran.org/download/libRadtran-2.0.5.tar.gz \
    | tar -xzC /opt/ \
  && mv /opt/libRadtran-2.0.5 /opt/libRadtran \
  && cd /opt/libRadtran \
  && ./configure && make

ENV PATH /opt/libRadtran/bin:$PATH

WORKDIR /opt/libRadtran

VOLUME ["/opt/libRadtran/shared"]
