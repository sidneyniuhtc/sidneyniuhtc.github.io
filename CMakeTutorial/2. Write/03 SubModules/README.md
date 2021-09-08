# Sub-Modules

## Multiple Projects
If we want to manage multiple projects, use submodule is a better way.

At git folder, you can add submodule by  
git submodule add <git-project> <final-path>  
for example:
```
$ git submodule add https://github.com/sidneyniuhtc/02Math.git 02Math
$ git submodule add https://github.com/sidneyniuhtc/01FirstProject.git 3rdParty/01FirstProject
```
And we can add the subfoler at our CMakeList.txt
```
add_subdirectory(02Math)
```
when you update submodule, need update
```
git submodule foreach --recursive git pull origin master
```
 
## Use the project
pull data with recursive method
  
```
git clone --recursive https://github.com/sidneyniuhtc/03SubModule.git
```

## Example
[https://github.com/sidneyniuhtc/03SubModule](https://github.com/sidneyniuhtc/03SubModule)

  
Previous: [Test Framework](../02%20CTtest%20Framework/), 
Main:[Upper Layer](../../)
Next: 
  
  
