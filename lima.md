# Lima Cheat Sheet

Lima (Linux virtual machines) which runs virtual machines with some supplementary features on macos.

Lima is able to run docker, containerd containers inside of the virtual machine. Nerdctl (Containerd ctl) is a docker cli compatible ctl for containerd. The containerd engine is available by default if a linux virtual machine is executed. Other container engines like docker, podman, k3s or singularity can be run by configuration (https://github.com/lima-vm/lima/tree/master/examples).

https://github.com/lima-vm/lima

https://github.com/containerd/nerdctl

https://containerd.io/docs/getting-started/

## Lima Basic Commands

`limactl start` - Starts a linux virtua machine

`lima uname -a` - Shows details of the guest virtual machine

`lima nerdctl images` - Shows the available images in the containerd runtime

`lima nerctl pull public.ecr.aws/ubuntu/ubuntu:latest` - Pulls the ubuntu latest image from public ecr repository
