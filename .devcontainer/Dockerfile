FROM osrf/ros:humble-desktop

# Installer outils nécessaires
RUN apt-get update && apt-get install -y \
    python3-colcon-common-extensions \
    python3-pip \
    vim \
    git \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Créer un utilisateur "alexdorcival"
ARG USERNAME=alexdorcival
ARG USER_UID=1000
ARG USER_GID=1000

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Définir le workspace par défaut
WORKDIR /root/ros2_ws

USER root

RUN apt-get update && apt-get install -y ros-humble-desktop-full
RUN echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc