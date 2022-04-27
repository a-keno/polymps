# PolyMPS

A C++ code for numerical modelling of free-surface flow :ocean: using Explicit, Weakly Compressible or Incompressible Moving Particle Simulation/Semi-implicit (**MPS**) method. Boundary walls modeled by polygonal mesh (triangles) or particles (walls and dummies).

<img src='/output/dambreak01_movie.gif' width="96%">

## How to cite PolyMPS ?
If you use PolyMPS, please cite the following reference:

Rubens Augusto Amaro Junior, Alfredo Gay Neto and Liang-Yee Cheng, "3D WC-MPS coupled with geometrically nonlinear shell for hydro-elastic free-surface flows", International Journal for Numerical Methods in Fluids. https://doi.org/10.1002/fld.5083

## Forum

On the [PolyMPS Discussions](https://github.com/rubensamarojr/polymps/discussions) page you can ask questions, discuss about simulation issues, share ideas, and interact with other members.

## Requirements

- [GCC (GNU Compiler Collection)](https://gcc.gnu.org)
- [Eigen](http://eigen.tuxfamily.org)
- [libigl](https://github.com/libigl/libigl)
- [JSON for Modern C++](https://github.com/nlohmann/json)

In order to install C++ compiler (GCC) on **windows**, we recommend to install [Cygwin](https://cygwin.com). You can find [here](https://www3.ntu.edu.sg/home/ehchua/programming/howto/Cygwin_HowTo.html) how to install Cygwin. 
The following Packages should be selected during the Cygwin installation:
- automake
- gcc-core
- gcc-fortran
- gcc-g++
- gdb
- libstdc++
- make

Eigen, libigl and JSON for Modern C++ are third party [header-only](https://en.wikipedia.org/wiki/Header-only) libraries, i.e., they do not need to be separately compiled, packaged and installed to be used :heart_eyes:.

## MPS input files

1. **SOLID DOMAIN**: 
- Boundary walls using **triangular meshes**. It is necessary to create a file (extension **.stl**) with informations about the initial geometry.
- Boundary walls using **particles**. Necessary to add one layer of wall particles (material ID = 2) and two layers of dummy particles (material ID = 3) in the **.grid** file.

2. **FLUID DOMAIN**<a id='fluid_input'></a>: it is necessary to create a file (extension **.grid**) with informations about the initial geometry and some numerical and physical parameters:
- First line: **0**
- Second line: **number of particles**
- Next lines in the columns: **material ID** coordinates of particles **X** **Y** **Z** the initial fluid velocities (generally 0.0) **VX** **VY** **VZ** the initial particle pressure (generally 0.0) **P** and presure average (generally 0.0) **PAV**

3. **FOLDERNAMES, FILENAMES, PHYSICAL and NUMERICAL parameters**: it is necessary to create a file (extension **.json**) and set all parameters.

There are some examples in the folder **input**.

## Compile

Code compiled and tested on Windows 7, and Linux CentOS 7 and Ubuntu64.

You can build the project in GNU/Linux using the makefile. Follow these steps (CPU version):

Clone this repository into your system using `terminal in Linux`, and [Git BASH](https://gitforwindows.org/) `or command prompt (cmd) in Windows`
```bash
git clone https://github.com/rubensaaj/polymps.git
```
Go to the folder **polymps**
```bash
cd polymps
```
Now, clone the third party libraries. You must run two commands
```bash
git submodule init
```
to initialize your local configuration file, and 
```bash
git submodule update
```
to fetch all the data from the third party libraries.

Edit the `Makefile` file (if necessary) with a text editor.

Make sure the environment is clean and ready to compile
```bash
make clean
```
Execute make
```bash
make all
```

This should create a binary `main` in folder **bin**

## Run
- LINUX

In the terminal, type
```bash
./bin/main
```
- WINDOWS

You can do this in two ways:

1st way - In the command prompt, type
```bash
bin\main.exe
```
2nd way - Move the *main.exe* from the folder **bin** to the root folder **polymps**. After that, double click on *main.exe*.

## Input
Type the name of the json input file (located in input directory), e.g.

```bash
MpsInputExample
```

## Additional Note
:warning: If the terminal shows an error message at this step, the problem may be related to the input file **dam1610_3D_fluid_lo0p010_mps.grid**. Please, go to the directory **input/grid** and extract the compressed folder **grid.zip** in the grid directory itself. Check if **dam1610_3D_fluid_lo0p010_mps.grid** contains the data mentioned before in [FLUID DOMAIN](#fluid_input). After that, try to run the code again.

## Output
This code writes pvd (header file) and corresponding vtu files as output. Look in the **output** directory.
You can visualize them by open the pvd file with [Paraview](https://www.paraview.org) :eyeglasses:.

## Directories

The PolyMPS contains several files and directories:

| File/Folder | Description |
| --- | --- |
| eigen | library for linear algebra: matrices, vectors, numerical solvers, and related algorithms |
| include | header files |
| input |	simple input examples (json, grid and stl files). Grid files compressed in a folder|
| libigl | geometry processing library |
| json | file that uses human-readable text to store and transmit data objects |
| output |ouput files (pvd, vtu and txt files) |
| src |	source files |
| LICENSE |	MIT License |
| Makefile | set of tasks to compile the program |
| README |text file |

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
