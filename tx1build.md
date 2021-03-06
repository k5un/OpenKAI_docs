---
title: Build & Run on NVIDIA Jetson TX1
keywords: NVIDIA Jetson TX1
tags: [Jetson_TX1]
sidebar: openkai
permalink: tx1build.html
summary: These brief instructions will help you build and run OpenKAI on NVIDIA Jetson TX1
---
# Build & Run on NVIDIA Jetson TX1 (Ubuntu 16.04LTS / JetPack2.3.1)

## JetPack install & flash
Download the latest [JetPack for L4T](https://developer.nvidia.com/embedded/jetpack) and run the installer, choose the following options to be installed and flashed into your Jetson TX1:

<div style="text-align:center">
{% include image.html file="JetPackInstall.png" alt="JetPack install option" caption="JetPack install option" %}
</div>

## Prerequisites

```shell
sudo apt-get update
sudo apt-get -y install git cmake build-essential cmake-curses-gui libatlas-base-dev libprotobuf-dev libleveldb-dev libsnappy-dev libboost-all-dev libhdf5-serial-dev libgflags-dev libgoogle-glog-dev liblmdb-dev protobuf-compiler libgtk2.0-dev pkg-config libdc1394-22 libdc1394-22-dev libjpeg-dev libpng12-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libtbb-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils unzip python-protobuf libeigen3-dev
```

## Git repositories

```shell
cd ~
mkdir src
cd src
git clone https://github.com/dusty-nv/jetson-inference.git
git clone https://github.com/yankailab/OpenKAI.git
```

## ZED
Download the latest driver from ZED site and run

```shell
chmod u+x ZED_SDK_Linux_JTX1_v1.2.0_64b_JetPack23.run
./ZED_SDK_Linux_JTX1_v1.2.0_64b_JetPack23.run
```

## jetson-inference

```shell
cd ~/src/jetson-inference/
mkdir build
cd build
cmake ../
make
```

## Build OpenKAI

```shell
cd ~/src/OpenKAI
mkdir build
cd build
cmake ../
make all -j4
```

## Run samples

```shell
cd ~/src/OpenKAI/build
sudo ./OpenKAI /home/ubuntu/src/OpenKAI/kiss/apmCopter.kiss
```

"apmCopter.kiss" part is the configuration script for each OpenKAI application, replace it to your own kiss file.


