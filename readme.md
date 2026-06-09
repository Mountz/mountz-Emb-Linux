# README

Repo manifest for OE/Yocto environment integrating meta-argus


## Repo Init

```
$> repo init git@github.com:Mountz/mountz-Emb-Linux.git
```

## Repo Sync
```
$> repo sync -j 8
```

## Configure build (1st Time)

```
$> TEMPLATECONF=${PWD}/sources/meta-argus-apps/conf/templates/argus \
   . sources/poky/oe-init-build-env build_xwayland > /dev/null
```

## Configure build (Other Times)

```
$> . sources/poky/oe-init-build-env build_xwayland > /dev/null
```

## Kickoff Build

```
$> bitbake fsl-image-qt5
```

## Docker Yocto Builder

The recommended Docker-based build environment is provided by the
`argus-yocto-docker-builder` repository. The builder container should be run
against a separate Yocto build/workspace directory, not this manifest repository
checkout.

Clone the builder next to this manifest repository:

```
$> cd ..
$> git clone git@github.com:Mountz/argus-yocto-docker-builder.git
```

Build the Docker image used by the builder:

```
$> cd argus-yocto-docker-builder
$> ./build-container.sh
```

Start the builder and pass it the path to the Yocto build/workspace directory:

```
$> ./run-yocto-builder.sh ../var-fslc-yocto-build-Jun9
```

The directory argument is the host directory mounted into the container as
`/home/yocto/yocto`. If the directory already exists, the builder starts in that
existing workspace, which supports rebuilding and repo updates. If the directory
does not exist, `run-yocto-builder.sh` prompts before creating it.

Inside the container, initialize or sync the source repositories, configure the
Yocto environment, and build the image:

```
$> init-and-sync-repos.sh
$> yocto-env build_xwayland
$> build-image.sh fsl-image-qt5
```

The container mounts the workspace from the host, so source files and build
outputs persist after exiting the container. It also reuses the host SSH and Git
configuration so private repository access works the same way it does on the
host.

For the full builder documentation, see:

```
../argus-yocto-docker-builder/readme.md
```
