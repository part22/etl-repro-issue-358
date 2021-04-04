## Requirements

 - Ubuntu 20.04 LTS running on wsl-2
 - Clang with avr support (needs to be compiled from source)
 - cmake 3.18

## Building

```
mkdir build
cmake -Ssource -Bbuild -GNinja --no-warn-unused-cli -DCMAKE_EXPORT_COMPILE_COMMANDS:BOOL=TRUE -DCMAKE_BUILD_TYPE:STRING=MinSizeRel -DCMAKE_C_COMPILER:FILEPATH=[path-to-clang] -DCMAKE_CXX_COMPILER:FILEPATH=[path-to-clang++] 
ninja -Cbuild
```
