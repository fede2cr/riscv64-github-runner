# riscv64-github-runner
Docker recipe for a riscv64 GitHub local runner

GitHub has popularized using CI/CD within the platform with ease, and they provide VMs from different Linux distributions as well as Windows and MacOS, and even provide different architectures like x86-64 and arm64, so that software can be compiled and tested natively (without using cross compilers). This is of course quite beneficial for free software projects that want to both test, and release binary versions of their software.

Yet, GitHub does not provide at the time with RISC-V 64 bit architecture VMs. What this project tries to do, is to share documentation, docker containers and recipes on how to use and run CI/CD pipelines with GitHub under several distributions.

If you are a RISC-V Lab and want to use this methods, please got a bit below in this document to find instructions on how to run a runner.

If you are a software project that requires a GitHub local runner with a RISCV64 architecture, please follow this steps.

## Instructions for setting up a RISCV64 CI/CD pipeline with GitHub

1. Contact a RISC V Lab. You can use the [Costa Rica RISCV Lab](https://github.com/fede2cr/CR-RISCV-Lab) (unofficial lab) or the first official lab which is [10x Enginners](https://riscv.org/risc-v-lab-partner/). Let them know what your project will be working on, how frequent will you run workloads, and how big are those workloads.

2. Setup a GitHub CI/CD action like you can find in the [example](doc/CI-example.md) or follow the more complex example of projects that build [Python wheel packages](https://github.com/fede2cr/riscv64-python-whl) on RISCV64 or that build [KDE9](https://github.com/fede2cr/riscv64-kde9-compiler) on RISCV64.

3. Create a key for your runner in GitHub. You may request multiple runner keys to your RISCV Lab by running this step multiple times. This should allow you to run on multiple hardware if your project is big enough to require it.

In GitHub, go to your project, and on the top menu, click on Settings.

![GitHub top menu, click on Settings](doc/imgs/github-menu.png)

## Instructions for setting up runners, for a RISCV Lab

## Distribution images

This is the current list of distributions supported. Please take a look at the FAQ below if you require other distributions or packages to be added.

|Distribution|Version|Docker Hub Link|Image short name|Source|
|------------|-------|---------------|----------|------|
|Ubuntu|22.04|[github-runner-ubuntu](https://hub.docker.com/r/fede2/github-runner-ubuntu)|fede2/github-runner-ubuntu|[ubuntu-runner/](ubuntu-runner/)|


## FAQ

- I want to use a distribution but is not on this list, can you please provide docker images for that particular distribution?

Yes, please create an issue stating what distribution and what version do you need and we will work on it.

- Is the software in this VMs, exactly what I would find on a GitHub VM?

No it is not, but it can be. If you are missing any obvious software from the images you would need to install it via apt-get/dnf for not, but also create an issue and let us know which software is it, to review if it makes sense to add it to the base images.

- Does the VMs get clean every time there is a new action sent to the runner?

This is very easy as they are docker images, but it is not happening as the current runner software does not exit after a failure or completion. This is a priority for this project and we hope to work on it very soon.

- Docker, podman, firecracker?

This currently works on both docker and podman. We hope to test firecracker images very soon.
