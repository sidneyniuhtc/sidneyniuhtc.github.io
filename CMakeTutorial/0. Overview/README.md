# Why we need CMake

## Interpreted vs Compiled Programming Languages
Interpreted languages such as Python, Javascript, Ruby are able to run directly on their environment.  
However, compiled languages such as C/C++, Java are need to run with compiled file.  

That is, we need a build system to convert codes to a file which is able to run on a computer.  

Generaly, there are three major compilers for compile C++ codes, which are Clang, GCC, MSVC. 
(Actually, these are front-end, all of them support LLVM back-end)  

## Why we need project
If we only has on file, the compiler is easily to compiled a file.  
However, we usually have a bunch of files to generate a executale file or even more complex link.  
We need a concept of management, that is project.  

## What is build system
Because different user has different library versions, we need a general method to find environment setting.  
Further, we want to give projects different compiling settings.  
On Linux, we usually use Makefile.  

## What is GNU Autotools
Because different linux distributions have different system environments, we use to search environment and generate Makefiles automaticly.  
GNU Autotools are GNU Autoconf, GNU Automake, GNU Libtool

## Why we need CMake
Because Windows and Linux have entirely different binary system, there are necessary to write another script to generate build system
For instance, build boost need to run windows script:
```
> .\bootstrap.bat  
> .\b2.exe  
```
But run linux script:
```
$ bash .\bootstrap.sh
```

We wish to write one project generator and runs on different OS.  
CMake is the solution.  

When we have CMake, we donot need to write two script file we can run same commands on both systems:
```
mkdir build
cd build
cmake ..
```

And just build and run project with there own compiler.
```
PS\> MSBuild ALL_BUILD.vcxproj /p:Platform=x64 /p:Configuration=Release
PS\> .\a.exe
```

```
[user]$ make
[user]$ .\a.out
```

[Upper Layer](../)