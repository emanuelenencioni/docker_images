# This is an auto generated Dockerfile for ros:ros-core
# generated from docker_images_ros2/create_ros_core_image.Dockerfile.em
FROM osrf/ros:humble-desktop-jammy
ENV WAYLAND_DISPLAY=wayland-0
# install ros2 packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    ros-humble-desktop-full=0.10.0-1* \
    && rm -rf /var/lib/apt/lists/*

RUN apt update && apt install -y qtwayland5 iputils-ping ros-humble-apriltag vim htop tmux #per le app qt5
# setup entrypoint
#COPY ./ros_entrypoint.sh /
RUN cd && git clone https://github.com/emanuelenencioni/config.git && mv config/.bash_profile . && cat config/.bashrc >> .bashrc && mv config/.tmux.conf .

#source the ros system env
RUN cd && echo "source /opt/ros/humble/setup.bash" >> .bashrc


ENTRYPOINT ["/ros_entrypoint.sh"]
CMD ["bash"]


