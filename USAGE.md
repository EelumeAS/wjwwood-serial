# Implementation

This library is downloaded as an overlay-port in vcpkg.

## Usage

Simple example of usage

### CMakeLists.txt
`find_package(wjwwood-serial CONFIG REQUIRED)`
`target_link_libraries(${TARGET_NAME} wjwwood-serial::wjwwood-serial)`

### my_header.h
`#include <serial/serial.h>`

### my_source.cpp
```cpp
// Create and open serial port
serial::Serial serialport("port name", baudrate, serial::Timeout::simpleTimeout(100));

// Transmit data
std::string data = "Transmit test";
auto transmitted_bytes = serialport.write(data);
if (transmitted_bytes != data.size())
{
    std::cout << "Transmitted size not equal data packet size" << std::cout::endl;
}

// Receive data
auto available_bytes = serialport.available();
std::string read_data = serialport.read(available_ bytes);

// Flush buffers
serialport.flush();

// Check if port is open
if (serialport.isOpen())
{
    std::cout << "Serialport is open" << std::cout::endl;
}

// Close port
serialport.close();
```

## Configure
Configure pointing to your vcpkg folder, `-DCMAKE_TOOLCHAIN_FILE=<...>/scripts/buildsystems/vcpkg.cmake` and target triplet `-DVCPKG_TARGET_TRIPLET=<applicable-triplet>`.
```ps
cmake .. -DCMAKE_TOOLCHAIN_FILE=<...>\scripts\buildsystems\vcpkg.cmake -DVCPKG_TARGET_TRIPLET=<applicable-triplet>
```
