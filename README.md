CMake Tutorial
==============

Copyright 2017, Skand Hurkat. All rights reserved.

## Building

### Linux and MacOS

```bash
mkdir build
cd build
cmake ..
make
### This will create an executable "hello-world" in the build directory.
./bin/hello-world
```

### Windows

 1. Use the CMake GUI.

     1. Set the source directory to this directory.

     2. Create a new "build" directory inside this one, set it as the
        build directory.

     3. Click on "Configure".

         1. Select the appropriate version of MSVC, e.g. "Visual Studio
            14 2015 Win64".

         2. Click "Finish".

      4. Click on "Generate".

      5. Click on "Open Project".

 2. This will open a Visual Studio project with three targets --
    ALL_BUILD, hello-world, ZERO_CHECK.

      1. Click through Build -> Build solution.

      2. This will create a folder (`bin/*`) for the current build
         configuration (Debug, MinSizeRel, Release, RelWithDebInfo) with
         a `hello-world.exe` file.

      3. Open a command prompt or PowerShell window in this folder, type
         in `.\hello-world.exe` to run this executable.

