# Write CMake codes

## Recommand Reading Datas

###  Docs
[CMake official Documentation](https://cmake.org/cmake/help/latest/index.html)

### Videos
★★☆☆☆ [CppCon 2017: Mathieu Ropert “Using Modern CMake Patterns to Enforce a Good Modular Design”](https://www.youtube.com/watch?v=eC9-iRN2b04)
  
★★★★★ [C++Now 2017: Daniel Pfeifer “Effective CMake"](https://www.youtube.com/watch?v=bsXLMQ6WgIk)

★★★★☆ [CppCon 2018: Mateusz Pusz “Git, CMake, Conan - How to ship and reuse our C++ projects”](https://www.youtube.com/watch?v=S4QSKLXdTtA)

★★★★☆ [Meeting C++ 2018: More Modern CMake - Deniz Bahadir](https://www.youtube.com/watch?v=y7ndUhdQuU8)

★★★★★ [CppCon 2019: Deep CMake for Library Authors - Craig Scott](https://www.youtube.com/watch?v=m0DwB4OvDXk)


## Basic concepts of CMake codes

The entry point of cmake project is **CMakeLists.txt**.  
That is, you need to cmake on the folder who obtain **CMakeLists.txt**.  

All cmake variables data type are **STRINGS**.  
**${VARIABLE}** is the method to get the data of variable, and the result is a string.  

CMake does not care UPPER or lower cases, IF() and if() are the same in cmake view.   
Conventionally, cmake variables use **UPPER_CASES** for naming, such as CMAKE_CXX_FLAGS_DEBUG, PROJ_INCLUDE_DIRS, etc.  
And cmake funtions use **lower_cases** for naming, such as add_compile_options(), find_package(), etc.  

The cmake funtion has two major classes, multi-command funtion and single command.  
The single command format is **funtion(TARGET paramater1, paramater2, paramater3.....)**.  
Maybe a funtion has TARGET, or maybe not.  
Further, as we mentioned before, the paramaters are only STRING type which is need quotation mark.  

### comments
There are two comment format:
```
# one line comment use sharp symbol


#[[ multiline comment
    use bracket ]]
```
### assign data
If we want to assign a variable with a data, we use set().
For example, if we want to set a flag of debug, we can do this:
```
#[[ 
CMAKE_CXX_FLAGS_DEBUG is the target variable
"-g" is the paramater1 string
]]

set(CMAKE_CXX_FLAGS_DEBUG "-g")

```
However, this will cause override the variable with new data.  
If we want to append, we can use this method:
```
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g")
```

### print
Moreover, The debug method is use **message()** built-in function.  
For example, if we want to print the variable of CMAKE_CXX_FLAGS_DEBUG,  
we can do this:
```
message("CMAKE_CXX_FLAGS_DEBUG is ${CMAKE_CXX_FLAGS_DEBUG}")

```

## Let's start our hello cmake project.

First, you need to assign minimum cmake version to constrain user version.  
Thus, the first line usually is 
```
cmake_minimum_required(VERSION 3.12)
# [[ 
VERSION is the target variable
3.5 is the paramater1 string
]]
```

and add our first code of cmake project

```
# add variable do not need declare
set(FIRST_STRING "Hello")
set(SECONT_STRING "CMake!!")

message("${FIRST_STRING} ${SECONT_STRING}")
```

And run with the command we learn at [overview](../../0.%20Overview#why-we-need-cmake-1)

## Example project
[https://github.com/sidneyniuhtc/00HelloCMake](https://github.com/sidneyniuhtc/00HelloCMake)

<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/00%20Basic%20Concept/linux.png"/>
<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/00%20Basic%20Concept/windows.PNG"/>

Previous: [Use CMake](../../1.%20Use/), 
Main: [Upper Layer](../../), 
Next: [Fist Project](../01%20Fist%20Project) 
