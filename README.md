# docker-vdbench

The docker-vdbench project can be used to create 2 docker images for testing specific scenarios using vdbench within containers.

 The first scenario builds a container to run vdbench in interactive mode using the rsh argument. The second scenario creates a container that has vdbench installed but does not execute a command. See run instructions below.

There are 2 Dockerfiles in subfolders to help with the construction of the specific containers, vdbench-interactive and vdbench-host.

### Requirements:

Download the version of vdbench that you want to use (eg. vdbench50407.zip)

### Build instructions:

```
> git clone https://github.com/mmoore71/docker-vdbench
> cd docker-vdbench
> unzip ~/Downloads/vdbenchxxxxx.zip -d vdbench
> cp -r vdbench vdbench-interactive
> cp -r vdbench vdbench-host
> rm -rf vdbench

> cd vdbench-interactive
> docker build --rm -t docker-vdbench:vdbench-interactive .
> cd ../vdbench-host
> docker build --rm -t docker-vdbench:vdbench-host .
> cd ..

> docker images
REPOSITORY                TAG                   IMAGE ID       CREATED         SIZE
docker-vdbench   vdbench-host          d2488d8f3d7f   17 hours ago    416MB
docker-vdbench   vdbench-interactive   ba0f1905898b   17 hours ago    416MB
```

After the containers are built you can publishing then to a repository of your choice.

### Docker run instructions:

Running the vdbench-interactive container launches vdbench rsh where it will wait for connections. Exit the container by typing `Ctrl-c`.
```
> docker run docker-vdbench:vdbench-interactive
```
Running the vdbench-host container with -it launches the container, cd's the vdbench folder, and will sit awaiting instructions in bash. Exit the container by typing `exit` in the bash shell.

```
> docker run -it docker-vdbench:vdbench-host
```

### Docker pull or run from Docker hub (optional):
If you don't want to build the images I have posted them on dockerhub.
```
> docker pull mmoore71/docker-vdbench:vdbench-interactive

> docker pull mmoore71/docker-vdbench:vdbench-host 

> docker images
REPOSITORY                TAG                   IMAGE ID       CREATED         SIZE
mmoore71/docker-vdbench   vdbench-host          d2488d8f3d7f   17 hours ago    416MB
mmoore71/docker-vdbench   vdbench-interactive   ba0f1905898b   17 hours ago    416MB
```
Or, you can just run the comtainers and they will download from docker hub automatically.
```
> docker run mmoore71/docker-vdbench:vdbench-interactive
19:45:18.376 Vdbench rsh daemon: waiting for new users
```
Kill it with Ctrl-c

```
> docker run -it mmoore71/docker-vdbench:vdbench-host
bash-4.2# pwd
/vdbench
bash-4.2# ls
aix            example1  example4  example7  linux       solaris         vdbench      vdbench.pdf
build_sds.txt  example2  example5  examples  mac         solx86          vdbench.bat  windows
classes        example3  example6  hp        readme.txt  swatcharts.txt  vdbench.jar
bash-4.2#
```

Stop the container by exiting the bash shell

```
> exit
```
