# User Defined Scripts

## Reusable  
If you want to package a bundle of scripts, you can write a file named XXX.cmake at folder cmake.  
You can call the script by `include()`  
```
include(${PROJECT_SOURCE_DIR}/cmake/getGLFW.cmake)
```

If you want to write your own FindXXX.cmake, you can put at **cmake/Modules**  
You can appending the script path on **CMAKE_MODULE_PATH**.  
```
list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/Modules)
```

The file structure is as following:
```
Project Folder  
　|　  
　├─　cmake (folder)  
　|　　　├─ scriptA.cmake  
　|　　　├─ scriptA.cmake  
　|　　　|
　|　  　└─ Modules(folder)  
　|　  　 　　├─ FindXXX.cmake  
　|　  　 　　└─ FindYYY.cmake  
　|　  
　└─　source (folder)  
　　　　├─ Fractor.cpp  
　　　　└─ Add.cpp  
```

## Example Project
[https://github.com/sidneyniuhtc/04CustomizedScripts](https://github.com/sidneyniuhtc/04CustomizedScripts)

Previous: [Sub-Modules and Install](../03%20SubModules/), 
Main:[Upper Layer](../../)
