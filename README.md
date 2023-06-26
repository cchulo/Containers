# Build Containers

## Description
Personal collection of build containers for setting up cross-compile toolchains.

## Requirements:
- podman
- nvidia-container-toolkit (optional, if running nvidia and would like to render to host from the container)


## GPU-accelerated containers with host-rendering
Some of these are meant for running GPU-accelerated apps that render on the host.

To test your setup, build glxgears-test:

### Note:
You may have to execute `xhost +local:` in case you run into permission errors

### Build:
`podman build -t glxgears-test-linux-x64 -f glxgears-test-linux-x64.Dockerfile`

### Test OpenGL:
`podman run -it --rm --device nvidia.com/gpu=0 -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:ro glxgears-test.ubuntu-20.04-linux-x64:latest "glxgears"`

### Test Vulkan:
`podman run -it --rm --device nvidia.com/gpu=0 -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:ro glxgears-test.ubuntu-20.04-linux-x64:latest "vkcube"`
