* Get the repository to ESP-IDF v5.1.4 (The highest version that works without problem)
```
mkdir -p ~/esp
cd ~/esp
git clone https://github.com/espressif/esp-idf.git
cd esp-idf
git pull
git checkout d7b0a45ddbddbac53afb4fc28168f9f9259dbb79
git submodule update --init --recursive
```

| Supported Targets | ESP32 | ESP32-C2 | ESP32-C3 | ESP32-C6 | ESP32-H2 | ESP32-S2 | ESP32-S3 |
| ----------------- | ----- | -------- | -------- | -------- | -------- | -------- | -------- |

# Using ESP-IDF in Custom CMake Projects

This example illustrates using ESP-IDF components as libraries in custom CMake projects. The application
in this example can run on either host or on an ESP32, and the appropriate libraries are linked
to the executable depending on which target is specified. If the target is an ESP32, the libraries
created from ESP-IDF components are linked. On the other hand, stub libraries are linked if example
is meant to be run on the host to simulate the same application behavior.

The application in this example is equivalent to the `hello_world` example under `examples/get-started/hello_world`.

## Building this Example

To build this example, the user can either run [build-esp32.sh](./build-esp32.sh) to build for the ESP32
or run [build.sh](./build.sh) to build for the host:

```bash
# Builds the example for ESP32s3
./build-esp32s3.sh
```

Note: To build for a different target SoC, copy the `build-esp32.sh` file and change the `-DTARGET=esp32` clause on the second line.

or

```bash
# Builds the example to run on host
./build.sh
```

## Flashing and Running this Example

To flash and run the example, users can run either  [run-esp32.sh](./run-esp32.sh) or [run.sh](./run.sh) depending
on what the example was built for. In the case of ``run-esp32.sh``, the port needs to be specified:

```bash
# Run the example on device connected to /dev/ttyUSB1
./run-esp32.sh /dev/ttyUSB1
```

or

```bash
# Run the example on the host
./run.sh
```

```bash
cmake --build build -- menuconfig
```
Note: ESP-IDF project configuration isn't used by the host CMake builds, the config is only read when the project is built using the ESP-IDF build system.

---

There is a discussion on using ESP-IDF in custom CMake projects in the programming guide under `API Guides` -> `Build System` -> `Using ESP-IDF in Custom CMake Projects`
