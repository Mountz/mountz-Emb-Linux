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
   . sources/poky/oe-init-build-env build_xwayland
```

## Configure build (Other Times)

```
$> . sources/poky/oe-init-build-env build_xwayland
```

## Kickoff Build

```
$> bitbake fsl-image-qt5
```
