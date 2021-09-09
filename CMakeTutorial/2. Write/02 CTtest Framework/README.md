# CTest Framework

## What is ctest?
ctest is cmake test framework, it provides cross-platform unit test. 

## Project File Hierarchy
Separate header and source is better for packing library.  
And separate test files for individual test.  
This structure is easy for install.  
```
Project Folder  
　|　  
　├─　include (folder)  
　|　　　├─ Add.hpp  
　|　　　└─ Fractor.hpp  
　|　  
　├─　src (folder)  
　|　　　├─ Add.cpp  
　|　　　└─ Fractor.cpp  
　|　  
　└─　test (folder)  
　　　　├─ test_main.cpp  
　　　　├─ TestFractor.cpp  
　　　　└─ TestAdd.cpp  
```

## Pack our project as library
First, Use **file()** funtion to find the source files of our library.  
Second, create our library with found sources.  
```
file(GLOB_RECURSE PROJ_LIB_SOURCES "${PROJECT_SOURCE_DIR}/src/*.cpp")
add_library(PROJ_LIB ${PROJ_LIB_SOURCES} ) 
```
Let all objects to include our headers.
```
target_include_directories(PROJ_LIB PUBLIC "${PROJECT_SOURCE_DIR}/include")
```
Further Reading: [Are CMAKE_SOURCE_DIR and PROJECT_SOURCE_DIR the same in CMake?](https://stackoverflow.com/questions/32028667/are-cmake-source-dir-and-project-source-dir-the-same-in-cmake)

## Create test_main with our project lib
Find the all test files.
```
file(GLOB_RECURSE PROJ_TEST_SOURCES "${PROJECT_SOURCE_DIR}/test/*.cpp")
add_executable(TestMath ${PROJ_TEST_SOURCES})
```
Link our library to the test file
```
target_link_libraries(${PROJ_TEST} ${PROJ_LIB})
```

## Write ctest
First, you need to enable testing
```
enable_testing()
```

In the past, you can add ctest with include(CTest), add_test().  
But now, we can use gtest  
```
include(GoogleTest)
gtest_discover_tests(${PROJ_TEST})
```


## Example code
[https://github.com/sidneyniuhtc/02TtestFramework](https://github.com/sidneyniuhtc/02TtestFramework)
On Windows:
```
git clone https://github.com/sidneyniuhtc/02TtestFramework
cd 02Math
mkdir build
cd build
cmake -x64 ..
cmake --build . --config Release
ctest
```
On Linux:
```
git clone https://github.com/sidneyniuhtc/02TtestFramework
cd 02Math
mkdir build
cd build
cmake ..
cmake --build .
ctest
```

<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/02%20CTtest%20Framework/ctest%20on%20linux.PNG"/>
<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/2.%20Write/02%20CTtest%20Framework/ctest%20on%20win.PNG"/>

Previous: [Basic Concept](../01%20Fist%20Project), 
Main:[Upper Layer](../../), 
Next: [SubModule](../03%20SubModules/) 
