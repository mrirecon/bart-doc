Introduction
============
This is the documentation for BART. The Berkeley Advanced Reconstruction Toolbox (BART) is a free and open-source image-reconstruction framework for Computational Magnetic Resonance Imaging. It consists of a programming library and a toolbox of command-line programs. The library provides common operations on multi-dimensional arrays, Fourier and wavelet transforms, as well as generic implementations of iterative optimization algorithms. The command-line tools provide direct access to basic operations on multi-dimensional arrays as well as efficient implementations of many calibration and reconstruction algorithms for parallel imaging and compressed sensing.

This is meant to be a tutorial-like guide to BART usage and development. Since this is a hand-written documentation rather than a auto-gen doc, some parts might be out of date. If you have any questions about the implementation details or find errors in this documentation, please send them to our mailing list https://lists.eecs.berkeley.edu/sympa/info/mrirecon.

License
-------

The tools in BART implement various reconstruction algorithms for
Magnetic Resonance Imaging. The software is intended for research use only
and NOT FOR DIAGNOSTIC USE. It comes without any warranty (see `LICENSE <https://github.com/mrirecon/bart/blob/master/LICENSE>`_ for
details).

Please cite the corresponding articles when using these tools.
Some references can be found at the end of this file. The source code might
provide more detailed references, e.g. for specific iterative algorithms.


Help
-----

Please direct all questions or comments to the public mailing list:

	mrirecon@lists.eecs.berkeley.edu

	https://lists.eecs.berkeley.edu/sympa/info/mrirecon

Note: This list has a public archive! Please do not send
any confidential information.

Updates and further information can be found here:

	http://mrirecon.github.io/bart/
