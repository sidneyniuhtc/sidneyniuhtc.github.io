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
Because Windows and Linux have entirely different binary system, there are necessary to write another script to generate build system.  
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
And it is able to build by cmake command.  
```
mkdir build
cd build
cmake ..
cmake --build . 
```

And run on different environment.  
```
PS\> .\a.exe
```

```
[user]$ .\a.out
```

# Why cmake is so difficult?
Although cmake is just a script language without complex types and cmake unified the command for easily using.  
However, there is NO cmake tutorial.  
There is NO systematic  resources.  

for example, when you using old cmake version and old visual studio with x64 and x86
```
mkdir build32
cmake -G "Visual Studio 14" -B build32 -S .
mkdir build
cmake -G "Visual Studio 14 Win64" -B build -S .


```
But at new version of cmake and new vs  with x64
```
cmake -G "Visual Studio 16 2019" -Ax64  -B build -S .

```
And I donot know how to force build x86 lol.


Further, using cmake need to have deeply understanding about OS environment variables such as PATH, or adding XXX_ROOT manully.  
Also you need to have deeply understanding about compiler compile flags such as linking, configurations, settings, etc.  

Debuging cmake is extremely tough.  
Take interpreted language for example, you can just stop at any step for debugging.  
For compiled language, you need debug flag and run after compiling.  
For cmake, you need to generate project on Windows and Linux to try the generator and then debug the compiling process.  
And finally debug the C++ code. This means you should debug entire workflow form layer to layer.  
CMake does not have breakpoint method.  
Moreover, it is difficult to just is the user command issue or developer code issue.  


## Recommend CMake development environment is VSCode
For cross platform development, it is better to choose cross platform Text Editor also such as VSCode.  
But, you still need to install visual studio 2019 for their compiler and libraries.  


Main: [Upper Layer](../), 
Next: [Use CMake Project](../1.%20Use/)
