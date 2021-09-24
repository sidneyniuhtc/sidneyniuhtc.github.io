# Sub-Modules and Install

## Developer

### Multiple Projects
If we want to manage multiple projects, use submodule is a better way.

At git folder, you can add submodule by `git submodule add <git-project> <final-path>`  
for example:
```
[user]$ git submodule add https://github.com/sidneyniuhtc/02Math.git 02Math
[user]$ git submodule add https://github.com/sidneyniuhtc/01FirstProject.git 3rdParty/01FirstProject
```
And we can add the subfoler at our CMakeList.txt
```
add_subdirectory(02Math)
add_subdirectory(3rdParty/01FirstProject)

```
When you update submodule, need update
```
[user]$ git submodule foreach --recursive git pull origin master
```

### Install Script 
Write **install()** function in CMakeList.txt
```
install(TARGETS lib02Math DESTINATION ViveSDK/libs)

install(DIRECTORY "${PROJECT_SOURCE_DIR}/02Math/include" DESTINATION ViveSDK)
```

### Create Config.cmake by EXPORT
When we need to generate Config.cmake automatically by cmake.  
We need to tell cmake where we move the files.
```
install(TARGETS lib02Math
  EXPORT lib02MathConfig
  RUNTIME DESTINATION ViveSDK/bin
  LIBRARY DESTINATION ViveSDK/lib
  ARCHIVE DESTINATION ViveSDK/lib
  INCLUDES DESTINATION ViveSDK/include
  )

install(EXPORT lib02MathConfig
    FILE lib02MathConfig.cmake
    DESTINATION ViveSDK
    NAMESPACE Vive::
)
```

## Use part

### Download
pull data with recursive method
  
```
[user]$ git clone --recursive https://github.com/sidneyniuhtc/03SubModule.git
```

### Build and install 

See: [Use CMake Project](../1.%20Use/)


## Example
[https://github.com/sidneyniuhtc/03SubModule](https://github.com/sidneyniuhtc/03SubModule)

  
Previous: [Test Framework](../02%20CTtest%20Framework/), 
Main:[Upper Layer](../../)
Next: [User Defined Scripts](../04%20User%20Defined%20Scripts/)
