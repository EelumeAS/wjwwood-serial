**CUSTOM FORK NOTE**

_2025-02-25 Update_
Functionality to list ports are upgraded to gather more ports than initially possible.

_Initial release_
This fork does not change any functionality of the original code. Changes applied are:
- Replaced usage of catkin build system in favor of cmake
- Cleaned build warnings for linux and windows builds

The rationale for making this port is to create a custom vcpkg port that can be included
in the different Eelume code projects the same way as other third party packages used.


# Serial Communication Library

This is a cross-platform library for interfacing with rs-232 serial like ports written in C++. It provides a modern C++ interface with a workflow designed to look and feel like PySerial, but with the speed and control provided by C++. 

This library is in use in several robotics related projects and can be built and installed to the OS like most unix libraries with make and then sudo make install, but because it is a catkin project it can also be built along side other catkin projects in a catkin workspace.

Serial is a class that provides the basic interface common to serial libraries (open, close, read, write, etc..) and requires no extra dependencies. It also provides tight control over timeouts and control over handshaking lines. 

### Documentation

Website: http://wjwwood.github.io/serial/

API Documentation: http://wjwwood.github.io/serial/doc/1.1.0/index.html

### Dependencies

Required:
* [cmake](http://www.cmake.org) - buildsystem

Optional (for documentation):
* [Doxygen](http://www.doxygen.org/) - Documentation generation tool
* [graphviz](http://www.graphviz.org/) - Graph visualization software

### Install

Get the code:

    git clone https://github.com/EelumeAS/wjwwood-serial.git

Configure:

    With example application:
    cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_EXAMPLE=ON

    Without example application:
    cmake -DCMAKE_BUILD_TYPE=Release

Build:

    Windows: cmake --build . --config Release
    Linux: make -j16

Install:

    Windows cmake --install .
    Linux: make install

### License

[The MIT License](LICENSE)

### Authors

William Woodall <wjwwood@gmail.com>
John Harrison <ash.gti@gmail.com>

### Contact

William Woodall <william@osrfoundation.org>
