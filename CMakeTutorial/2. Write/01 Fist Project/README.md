# Wrtie CMake

## Our first project

### Project name

Remember, when you are using cmake, you always need to read the log.  
At previous part, we saw that there is a warning message when call the cmake command:
```
  No project() command is present.  The top-level CMakeLists.txt file must
  contain a literal, direct call to the project() command.  Add a line of
  code such as

    project(ProjectName)

  near the top of the file, but after cmake_minimum_required().

  CMake is pretending there is a "project(Project)" command on the first
.
.
.
```

Let us add project name to our project
```
project ("FirstProject")
```


### Executable project

If you want to make a executable project, you need to add a 

```
add_executable(FirstProject "main.cpp")
```

### Find library

If a module is support by cmake in default, there is a FindXXX.cmake method.

You can see official doc at [modules](https://cmake.org/cmake/help/latest/manual/cmake-modules.7.html) or just see the file in cmake installed path.  
For example:   
"C:\Program Files\CMake\share\cmake-3.18\Modules" has lots of FindXXX.cmake files.  
"usr/share/cmake-3.21/Modules/" has lots of FindXXX.cmake files.  

We use google test as our example.

```
find_package(GTest)

```

When you call the find_package(XXX)

Usually has many variables such as XXX_INCLUDE_DIRS, XXX_SHARED_LIBRARIES, XXX_STATIC_LIBRARIES, XXX_VERSION, XXX_FOUND.  
All of these can be found in Modules/FindXXX.cmake file.  
For example, you can check
```
message("GTEST_FOUND is ${GTEST_FOUND}")
message("GTEST_INCLUDE_DIRS is ${GTEST_INCLUDE_DIRS}")
message("GTEST_VERSION is ${GTEST_VERSION}")

```

For link libraries and include the headers, you need to use include_directories and link_libraries
```
    include_directories(${GTEST_INCLUDE_DIRS})
    link_libraries(${GTEST_BOTH_LIBRARIES})
```

If you have many projects, you need to assign by target.
Thus, this one is more recommended:
```
# assign for target - paramater
target_include_directories(FirstProject ${GTEST_INCLUDE_DIRS})
target_link_libraries(FirstProject ${GTEST_BOTH_LIBRARIES})
```

### flow control

At "Basic concepts of CMake codes", we told about there are two classes of funtions.  
Another fution class is multi-command funtions.  
These funtions have pair of start function and end function, like html has a starting tag and closing tag.  
for example:
```
foreach(INPUTS input1, input2, input3....)
    message("current is ${INPUTS}")
endforeach(INPUTS)
```

We can add google test as library when we found the library
```
if(GTEST_FOUND)
    include_directories(${GTEST_INCLUDE_DIRS})
    target_link_libraries(01GoogleTest ${GTEST_BOTH_LIBRARIES})
endif()

```

### Example project
[https://github.com/sidneyniuhtc/01FirstProject](https://github.com/sidneyniuhtc/01FirstProject)

<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/01%20Fist%20Project/Windows.PNG"/>


### fail on linux

<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/01%20Fist%20Project/Fail%20on%20Linux.PNG"/>

When we just build the project on linux, google test will fail because the log shows not find the pthread.  
We need to add a setting in our cmake codes.
```
if(UNIX)
    target_link_libraries(01GoogleTest ${GTEST_BOTH_LIBRARIES})
endif()
```
Finally,  
<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/01%20Fist%20Project/Success%20on%20Linux.PNG"/>



Previous: [Basic Concept](../00%20Basic%20Concept), 
Main:[Upper Layer](../../)