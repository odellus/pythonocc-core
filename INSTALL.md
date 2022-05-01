Overview
--------

pythonOCC is a python library whose purpose is to provide 3D modeling features.
It's intended to
developers who aim at developing a complete CAD/PLM application, and to
engineers who want to have a total control over the data during complex design
activities.

About this document
-------------------

This file explains how to build pythonocc-core from source on Windows, Linux or
MacOSX platforms.

Requirements
------------

pythonOCC needs the following libraries or programs to be installed before you
can compile/use it :

*   the python programming language (<http://www.python.org>). Python 3.x is required. Python 2
is officially dropped since the release 7.5.0.

*   OpenCascade 7.5.3 (<https://dev.opencascade.org>), direct source download at https://git.dev.opencascade.org/gitweb/?p=occt.git;a=snapshot;h=fecb042498514186bd37fa621cdcf09eb61899a3;sf=tgz

    IMPORTANT: OpenCASCADE has to be compiled using flag -D BUILD_RELEASE_DISABLE_EXCEPTIONS=OFF

*   SWIG 3.0.11 or higher (<http://www.swig.org>),

Optional
--------

If you want to benefit from a 3D graphical rendering, you will need a GUI manager, e.g. PyQt, PySide or wxPython.

Create a local copy of the repository
-------------------------------------

    git clone git://github.com/tpaviot/pythonocc-core.git

pythonocc-core compilation
--------------------------

    cd pythonocc-core
    mkdir cmake-build
    cd cmake-build

The configuration steps uses cmake:

    cmake ..
By default, cmake looks for oce include headers in /usr/local/include/oce and
libraries in /usr/local/include/lib. If these paths don't match your
installation, you have to set OCE_INCLUDE_PATH and OCE_LIB_PATH:

    cmake -DOCE_INCLUDE_PATH=/your_oce_headers -DOCE_LIB_PATH=/your_lib_dir ..

And launch the build process

    make

If you have many cpus, you can increase the compilation speed with:

    make -j$ncpus

According to your machine/os/ncpus, the total compilation time should be around 15 minutes.

Then

    make install

You may require admin privileges to install

    sudo make install

test
----
In order to check that everything is ok, run the pythonocc unittest suite:

    cd ../test
    python run_tests.py

demos
-----
Download/test demos available at <https://github.com/tpaviot/pythonocc-demos>
