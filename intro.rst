Introduction
============

Overview
--------

BART is a free and open-source image-reconstruction framework for Computational Magnetic Resonance Imaging. It consists of a programming library and a toolbox of command-line programs.

.. The BART library provides common operations on multi-dimensional arrays, Fourier and wavelet transforms, as well as generic implementations of iterative optimization algorithms.

.. The BART tools provide direct access to basic operations on multi-dimensional arrays as well as efficient implementations of many calibration and reconstruction algorithms for parallel imaging and compressed sensing.

This documentation is meant to be a guide for BART usage and development. Since this is hand-written rather than machine generated, some code snippets might be outdated by the time you read them. However, the general idea should remain the same.

If you have any questions about the implementation details or find errors in this documentation, please send them to our mailing list https://lists.eecs.berkeley.edu/sympa/info/mrirecon.

List of Features
----------------

* Basic features
  
  * support for Linux, Mac OS X, and Windows (with Cygwin)
  * multi-dimensional operations on arrays
  * fast non-uniform Fourier Transform (nuFFT)
  * multi-dimensional (divergence-free) wavelet transform
  * parallel computation on multiple cores and with Graphical Processing Units (GPU)
    
* Iterative methods
  
  * Conjugate Gradients (CG)
  * (Fast) Iterative Soft-Thresholding Algorithm (ISTA and FISTA)
  * Alternating Direction Method of Multipliers (ADMM)
  * Iteratively Regularized Gauss-Newton Method (IRGNM)
    
* Calibration methods for parallel MRI
  
  * direct calibration from k-space center
  * Walsh's method
  * ESPIRiT
    
* Reconstruction methods for MRI
  
  * iterative parallel imaging reconstruction: POCSENSE, SENSE
  * compressed sensing and parallel imaging
  * non-linear inverse reconstruction: NLINV (blind multi-channel deconvolution)
  * calibration-less parallel imaging: SAKE (structured low-rank matrix completion)
    
* Regularization (in arbitrary dimensions)
  
  * Tikhonov
  * total variation
  * l1-wavelet
  * (multi-scale) low-rank

Resources for BART
------------------

There are many resources for getting started with BART.

For tutorial-style code demos, please visit the github repository:

    https://github.com/mikgroup/bart-workshop.

The material was presented at the `2016 ISMRM Workshop on Data Sampling & Image Reconstruction <http://www.ismrm.org/workshops/Data16/>`_ as a software demo.

Examples of using BART in MATLAB is available at:

    https://github.com/mikgroup/espirit-matlab-examples


Please direct all questions or comments to our public mailing list:

    mrirecon@lists.eecs.berkeley.edu

    https://lists.eecs.berkeley.edu/sympa/info/mrirecon

Note: This list has a public archive! Please do not send
any confidential information.

Updates and further information can be found here:

    http://mrirecon.github.io/bart/


License
-------

The tools in BART implement various reconstruction algorithms for
Magnetic Resonance Imaging. The software is intended for research use only
and NOT FOR DIAGNOSTIC USE. It comes without any warranty (see `LICENSE <https://github.com/mrirecon/bart/blob/master/LICENSE>`_ for
details).

Please cite the corresponding articles when using these tools.
Some references can be found at the end of this file. The source code might
provide more detailed references, e.g. for specific iterative algorithms.

