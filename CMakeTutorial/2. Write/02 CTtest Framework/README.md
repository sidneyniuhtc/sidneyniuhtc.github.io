# Write CMake

## CTest Framework

### What is ctest?
ctest is cmake test framework, it provides cross-platform


### Project File Sample
Project Folder  
　|　  
　├─　include (folder)  
　|　　　├─ Add.hpp  
　|　　　└─ Fractor.hpp  
　├─　src (folder)  
　|　　　├─ Add.cpp  
　|　　　└─ Fractor.cpp  
　├─　test (folder)  
　　　　├─ test_main.cpp  
　　　　├─ TestFractor.cpp  
　　　　└─ TestAdd.cpp  


### 


### Write ctest
First, you need to add 


### Example code
[https://github.com/sidneyniuhtc/02Math](https://github.com/sidneyniuhtc/02Math)
On Windows:
```
git clone https://github.com/sidneyniuhtc/02Math
cd 02Math
mkdir build
cd build
cmake -x64 ..
cmake --build . --config Release
ctest
```
On Linux:
```
git clone https://github.com/sidneyniuhtc/02Math
cd 02Math
mkdir build
cd build
cmake ..
cmake --build .
ctest
```
