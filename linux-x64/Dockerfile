# Multistage docker build, requires docker 17.05

# builder stage
FROM ubuntu:20.04

RUN set -ex && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get --no-install-recommends --yes install \
        git \
        build-essential \
        cmake \
        libuv1-dev \
        libssl-dev \
        libhwloc-dev \
        nmon \
        wget


COPY ./entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh


WORKDIR /miner


#RUN wget https://github.com/xmrig/xmrig/releases/download/v6.20.0/xmrig-6.20.0-focal-x64.tar.gz
COPY ./xmrig-6.20.0-focal-x64.tar.gz /miner/xmrig-6.20.0-focal-x64.tar.gz
RUN tar -xf xmrig-6.20.0-focal-x64.tar.gz
WORKDIR /miner/xmrig-6.20.0/

ENTRYPOINT ["/entrypoint.sh"]
