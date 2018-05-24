# Tasmanian.jl 

[![Build Status](https://travis-ci.com/floswald/Tasmanian.jl.svg?branch=master)](https://travis-ci.com/floswald/Tasmanian.jl)

Wrapping the awesome [tasmanian](https://github.com/ORNL/Tasmanian) library.


## Example 1: The *Darth Vader* Function

Approximating the function at increasing levels of grid refinement at 1000 randomly chosen points.


```julia
julia> using Tasmanian
julia> Tasmanian.ex2()
INFO: error on initial grid:    0.06798, with 13 points
INFO: refinement level 1 error: 0.02096, with 16 points
INFO: refinement level 2 error: 0.00896, with 36 points
INFO: refinement level 3 error: 0.00314, with 80 points
INFO: refinement level 4 error: 0.00097, with 176 points
INFO: refinement level 5 error: 0.00031, with 384 points
INFO: refinement level 6 error: 9.0e-5, with 824 points
INFO: refinement level 7 error: 2.0e-5, with 1688 points
INFO: Saved animation to /Users/74097/.julia/v0.6/Tasmanian/examples/ex2.gif
Plots.AnimatedGif("/Users/74097/.julia/v0.6/Tasmanian/examples/ex2.gif")
```

![](examples/ex2.gif)

## Example 2: Genz test function


![](examples/ex3.gif)


## Checklist

- [x] Basis functionality wrapped: getters, setters
- [x] Simple tests implemented
- [x] `LocalPolynomialGrid` implemented
- [x] grid refinement implemented
- [ ] Automate build of library via `BinDeps`
- [ ] Documentation
- [ ] Other grid types missing: global, sequential and wavelet



## Installation

To install julia package

```julia
Pkg.clone("git@github.com:floswald/Tasmanian.jl.git")
```

The Tasmanian library needs to be manually installed for now.

in terminal, to install the Tasmanian library.
this will install the library into dir `/Applications/TSG`. You need to modify in `src/Tasmanian.jl` the line

```julia
  const TASlib = "/Applications/TSG/lib/libtasmaniansparsegrid.dylib"
```

with the corresponding path for your machine.


```
git clone https://github.com/ORNL/TASMANIAN
cd TASMANIAN
mkdir build
cd build

cmake \
-D CMAKE_INSTALL_PREFIX=/Applications/TSG \
-D Tasmanian_STRICT_OPTIONS=OFF \
-D Tasmanian_ENABLE_BLAS=ON \
-D Tasmanian_ENABLE_PYTHON=ON \
-D Tasmanian_ENABLE_MATLAB=OFF \
-D Tasmanian_ENABLE_FORTRAN=ON \
-D Tasmanian_ENABLE_CUBLAS=OFF \
-D Tasmanian_ENABLE_CUDA=OFF \
-D Tasmanian_ENABLE_MPI=OFF \
-D Tasmanian_SHARED_LIBRARY=ON \
-D Tasmanian_STATIC_LIBRARY=ON \
-D CMAKE_BUILD_TYPE=Debug ..

make
make test
make install
```


