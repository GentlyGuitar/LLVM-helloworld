### The simplest llvm tutorial you can ever find on Internet!

This tuturial shows you how to compile llvm and clang, and how to run a simple llvm pass.

The repo already has both llvm and repo, so you can directly go build it.

## Build Clang and LLVM

```bash
$ cd build
$ cmake -G "Unix Makefiles" ../llvm # you might need to use `cmake3`, if your cmake is cmake 2.x
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
```

## Credit

This tutorial is based on llvm and clang's [introduction](http://clang.llvm.org/get_started.html) document and Dr. Sampson's [blog](http://www.cs.cornell.edu/~asampson/blog/llvm.html)