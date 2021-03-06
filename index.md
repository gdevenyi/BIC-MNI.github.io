---
layout: default
title: BIC-MNI Software repository
---
## Contents:
* [MINC Toolkit](#MINC-Tool-Kit)
  * [MINC Toolkit versions](#notes-about-versions)
  * Version 2 [Version 1.9.17](#v2-version-1917)
  * Version 1 [Version 1.0.09](#v1-version-1009-legacy) *Legacy*
  * [Containers](#containers)
  * [Virtual Machine](#virtual-machine)
  * [Data files and models](#data-files-and-models)
  * [Previous versions](#previous-versions)
  * [Installing](#installing)
    * [On Debian/Ubuntu](#on-debianubuntu)
    * [On CentOS / OpenSuse / Fedora](#on-centos--opensuse--fedora)
    * [On MacOS X 10.8](#on-macos-x-108-and-later)
  * [Using](#using)
  * [Running test suite](#running-test-suite)
  * [Building from the source](#building-from-the-source)
* [Additional software ported to support MINC file format](#additional-software-ported-to-support-minc-file-format)
  * [ITK-SNAP 3.2](#itk-snap-32)


This software repository contains open-source tools developed at the McConnell Brain Imaging Centre, Montreal Neurological Institute
The main documentation site for this repository is located at [wikibooks](https://en.wikibooks.org/wiki/MINC)

Also, concise man pages for various minc tools are located at [bic-mni.github.io/man-pages](http://bic-mni.github.io/man-pages/)

## Support
Contact @vfonov, @andrewjanke, @gdevenyi or @rdvincent if you have any questions

## MINC Tool Kit
This toolkit contains most of the commonly used minc tools in one precompiled 32 and 64bit binary packages of Debian, Ubuntu, RedHat and Mac OS X.
It includes most of the standard minc tools, Display, Register and a  basic image processing pipeline based on the one developed for NIHPD
project (standard_pipeline.pl) Everything is currently installed in ``/opt/minc/VERSION`` , to avoid conflict with standard /usr/local/bic location.

### Notes about versions
* **1.9.XX** - includes the same standard minc-tools as version 1.0.XX, but sometimes with updated parameters (minctracc so far is the only such program).
  Also includes new experimental software based on ITK 4.XX and latest versions of ANTS,Elastix and C3D.
  **Use this version**
* **1.0.XX** - is a legacy version that still includes all the latest versions of the minc tools, and several programs based on ITK 3.20.
  The standard minc-based programs are kept up-to date, but new experimental software is not included. Use this version if you need
  only basic minc tools (i.e register/Display/xdisp) or you are running a legacy image processing pipeline that does not require new tools.

### V2 Version 1.9.17
This version includes ITK-4.13.1, latest version of Elastix, ANTs and C3D - all with minc support. **WARNING** some basic tools produce results incompatible with version 1.00.XX Test-suite will fail due to changes in minctracc
All files will be installed into /opt/minc/1.9.17 in order to co-exist with other versions of minc-toolkit

* 64 bit tools
  * Ubuntu
    * [1.9.17 Ubuntu 19.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Ubuntu_19.04-x86_64.deb)
    * [1.9.17 Ubuntu 18.10](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Ubuntu_18.10-x86_64.deb)
    * [1.9.17 Ubuntu 18.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Ubuntu_18.04-x86_64.deb)
    * [1.9.17 Ubuntu 16.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Ubuntu_16.04-x86_64.deb)
    * [1.9.17 Ubuntu 14.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Ubuntu_14.04-x86_64.deb)
  * Debian
    * [1.9.17 Debian-9.8](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Debian_9.8-x86_64.deb)
    * [1.9.17 Debian-8.11](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Debian_8.11-x86_64.deb)
  * Redhat-based
    * [1.9.17 CentOS 6.10](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.9.17-20190313-CentOS_6.10-x86_64.rpm)
    * [1.9.17 CentOS 7.6](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.9.17-20190313-CentOS_7.6.1810-x86_64.rpm)
    * [1.9.17 Fedora 28](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.9.17-20190313-Fedora_28-x86_64.rpm)
    * [1.9.17 Fedora 29](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.9.17-20190313-Fedora_29-x86_64.rpm)
  * MacOS X
    * [1.9.17 MacOS X 10.10 or later](https://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/minc-toolkit-1.9.17-20180808-Darwin-10.10-x86_64.dmg)
* 32 bit tools **Caveat Emptor** Unfortunately, currently `mincbeast` is unable to run in 32bit mode properly, so `standard_pipelene.pl` will fail
  * Ubuntu , also nu_correct produces different results then 64 bit version
    * [1.9.17 Ubuntu 16.04 or newer](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.17-20190313-Ubuntu_16.04-i686.deb)
* Source code
  * minc-toolkit complete source archive
    * [1.9.17 tar.bz2 archive](http://packages.bic.mni.mcgill.ca/minc-toolkit/minc-toolkit-v2-1.9.17.tar.bz2)

### V1 Version 1.0.09 *legacy*
All files will be installed into /opt/minc/1.0.09 in order to co-exist with other versions of minc-toolkit
* 64 bit tools
  * Ubuntu
    * [1.0.09 Ubuntu 19.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Ubuntu_19.04-x86_64.deb)
    * [1.0.09 Ubuntu 18.10](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Ubuntu_18.10-x86_64.deb)
    * [1.0.09 Ubuntu 18.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Ubuntu_18.04-x86_64.deb)
    * [1.0.09 Ubuntu 16.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Ubuntu_16.04-x86_64.deb)
    * [1.0.09 Ubuntu 14.04](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Ubuntu_14.04-x86_64.deb)
  * Debian
    * [1.0.09 Debian-9.8](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Debian_9.8-x86_64.deb)
    * [1.0.09 Debian-8.11](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Debian_8.11-x86_64.deb)
  * RPM based
    * [1.0.09 CentOS 6.10](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.09-20170529-CentOS_6.10-i686.rpm)
    * [1.0.09 CentOS 7.6](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.09-20170529-CentOS_7.6.1810-x86_64.rpm)
  * [1.0.09 Fedora 28](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.09-20170529-Fedora_28-x86_64.rpm)
  * [1.0.09 Fedora 29](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.09-20170529-Fedora_29-x86_64.rpm)
  * [1.0.09 Fedora 30](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.09-20170529-Fedora_30-x86_64.rpm)
  * MacOS X
    * [1.0.09 MacOS X 10.8](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/minc-toolkit-1.0.09-20170529-Darwin-10.8-x86_64.dmg)
* 32 bit tools **Caveat Emptor** Unfortunately, currently `mincbeast` is unable to run in 32bit mode properly, so `standard_pipelene.pl` will fail (and the test-suite will also fail).
  * Ubuntu
    * [1.0.09 Ubuntu 16.04 or later](https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.09-20170529-Ubuntu_16.04-i686.deb)
  * RPM based
    * [1.0.09 CentOS 6.10](https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.09-20170529-CentOS_6.10-i686.rpm)
* Source code
  * minc-toolkit complete source archive
    * [1.0.09 tar.gz archive](http://packages.bic.mni.mcgill.ca/minc-toolkit/minc-toolkit-1.0.09-20170529.tar.bz2)
* Testsuite (under development)
    * [0.1.3 Debian/Ubuntu](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-testsuite-0.1.3-20131212.deb)
    * [0.1.3 CentOS 6.4](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-testsuite-0.1.3-20131212.rpm)
    * [0.1.3 MacOS X 10.7](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/minc-toolkit-testsuite-0.1.3-20131212.dmg)

### Older Versions
Older packages are archived at https://packages.bic.mni.mcgill.ca/minc-toolkit/Debian for Ubuntu/Debian and https://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/ for CentOS, Fedora and RedHat

### Containers
* Containers based on Ubuntu 16.04 64bit and include  R 3.4.3 + tidyverse + RMINC 1.5.1.0 , python 2.7 + pyminc + pyezminc + minc2_simple, and also standard anatomical models and beast templates installed in `/opt/minc`
  * Docker minc-toolkit-v2 1.9.17: `docker pull nistmni/minc-toolkit:1.9.17`
  * Docker minc-toolkit-v1 1.0.09: `docker pull nistmni/minc-toolkit:1.0.09`
  * Singularity minc-toolkit-v2 1.9.17: `singularity pull --name minc-toolkit-1.9.17.simg shub://vfonov/minc-toolkit-containers:1.9.17`
* Containers without visual tools (Register, Display and ray_trace are missing) and without anatomical models:
  * Docker minc-toolkit-v2 1.9.17: `docker pull nistmni/minc-toolkit-min:1.9.17`
  * Singulatity minc-toolkit-v2 1.9.17: `singularity pull --name minc-toolkit-1.9.17-min.simg shub://vfonov/vfonov/minc-toolkit-containers:1.9.17-min`

### Virtual Machine

A virtual machine containing minc-toolkit, as well as a number of tools built upon it is available for download at [CoBrALab/MINC-VM](https://github.com/CobraLab/MINC-VM)
It is kept up to date with the latest releases of minc-toolkit and additional tools.

### Data files and models
These packages contain anatomical models needed for standard pipeline, all files are installed into `/opt/minc/share`

  * BEaST segmentation library, needed to run mincbeast software for brain extraction
    * [1.1.0 Debian/Ubuntu](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/beast-library-1.1.0-20121212.deb)
    * [1.1.0 CentOS](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/beast-library-1.1.0-20121212.rpm)
    * [1.1.0 MacOS X](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/beast-library-1.1.0-20121212.dmg)
  * bic-mni-models  anatomical template library,  includes models from [ICBM 2009 template](http://www.bic.mni.mcgill.ca/ServicesAtlases/ICBM152NLin2009)
    * [0.1.1 Debian/Ubuntu](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/bic-mni-models-0.1.1-20120421.deb)
    * [0.1.1 CentOS 6.4](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/bic-mni-models-0.1.1-20120421.rpm)
    * [0.1.1 MacOS X 10.7](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/bic-mni-models-0.1.1-20120421.dmg)

### Previous versions

Previous versions are archived in [http://packages.bic.mni.mcgill.ca/minc-toolkit/](http://packages.bic.mni.mcgill.ca/minc-toolkit/)

### Installing

#### On Debian/Ubuntu
* install dependencies: `sudo apt-get install libc6 libstdc++6 imagemagick perl gdebi-core`
* Visualization programs : register, display and ray_trace rely on working OpenGL , install appropriate drivers or software emulation `sudo apt-get install libgl1-mesa-glx libglu1-mesa`
* optional dependency is octave, which is currently used only by xfmavg script.
* download corresponding binary packages
* run `for file in minc-toolkit-<version>.deb minc-toolkit-testsuite-<version>.deb bic-mni-models-<version>.deb beast-library-<version>.deb; do gdebi $file; done`.

#### On CentOS / OpenSuse / Fedora
* install dependencies: `sudo yum install glibc libstdc++ ImageMagick perl`
* install downloaded rpm packages

#### On MacOS X 10.8 and later
* download and double click on  appropriate dmg file, the standard MacOS X installer will start
* install ImageMagick, either using [mac ports](https://www.macports.org/install.php) - preferred or [homebrew](http://brew.sh/)

### Using
* Version **1.0.09 (version 1)**:
   source the environment in `/opt/minc/1.0.09/minc-toolkit-config.sh` for bash or `/opt/minc/1.0.09/minc/minc-toolkit-config.csh` for tcsh
* Version **1.9.17 (version 2)**:
   source the environment in `/opt/minc/1.9.17/minc-toolkit-config.sh` for bash or `/opt/minc/1.9.17/minc-toolkit-config.csh` for tcsh

### Running test suite
**Currently Broken** Test data is installed in `/opt/minc/share/testsuite/`.  To run the test, execute `/opt/minc/run_tests.sh <prefix>`, it will take around
an hour on  a modern PC, the output will be in `<prefix>/00200`  and `<prefix>/00201` and the log file will be saved in
`<prefix>/minc-toolkit-test-<date>.log`.  The results of the local test will be compared to a file containing the results from
a baseline test to determine if the tools have been installed and run correctly.

### Building from the source
Consult [minc-toolkit on github](https://github.com/BIC-MNI/minc-toolkit) or [minc-toolkit-v2 on github](https://github.com/BIC-MNI/minc-toolkit-v2) for details and to download latest version of the software. The binary builds are now built using docker, see all the scripts here: [build_packages on github](https://github.com/BIC-MNI/build_packages)

## Additional software ported to support MINC file format:

### ITK-SNAP 3.2
* MacOS X
  * [MacOS X 10.7 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/third-party/itksnap-3.4.0-20151130-MacOS-x86_64-qt4.dmg) - QT 4 version (doesn't support retina display)
  * [MacOS X 10.11 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/third-party/itksnap-3.4.0-20151130-MacOS-10.11-x86_64-qt5.dmg) - QT 5 version
