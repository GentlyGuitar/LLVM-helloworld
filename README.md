### The simplest llvm tutorial you can ever find on Internet!

This tuturial shows you how to compile llvm and clang, and how to run a simple llvm pass, **all in one minute**.

## Prerequisites

- GNU Make        3.79, 3.79.1    Makefile/build processor
- GCC >=4.8.0     C/C++           compiler1
- python          >=2.7           Automated test suite2
- zlib            >=1.2.3.4       Compression library3

## Build Clang and LLVM

The repo already has both llvm and repo, so you can directly go build it.

```bash
$ cd build
$ cmake -G "Unix Makefiles" ../llvm # you might need to use cmake3, if your cmake is cmake 2.x
$ make
```

Try clang (assume you are still in build/):

```bash
$ ./bin/clang --help
$ ./bin/clang hello/hello.c -o hello/hello  # compile the C file into a native executable
$ ./bin/clang -O3 -emit-llvm hello.c -c -o hello.bc  # compile the C file into an LLVM bitcode file
```

Run the program in both forms

```bash
$ ./hello/hello
$ ./bin/lli ./hello/hello.bc
```

## Write a Simple Pass

Go to directory llvm-pass-skeleton/

```bash
$ cd ../llvm-pass-skeleton
$ mkdir build
$ cd build
$ LLVM_DIR=../llvm/build/lib/cmake/llvm/ cmake ..
$ make  # build the pass.
```

```bash
$ cd ..  # go to project root directory
$ llvm/build/bin/clang -Xclang -load -Xclang llvm-pass-skeleton/build/skeleton/libSkeletonPass.* build/hello/hello.c
I saw a function called main!
```

That -Xclang -load -Xclang path/to/lib.so dance is all you need to load and activate your pass in Clang.

Congrats! You've just hacked a compiler! 

## Credits

This tutorial is based on llvm and clang's [introduction](http://clang.llvm.org/get_started.html) document and Dr. Sampson's [blog](http://www.cs.cornell.edu/~asampson/blog/llvm.html)