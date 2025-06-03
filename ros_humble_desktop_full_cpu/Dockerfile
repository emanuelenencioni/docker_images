# This is an auto generated Dockerfile for ros:ros-core
# generated from docker_images_ros2/create_ros_core_image.Dockerfile.em
FROM osrf/ros:humble-desktop-jammy
ENV WAYLAND_DISPLAY=wayland-0
# install ros2 packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    ros-humble-desktop-full=0.10.0-1* \
    && rm -rf /var/lib/apt/lists/*

RUN apt update && apt install -y qtwayland5 iputils-ping ros-humble-apriltag vim htop tmux wget
#per le app qt5 software-properties-common python3-colcon-clean
RUN apt install -y software-properties-common python3-colcon-clean ros-humble-v4l2-camera
# setup entrypoint
#COPY ./ros_entrypoint.sh /


ARG USERNAME=emanuele
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid "$USER_GID" "$USERNAME" \
    && useradd --uid "$USER_UID" --gid 1000 -m "$USERNAME" \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo "$USERNAME" ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/"$USERNAME" \
    && chmod 0440 /etc/sudoers.d/"$USERNAME"

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME
RUN cd && git clone https://github.com/emanuelenencioni/config.git && mv config/.bash_profile .\
    && cat config/.bashrc >> .bashrc && mv config/.tmux.conf .
RUN cd && echo "source /opt/ros/humble/setup.bash" >> .bashrc
ENTRYPOINT ["/ros_entrypoint.sh"]
CMD ["bash"]


