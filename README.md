# scc
Source code for segmentation and creation of compositional complexity profiles of DNA sequences


UNZIP
=====
Extract scc.zip to an empty folder (on Ubuntu type 'unzip scc.zip' in the desired directory).
You will find:

scc -> Precompiled binary for Ubuntu.

scc.f90, chi.f90 and diver8.f90 -> Main source code and libraries

example_DNA.fa -> Example fasta DNA file

makefile -> Script file for building the program by using 'make'

readme.txt -> This file

INSTALLATION
============

If you are using Ubuntu or any other Debian-based distribution you can simply use the
precompiled binary 'scc'. To use it give it execution permission by typing at command line: 'chmod +x scc'

If you need, or prefer, building the binary, be sure that you are in the folder where you
unziped 'scc.zip' and type 'make'. It should generate an executable called 'scc'.
By default the fortran compiler is set to gfortran. You can change it by changing the first line of the
script makefile. It has been tested for ifort, gfortran and f77 compilers.

CHECK
=====
To check the program type:

./scc example_DNA.fa 0.95 0.95 1

The output should be something like:
#_______________________________________
#_______________________________________
#
# DNA file:          exmple_DNA.fa
# Sequence length             400
# Undefined                     0
# Frecs:                      100         100         100         100
# Total Entropy        2.00000000
#
#_______________________________________
#_______________________________________
#
  0.95000000	  2.00000000	           4
example_DNA.fa	4L	  0.95000000	  2.00000000	           4

and the file segment_sizes.dat should contain:
#	  0.95000000	  2.00000000	           4
           1	         100	         100	         100	           0	           0	           0
         101	         200	         100	           0	         100	           0	           0
         201	         300	         100	           0	           0	         100	           0
         301	         400	         100	           0	           0	           0	         100

You can also check the segmentation with binary alphabets by typing:

./scc example_DNA.fa 0.95 0.95 1 -a 2 RY
./scc example_DNA.fa 0.95 0.95 1 -a 2 SW
./scc example_DNA.fa 0.95 0.95 1 -a 2 KM

The results should be similar but segment_sizes.dat will have 3,2 and 4 segments respectively.

USAGE
=====
If you type 'scc' without arguments you will get a help screen.
The program is intented to segment a DNA sequence at different significance levels so, the minimal parameters required are:
The DNA sequence, the initial significance level (number in [0,1]), final significance level (number in [0,1]) and the number of segmentations:

 USAGE:
     scc <DNA file> <init. sl> <end sl> <# exp.> [options]

If you simply want to segment at a given significance level, e.g. 95% you can type:

scc <DNA file> 0.95 0.95 1

Note that 0.95 corresponds to 95% significance.





