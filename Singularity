BootStrap: docker
From: ubuntu:18.04

%labels
    Maintainer zyou@osc.edu
    Recipe https://github.com/OSC/sa_singularity_winehq

%post
    apt update
    apt upgrade -y
    dpkg --add-architecture i386 
    DEBIAN_FRONTEND=noninteractive apt install -y software-properties-common wget
    wget -nc https://dl.winehq.org/wine-builds/winehq.key
    apt-key add winehq.key

    apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main'
    apt update
    DEBIAN_FRONTEND=noninteractive apt install -y winehq-stable=4.0.3~bionic

    # Clean up
    apt autoclean
    apt autoremove --purge -y
    rm -rf /var/lib/apt/lists/*

%runscript
    exec wine64 "$@"
