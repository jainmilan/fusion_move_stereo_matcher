# fusion_move_stereo_matcher
FMSM (Fusion Move Stereo Matcher) is an implementation of fusion move algorithm and QBPO minimization in the existing code which can be downloaded from http://vision.middlebury.edu/MRF/code/. Here you can find the faster implementations of the global methods (graph cuts and belief propagation) which are part of their MRF library. Here is C++ source code for MRF minimization and all benchmarks. The code in the first 3 files compiles with gcc 4 under linux and cygwin on 64-bit machines. 64-bit code is are assumed by default; edit the Makefile for 32-bit machines. QPBO code was available from http://pub.ist.ac.at/~vnk/software.html. You can use http://www.iiitd.edu.in/~chetan/teaching/pgm-winter-15/assignment-1.pdf to download actual copy of the assignment. 

We updated the code with the implementation of fusion move algorithm for stereo matcher problem as part of an assignment for PGM (Probabilistic Graphical Model) course offered by Dr. Chetan Arora in IIIT Delhi. Existing code had maxflow and graph cut implemented but fusion move includes submodular terms, therefore we have also implemented QPBO to find out min cut and energy minimization.

1. imageLib: Library which works on image files and remains untouched for current implementation.
2. MRF: Library to implement markov random field and includes faster implementations of the global optimization methods. Both QPBO algorithm and fusion move algorithm was implemented in this library. Files required to be updated are: Makefile(to include QPBO code), GCOptimization.cpp, GCOptimization.h(to implement fusion move and QPBO graph cut)
3. mrfstereo: Library to use MRF library for stereo matcher problem. Includes various parameters which can be used to tweak settings for running the algorithm. mrfstereo.cpp need to be updated to include option to execute fusion move algorithm.

To execute the code:
1. cd imageLib
2. make
3. cd ../MRF
4. make
5. cd ../mrfstereo
6. make
7. ./mrfstereo ./tsukuba/scene1.row3.col1.ppm ./tsukuba/scene1.row3.col5.ppm ./tsukuba/tsukuba.png

