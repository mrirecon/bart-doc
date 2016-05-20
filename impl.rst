Software Implementation
========================


Memory-mapped Input/Output
----------------------------


Input and output is performed using memory-mapped files.
This allows efficient access to small parts of a large
file, e.g. a slice of a 3D data set.

The use of memory-mapped input/output allows simple processing of
extremely large data sets. While all data can be accessed simply,
either directly with points or using the functions of the library,
only the parts of the data which are actually accessed are loaded
into memory. 

It is also possible to access data during long-running computations
or debugging stops. 


Multi-Dimensional Arrays
------------------------

Multi-dimensional arrays are part of almost every framework for image reconstruction. A set of functions is provided for basic addressing/indexing, mathematical operations, and some transforms. It offers simple but powerful interfaces for many operations on multi-dimensional arrays, e.g. to access slices of an array or to apply an FFT along selected dimensions.


GPU Acceleration
-----------------


Most operations can be transparently accelerated using GPUs.
Data can be allocated on the GPU using:


The generic copy function ``md_copy`` can be used to copy data
from on to the GPU. Basic operations, FFT, ... are
implemented for the CPU and GPU. The library keeps track
of all allocated memory regions and automatically
uses the right function.


