# User Defined Scripts

## Reusable Scripts
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
　|　　　├─ scriptB.cmake  
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



## User Defined Function
The format of user defined function is 
```
function(<YourFunctionName> Arg1 Arg2...)
  <commands>
endfunction()
```
For example:
```
# define a funtion
funtion(foo Input1)
   message("${Input1}")
endfuntion()

# use a function
foo("hello cmake")
```


Previous: [Sub-Modules and Install](../03%20SubModules/), 
Main:[Upper Layer](../../)
