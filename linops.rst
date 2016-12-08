Linear Operators
================

.. _linop:

``linop`` interface
--------------------

The ``linop`` interface provides an abstraction for linear operators. For each ``linop`` A, it supports forward operation, adjoint operation and normal operation.


``linop_chain``
---------------

The ``linop_chain`` function is arguably the most powerful feature of the ``linop`` interface.
Given two linops A and B, the composite linear operator A(B) can be chained together by doing::
  
  AB = linop_chain(A, B)

This automatically chains the adjoint operation, and normal operation.

``fft``
--------

``fft`` implements the fast Fourier transform using the FFTW library for CPU and cudaFFT for GPU.


``nufft``
----------

``sense``
---------

``wavelet``
-------------

``finite_diff``
---------------
