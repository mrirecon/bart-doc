Tools
=====
This section focuses on a few main reconstruction tools in BART and details their usage and design.


ecalib
----------

The ecalib tool estimates coil sensitivies using the ESPIRiT calibration method. It takes a Cartesian kspace data with fully-sampled calibration region as input and outputs ESPIRiT sensitivity maps with the same image dimensions as the input kspace. ecalib usage can be as simple as follows::

  bart ecalib kspace sensitivity

The calibration region does not have to be centered in the kspace array. ecalib estimates the center of kspace by looking at the maximum kspace amplitude and extracts the surrounding region as the calibration region.

Non-Cartesian kspace data must first be gridded onto a Cartesian grid and passed to ecalib. For details about gridding, please see the nufft section.


pics
---------
The pics tool performs general parallel imaging and compressed sensing reconstruction. For Cartesian imaging, it takes kspace data and sensitivity maps as inputs and outputs an image dataset. By default, pics performs a SENSE reconstruction using conjugate gradient and can be used as simple as::
  
  bart pics kspace sensitivity image

For non-Cartesian imaging, the trajectory file must be supplied with the flag ``-t``. For example::

  bart pics -t trajectory kspace sensitivity image


nufft
---------
The nufft tool performs non-uniform fast Fourier transform operations.
