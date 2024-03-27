# Unofficial FTD2XX MSI packages
This repository packages the closed-source FTD2XX drivers as an MSI using CMake and WiX, so that we can install and use them during automated builds. It includes a CMake config file, so you can directly use it in your projects

## Installation
Install CMake using `winget install kitware.cmake` in an Administrator Command Prompt and get WiX 3 from <https://github.com/wixtoolset/wix3/releases/tag/wix314rtm>. You can then build an MSI using the following commands:

```batch
mkdir build
cd build
cmake ..
cpack
```

It will create an MSI file in the `build` directory. You can install it by double-clicking it and following the wizard.

## Usage
Once the package has been installed, you can use it in your CMakeLists using the following statements:

```cmake
find_package(ftd2xx REQUIRED)
target_include_directories(mytarget PUBLIC ${ftd2xx_INCLUDE_DIRS})
target_link_directories(mytarget PUBLIC ${ftd2xx_LIBRARY_DIRS})
target_link_libraries(mytarget ${ftd2xx_LIBRARIES})
```