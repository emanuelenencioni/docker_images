# docker_images
#### To build
Go the subdirectory of the specific dockerfile and write the following command:
```bash
docker buildx build -t IMAGE_NAME .
```

To allow docker to access X:
```bash
xhost +local:docker
```
In this way, docker can use Xwayland for compatibility with X11 apps.

Running X11 GUI applications in Docker on a host system that uses Wayland:
```bash
docker container run -it  -v /dev/dri:/dev/dri --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --device /dev/video0 -v path_of_a_volume:path_of_volume_in_containter --name="NAME" --hostname="docker" IMAGE_NAME

```
add `--rm` to delete the container after use.
