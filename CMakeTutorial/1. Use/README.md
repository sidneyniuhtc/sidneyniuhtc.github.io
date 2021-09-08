# Use CMake

## mix using command line and gui
```
 mkdir opencv
```

```
git clone https://github.com/Itseez/opencv_contrib.git
cd opencv_contrib
git checkout ${CV_VERSION}

```
```

```
cd ..
git clone https://github.com/Itseez/opencv.git
cd opencv
git checkout ${CV_VERSION}
```

```
```
mkdir build
cd build
cmake -G "Visual Studio 16 2019" -Ax64 \
    -DCMAKE_BUILD_TYPE=RELEASE \
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
