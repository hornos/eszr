# ESZR module environment

ESZR is a [Modules](http://modules.sourceforge.net/) based environment for HPC users.

## What problem does it solve ?
You can modify your shell environment by loadable modules.

## Install
Install via git:

```bash
cd $HOME
mkdir site
cd site
git clone git://github.com/hornos/eszr.git
```

## Setup in .profile
```bash
module use ${HOME}/site/eszr/mod/common
module use ${HOME}/site/eszr/mod/local
module load eszr/local
module load eszr/sys/local/osx
# or
# module load eszr/sys/local/ubuntu
```

Put your modules (copy from mod/site) to mod/local.
