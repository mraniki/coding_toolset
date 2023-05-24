FROM ubuntu:16.04

WORKDIR /tmp/

RUN set -ex; \
    dpkg --add-architecture i386; \
    DEBIAN_FRONTEND=noninteractive apt-get update -y; \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
        apt-transport-https \
        binutils \
        cabextract \
        curl \
        # To take screenshots of Xvfb display
        imagemagick \
        p7zip \
        software-properties-common \
        wget \
        unzip \
        xz-utils \
        xvfb \
        fluxbox \
        x11vnc

RUN set -ex; \
    wget https://dl.winehq.org/wine-builds/Release.key; \
    apt-key add Release.key; \
    apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/; \
    DEBIAN_FRONTEND=noninteractive apt-get update -y; \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --install-recommends \
        winehq-stable --allow-unauthenticated; \
    rm Release.key

RUN set -ex; \
    wget https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks; \
    chmod +x winetricks; \
    mv winetricks /usr/local/bin

COPY waitonprocess.sh /docker/
RUN chmod a+rx /docker/waitonprocess.sh
