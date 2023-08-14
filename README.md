# micro_ulab
Micro_uLab is a project that allows you to easily build and deploy Micropython firmware with uLab support on ESP32 boards. 
This repository provides an automated workflow using GitHub Actions to generate the firmware.

## Ref) [micropython-ulab](https://github.com/v923z/micropython-ulab)
Following the examples set in the referenced repositories, I successfully created the latest firmware using GitHub Actions.

## Version
- [Micropython](https://github.com/micropython/micropython.git): v1.20.0
- [ESP-IDF](https://github.com/espressif/esp-idf.git): v5.0.2
- [ULab](https://github.com/v923z/micropython-ulab): v6.0.12

A version of esp-idf that is compatible with the latest version of micropython.
- Micropython v1.19 & ESP-IDF v4.4.x (espnow X)
- Micropython v1.20 & ESP-IDF v5.0.x (espnow O)

```shell
export BUILD_DIR=$(pwd)

git clone https://github.com/v923z/micropython-ulab.git ulab
git clone https://github.com/micropython/micropython.git

cd $BUILD_DIR/micropython/
git clone -b v5.0.2 --recursive https://github.com/espressif/esp-idf.git esp-idf
cd esp-idf
./install.sh
. ./export.sh

cd $BUILD_DIR/micropython/mpy-cross
make
cd $BUILD_DIR/micropython/ports/esp32
make submodules

Makefile
BOARD=GENERIC 
USER_C_MODULES=$(BUILD_DIR)/ulab/code/micropython.cmake

make
```
