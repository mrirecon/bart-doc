Data Format
===========

BART's data format consists of a pair of files: one header file (``.hdr``) and one raw complex float data file (``.cfl``).

The header file (``.hdr``) is a simple text readable file that describes the dimensions of the data. Any line that starts with ``#`` is regarded as comments. For example, a valid data header for a 192-by-128 dataset is::
  
  # Dimensions
  192 128 1 1 1 1

The raw data file (``.cfl``) is a binary file containing a single contiguous block of array data of dimensions described in the header stored in column-major order (first index is sequential). The raw data file is complex float (32 bit real + 32 bit imaginary, IEEE 747 binary32 little-endian).

MATLAB functions to read and write our data files may be found in recon/matlab (readcfl.m and writecfl.m). Python functions to read and write our data files may be found in recon/python (cfl.py). 

Cartesian Datasets
--------------------------------------

For Cartesian MRI data and images, the dimensions are usually assigned in the following order::

    0 readout
    1 phase-encoding dimension 1
    2 phase-encoding dimension 2
    3 receive channels
    4 ESPIRiT maps
    ...
    ...

(more dimensions are defined in src/misc/mri.h)

Undersampled data is stored with zeros in the unsampled positions.


Non-Cartesian Datasets
--------------------------------------

Non-Cartesian datasets are stored in two separate BART datafiles: one kspace coordinates dataset and one non-Cartesian samples dataset . Each datafile consists of a header and a raw data file.


The k-space coordinates for each sample are stored along dimension 0 which must have size equal to three. Dimension 1 stores the samples along a single readout windows while dimension 2 may be used to differentiate between different lines (e.g. radial spokes). Channel (3) and map (4) dimensions must not be used (i.e. have size one), while other dimensions can be used as for Cartesian data.

The dimensions for the kspace coordinates are usually assigned in the following order::

  0   3
  1   readout dimension
  2   Number of TRs
  3   1
  4   1
  ...
  ...

The unit of measurement for kspace trajectory is 1/FOV. For example, a valid kspace trajectory for a 192-by-128 image should be scaled such that the x-coordinates cover the range of -192/2 to 192/2 and y-coordinates cover the range of -128/2 to 128/2.


Non-Cartesian samples are stored in a similar way as trajectories except that dimension 0 is not used. The channel dimension can be used for different receiver coils as usual.

The dimensions for the kspace samples are usually assigned in the following order::

  0   1
  1   readout dimension
  2   Number of TRs
  3   Number of coils
  4   1
  ...
  ...
  
