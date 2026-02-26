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
$> MACHINE=imx8mp-var-dart DISTRO=fslc-xwayland . var-setup-release.sh build_xwayland
```

## Configure build (Other Times)

```
$> source setup-environment build_xwayland
```

## Kickoff Build

```
$> bitbake fsl-image-qt5
```
