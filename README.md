This is just a mirror for the content at:
 https://people.csail.mit.edu/smcc/projects/single-file-programs/

Large single compilation-unit C programs

When developing research tools that operate on C programs, it is often convenient to ignore the fact that C supports separate compilation, and to develop tools with support only for compiling programs in a single compilation unit; that is, in a single .c file. Unfortunately, the realistic programs on which you would like to test your tool are generally distributed as a number of small .c and .h files. When I faced this dilemma recently, I expended some effort converting versions of several well-known open-source applications into single-file versions. To save other developers the task of doing similar translations, and to encourage the use of freely-available benchmarks, I'm making these programs available here.

These programs have been tested to compile and run with GCC version 3.3.5 on Linux. They haven't gone through the C preprocessor, and they don't include any system header files, so they should be relatively portable, but I haven't made a systematic effort to eliminate all system dependencies, and the header files that result from the configure process are inlined, so some modification would probably be needed for other systems. The programs represent approximately three different decimal orders of magnitude in code size.

#bzip2

bzip2 is the second-most popular lossless compression tool for Linux; it implements the Burrows-Wheeler block sorting transformation and Huffman coding. This is based on version 1.0.2. bzip2.c source code (approx. 200k). Suggested benchmark task: compress the GCC source code below.

#gzip

gzip is a widely used lossless compression tool. This is based on version 1.3.5. gzip.c source code (approx. 260k). Suggested benchmark task: compress the GCC source code below.

#oggenc

oggenc and the libogg and libvorbis libraries implement a command-line encoding tool for Ogg Vorbis, a non-proprietary lossy audio compression scheme (broadly similar to the well known MP3 format). This is based on the 1.0.1 distribution of vorbis-tools. oggenc.c source code (1.7MB). As a freely-redistributable test input, I suggest a WAV file containing the speech that John F. Kennedy gave in Berlin in June 1963: JFK Berlin speech WAV (bzip2 compressed, 28MB).

#gcc

gcc is (here) the GNU project C compiler, a retargetable optimizing compiler that is the standard system compiler for Linux and most other free Unix-compatible OSes. The program here is what would actually be installed as cc1; the main compiler back end which reads in C code (with an integrated preprocessor) and writes out assembly language. This version is configured to compile for Linux on an x86 platform. It's based on a CVS development version from July of 2004, on the development track for what was then planned to be version 3.5.0, and is now known as 4.0.0. On a suitable Linux/x86 system, this compiler can bootstrap itself. gcc.c source code (bzip2 compressed, 3.2MB). Suggested benchmark task: run the compiler on its own source code.

