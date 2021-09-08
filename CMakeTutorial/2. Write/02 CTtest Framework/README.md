# Write CMake

## CTest Framework

### what is ctest?

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
 
### Example code
[https://github.com/sidneyniuhtc/02Math](https://github.com/sidneyniuhtc/02Math)
```
git clone https://github.com/sidneyniuhtc/02Math
mkdir build
cd build
cmake -x64 ..
cmake --build . --config Release
ctest
```
