FROM arm64v8/ubuntu:jammy

SHELL ["/bin/bash", "-c"]

# Set the environment to non-interactive
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update -q && \
    apt-get install -y apt-utils

RUN rm /etc/apt/apt.conf.d/docker-clean

ARG ROS_DISTRO=humble
ARG INSTALL_PACKAGE=desktop

RUN apt update -q && \
    apt install -y curl gnupg2 lsb-release  && \
    curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/ros2.list > /dev/null && \
    apt-get update -q && \
    apt-get install -y ros-${ROS_DISTRO}-${INSTALL_PACKAGE} \
    python3-argcomplete \
    python3-colcon-common-extensions \
    python3-rosdep python3-vcstool
    
RUN apt-get update && apt-get install -y net-tools \
    iputils-ping\
    snapd \
    git \
    tmux \
    vim \
    nano \
    wget \
    software-properties-common \
    python3-pip && \
    python3 -m pip install transforms3d websocket-client catmux distro && \
    rosdep init && \
    rm -rf /var/lib/apt/lists/* 

RUN apt-get update -q && \
    apt-get install -y \
    ros-humble-tf-transformations \
    ros-humble-turtlebot3 \
    ros-humble-turtlebot3-msgs \
    ros-humble-gazebo-msgs \
    ros-humble-laser-proc \
    ros-humble-ros-ign-bridge \
    ros-humble-rqt* \
    ros-humble-controller-interface \
    ros-humble-effort-controllers \
    ros-humble-joint-trajectory-controller \ 
    ros-humble-robot-localization \ 
    ros-humble-ros2-control \ 
    ros-humble-ros2-controllers \
    ros-humble-pointcloud-to-laserscan && \ 
    echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

RUN add-apt-repository ppa:borglab/gtsam-release-4.1 && \
     apt install -y libgtsam-dev libgtsam-unstable-dev

RUN apt-get update -q && \
    apt-get install -y \
    ros-humble-rosidl-generator-dds-idl \ 
    ros-humble-rmw-cyclonedds-cpp \
    ros-humble-pcl-conversions \
    ros-humble-rmw-cyclonedds-cpp \
    ros-humble-pcl-ros

RUN git clone https://github.com/Livox-SDK/Livox-SDK2.git && \
    cd ./Livox-SDK2 && \
    mkdir build  && \
    cd build && \
    cmake .. && make -j && \
    make install && \
    cd ../.. && \
    rm -rf Livox-SDK2

RUN apt-get update && apt-get install -y net-tools \
    libpcap-dev
 