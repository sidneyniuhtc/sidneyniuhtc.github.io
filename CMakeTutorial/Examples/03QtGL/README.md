# 03QtGL 
manipulate pen drawing

## Keyboard
'Up' : make pen dot bigger  
'Down' : make pen dot smaller  
'R' : make pen color red  
'G' : make pen color green  
'B' : make pen color blue  
'W' : make pen color white  

# Prerequisites  
  * CMake (3.5 or latter)  
  * Qt5 (5.8 is better)  

## Command on Windows PowerShell:  
First, you need $ENV:Qt5_ROOT  
Second, you need add C:\Windows\Microsoft.NET\Framework\\_v4.0.30319_ to Path  
PS\\> mkdir build  
PS\\> cd build  
PS\\> cmake -G "Visual Studio 14 Win64" ..  
PS\\> MSBuild ALL_BUILD.vcxproj /p:Platform=x64 /p:Configuration=Debug  
PS\\> MSBuild ALL_BUILD.vcxproj /p:Platform=x64 /p:Configuration=Release   

## Command on  Linux:
[user]$ mkdir build && cd build && cmake .. && make  
