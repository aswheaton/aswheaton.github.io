---
layout: post
title: Recipe for Installing BAGPIPEs on Ubuntu 20.04 LTS
date: 2020-10-14
tag: Astronomy
author: Alexander S. Wheaton
categories: ["Astronomy"]
image:
---

This week I had to get the [Bagpipes](https://github.com/ACCarnall/bagpipes) [(docs)](https://bagpipes.readthedocs.io/en/latest/#) Python module up and running for work on my thesis. BAGPIPEs relies on PyMultiNest, a Python API for the MultiNest algorithm. PIP pulls in PyMultiNest when installing BAGPIPEs, but this requires that the MultiNest library already be installed on your system. There are [several](https://github.com/JohannesBuchner/MultiNest) [pieces](http://johannesbuchner.github.io/pymultinest-tutorial/install.html#on-your-own-computer) of [documentation](https://github.com/DarkMachines/pyBAMBI/wiki/MultiNest-installation) surrounding this, all of which provide conflicting information on how to get it right. If your search engine has led you this deep, here is my take, to confuse or clarify:

In summary, Bagpipes needs PyMultiNest which needs the MultiNest library which finally relies upon the lapac linear algebra library. Fortunately, there is a version of this in the Ubuntu repositories; you need it and the development version as well. You'll also need cmake and a FORTRAN compiler to build the library. Install lapac and other dependencies for MultiNest:

```bash
sudo apt install libblas{3,-dev} liblapack{3,-dev} libatlas{3-base,-base-dev} cmake gfortran
```

PyMultiNest docs [here](https://johannesbuchner.github.io/PyMultiNest/install.html) say you also need `build-essentials` but I didn't find this to be necessary. Clone the MultiNest repository and build:

```bash
git clone https://github.com/JohannesBuchner/MultiNest
cd MultiNest/build
cmake ..
make
sudo make install
```

PyMultiNest needs to know where to find the newly compiled library, so set the LD_LIBRARY_PATH environment variable to include libmultinest.so:

```bash
export LD_LIBRARY_PATH=/usr/local/lib/:$LD_LIBRARY_PATH
```

If you don't want to do this every time you open a new Terminal, copy the line above into `~/.bashrc` so that this is done with every new bash instance. Get all the required Python 3 dependencies and PIP3, if you don't already have them (also PIP should pull dependencies in with Bagpipes):

```bash
sudo apt install python3-scipy
sudo apt install python3-pip
```

Install BAGPIPEs from the PIP repositories:

```bash
pip3 install bagpipes
```

You can now import bagpipes by convention:

```python3
python3
>>> import bagpipes as pipes
```

A failed import looks something like:

```python3
ERROR:   Could not load MultiNest library "libmultinest.so"
ERROR:   You have to build it first,
ERROR:   and point the LD_LIBRARY_PATH environment variable to it!
ERROR:   manual: http://johannesbuchner.github.com/PyMultiNest/install.html

ERROR:   Could not load MultiNest library: libmultinest.so
ERROR:   You have to build MultiNest,
ERROR:   and point the LD_LIBRARY_PATH environment variable to it!
ERROR:   manual: http://johannesbuchner.github.com/PyMultiNest/install.html

problem: libmultinest.so: cannot open shared object file: No such file or directory
Bagpipes: PyMultiNest import failed, fitting will be unavailable.
```

In this event, check that `/usr/local/lib/libmultitest.so` actually exists and if not, rebuild the library. Once successful, you can remove the MultiNest source:

```bash
rm -rf ~/MultiNest
```
Or you can leave it there to pull new updates and rebuild the library (these don't come often).
