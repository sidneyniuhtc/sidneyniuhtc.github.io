# Wrtie CMake

## Recommand Datas

###  Docs
[CMake official Documentation](https://cmake.org/cmake/help/latest/index.html)

### Videos
★★★☆☆ [CppCon 2017: Mathieu Ropert “Using Modern CMake Patterns to Enforce a Good Modular Design”](https://www.youtube.com/watch?v=eC9-iRN2b04)
  
★★★★★ [C++Now 2017: Daniel Pfeifer “Effective CMake"](https://www.youtube.com/watch?v=bsXLMQ6WgIk)

★★★★★ [CppCon 2018: Mateusz Pusz “Git, CMake, Conan - How to ship and reuse our C++ projects”](https://www.youtube.com/watch?v=S4QSKLXdTtA)

★★★★☆ [More Modern CMake - Deniz Bahadir - Meeting C++ 2018](https://www.youtube.com/watch?v=y7ndUhdQuU8)

★★★★★ [Deep CMake for Library Authors - Craig Scott - CppCon 2019](https://www.youtube.com/watch?v=m0DwB4OvDXk)


## Basic concepts of CMake codes

The entry point of cmake project is **CMakeLists.txt**.  
That is, you need to cmake on the folder who obtain **CMakeLists.txt**.  

All cmake variables, functions, data.... are strings.  
That is, the codes will be expand, just like macro.  

Conventionally, major cmake variables use **UPPER_CASE**, such as CMAKE_CXX_FLAGS_DEBUG, PROJ_INCLUDE_DIRS, etc.  

The cmake funtion has two major class, multi-command funtion and single command.  
The single command format is funtion(paramater1, paramater2, paramater3.....).  
For example, if we want to set a flag of debug, we can do this:
```
set(CMAKE_CXX_FLAGS_DEBUG "-g")

```
However, this will cause we override the variable with new data.  
If we want to append, we can use this method:
```
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g")
```
**${VARIABLE}** is the method to get the data of variable, which is all string as mentioned before.

Moreover, The debug method is use **message()** built-in function.  
For example, if we want to print the variable of CMAKE_CXX_FLAGS_DEBUG,  
we can do this:
```
message("CMAKE_CXX_FLAGS_DEBUG is ${CMAKE_CXX_FLAGS_DEBUG}")

```

## Let start our first cmake project.

First, you need to assign minum cmake version to avoid old features.  
Thus, the first line usually is 
```
cmake_minimum_required(VERSION 3.5)
```

There are two comment format:
```
# one line use sharp symbol


#[[ multiline 
    use bracket ]]
```

and add our first code of cmake project

```
set(FIRST_STRING "Hello")
set(SECONT_STRING "CMake!!")

message("${FIRST_STRING} ${SECONT_STRING}")
```

And run with the command we learn at [overview](../../0.%20Overview#why-we-need-cmake-1)

## Example project
[https://github.com/sidneyniuhtc/00HelloCMake.git](https://github.com/sidneyniuhtc/00HelloCMake.git)

<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/00%20Basic%20Concept/linux.png"/>
<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/00%20Basic%20Concept/windows.PNG"/>

[Upper Layer](../../)