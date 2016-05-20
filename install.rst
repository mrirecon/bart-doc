.. highlight:: rst

Installation
============

Prerequisites
------------------

BART requires the GCC compiler, the FFTW library, and optionally CUDA for NVIDIA GPU computing.
(see recon/Makefile to turn options on or off)

The software can be used in combination with Matlab, python or octave.


There is limited support for reading Cartesian data encoded with
the ISMRM Raw Data format when linking with the ISMRMRD library (version 0.5.2)
(http://ismrmrd.sourceforge.net/).


In the following, the symbol '$' indicates a shell prompt.
Do not type '$' when entering commands.



Linux
------------------

BART runs on any recent Linux distribution.

To install the required libraries on Debian and Ubuntu run::

    $ sudo apt-get install gcc make libfftw3-dev liblapacke-dev libpng-dev

    (optional)
    $ sudo apt-get install octave

    (optional)
    install version 0.5.2 of the ISMRMRD library



Mac OS X
------------------

Xcode command line tools are required and can be installed by running::

    $ xcode-select --install

We recommend installing a newer version of gcc (4.7 seems to work) from MacPorts (http://www.macports.org/). To install the required libraries, run::

    $ sudo port install fftw-3-single
    $ sudo port install gcc47
    $ sudo port install libpng

    (optional)
    $ sudo port install octave

    (optional)
    install version 0.5.2 of the ISMRMRD library



Windows
------------------

You can use BART on Windows using Cygwin:

https://www.cygwin.com/

Install Cygwin and select the following packages::

    Devel: gcc, make
    Math: fftw3, fftw3-doc, libfftw3-devel, libfftw3_3
    Math: liblapack-devel, liblapack-doc, liblapack0
    Libs: libpng, libpng-devel


Then use the cygwin shell to compile BART as described below.


An alternative to using Cygwin is a virtual machine with Linux.



Downloading and Compilation
--------------------------------

If you are a git user, you can simply clone our public repository::

    $ git clone https://github.com/mrirecon/bart


Otherwise, please download the latest version as a zip file
from Github:

    http://github.com/mrirecon/bart/releases/latest

and unpack it somewhere on your computer.


Open a terminal window and enter the bart directory (the top-level
directory with the Makefile in it). To build the reconstruction
tools type::

    $ make


If you have installed the ISMRMRD library version 0.5.2, you can also
build the ISMRM raw data import tool::

    $ make ismrmrd
