FROM ros:humble-perception

ENV WS_DIR="/ros2_ws"
WORKDIR ${WS_DIR}

SHELL ["/bin/bash", "-c"]

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
 && apt-get install -y \
    build-essential \
    cmake \
    git-all \
    software-properties-common \
 && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
 && apt-get install -y curl gpg \
 && mkdir -p /etc/apt/keyrings \
 && curl -sSf https://librealsense.realsenseai.com/Debian/librealsenseai.asc \
    | gpg --dearmor \
    | tee /etc/apt/keyrings/librealsenseai.gpg > /dev/null \
 && echo "deb [signed-by=/etc/apt/keyrings/librealsenseai.gpg] https://librealsense.realsenseai.com/Debian/apt-repo jammy main" \
    | tee /etc/apt/sources.list.d/librealsense.list \
 && apt-get update \
 && apt-get install -y \
    librealsense2-utils \
    ros-${ROS_DISTRO}-librealsense2* \
    ros-${ROS_DISTRO}-realsense2-* \
 && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
 && apt-get install -y \
    ros-${ROS_DISTRO}-rviz2 \
    ros-${ROS_DISTRO}-vrpn \
    ros-${ROS_DISTRO}-vrpn-mocap \
 && rm -rf /var/lib/apt/lists/*

ARG DEBIAN_FRONTEND=dialog
