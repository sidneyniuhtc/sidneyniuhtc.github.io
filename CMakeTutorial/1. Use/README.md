# Use CMake Project

## Ideal Scenario
* CMake Cycle
  1. there is a cmake project  
  2. build the cmake project  
  3. write a cmake project to include and link pre-build cmake project  
  4. loop i~iii

## Other Setting for cmake
On windows we need to build cmake with x64 and x86 at different folder.  
```
mkdir build
cd build
cmake -Ax64 ..
cmake --build . --config Debug
cmake --build . --config Release

cd ..
mkdir build32
cmake ..
cmake --build . --config Debug
cmake --build . --config Release
```

## Take GoogleTest for example
CMake only recognized the slash path which is "/" even on windows.  

### On Windows 
if you want to build google test with dll 
```
cd D:\package\Google
git clone https://github.com/google/googletest.git
cd .\googletest\
mkdir build
cd build
cmake -Ax64 -DBUILD_SHARED_LIBS=ON -DCMAKE_INSTALL_PREFIX=D:/package/Google/googletest/install ..
cmake --build . --config Debug
cmake --build . --config Release
cmake --install .
```
And you need to Add environment of GTEST_ROOT with D:\package\Google\googletest\install  
And put all dll to your path.  
for exmaple :
```
PS \> $env:GTEST_ROOT = D:\package\Google\googletest\install
PS \> $env:Path = D:\package\Google\googletest\install\bin;$env:Path
```

### On linux 
if you want to build static library you need to build by cmake after download.  
[https://forums.linuxmint.com/viewtopic.php?t=267500](https://forums.linuxmint.com/viewtopic.php?t=267500)

## Where to find the cmake variables?
There are many method to find how to set cmake project variables.   
One method is to read the cmake files of the project.  
Better method is using command `cmake -LAH`  

Easy method is use CMake-GUI, and this is what I most recommend.  
<img src="https://github.com/sidneyniuhtc/sidneyniuhtc.github.io/raw/master/CMakeTutorial/1.%20Use/cmake-gui.PNG"/>


## Take OpenCV for example
```
mkdir opencv
cd opencv
git clone https://github.com/Itseez/opencv_contrib.git
cd opencv_contrib
git checkout ${CV_VERSION}
cd ..
git clone https://github.com/Itseez/opencv.git
cd opencv
git checkout ${CV_VERSION}
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=RELEASE \
    -DCMAKE_INSTALL_PREFIX=/usr/local \
    -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
    -DINSTALL_C_EXAMPLES=OFF \
    -DINSTALL_PYTHON_EXAMPLES=OFF \
    -DBUILD_EXAMPLES=OFF \
    -DWITH_OPENGL=ON \
    -DWITH_V4L=ON \
    -DWITH_XINE=ON \
    -DWITH_TBB=ON ..
     
```

Previous: [Overview](../0.%20Overview/), 
Main: [Upper Layer](../), 
Next: [Write CMake](../2.%20Write/00%20Basic%20Concept/)
