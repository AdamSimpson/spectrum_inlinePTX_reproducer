# To build

```
$ module list
Currently Loaded Modules:
  1) DefApps   2) python/3.5.2   3) summitdev_tests   4) cmake/3.6.1   5) cuda/8.0.35   6) xl/20161117   7) essl/5.5.0-20161110   8) spectrum_mpi/10.1.0.2
```
```
$ mkdir build
$ cd build
$ CC=gcc CXX=g++ cmake ..
$ make
$ cp ../inlinePTX_kernel.cu . 
```

## Reproduce failure
```
$ mpirun -n 1 ./inlinePTX_nvrtc 
CUDA inline PTX assembler sample
> Using CUDA Device [0]: Tesla P100-SXM2-16GB
> GPU Device has SM 6.0 compute capability
--------------------------------------------------------------------------
mpirun noticed that process rank 0 with PID 0 on node summitdev-c1r0n16 exited on signal 11 (Segmentation fault).
```

## Adding ```-gpu``` works although MPI is not used at all in the code
```
$ mpirun -gpu -n 1 ./inlinePTX_nvrtc 
CUDA inline PTX assembler sample
> Using CUDA Device [0]: Tesla P100-SXM2-16GB
> GPU Device has SM 6.0 compute capability
Test Successful.
```

## Running without mpirun  works
```
$ ./inlinePTX_nvrtc 
CUDA inline PTX assembler sample
> Using CUDA Device [0]: Tesla P100-SXM2-16GB
> GPU Device has SM 6.0 compute capability
Test Successful.
```
