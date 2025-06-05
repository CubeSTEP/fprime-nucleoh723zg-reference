# F´ LED Blinker Tutorial for Arduinos

This repository contains the source code and documentation for the F Prime Arduino LED Blinker tutorial.

This project is an implementation of the [F´ LED Blinker ARM Linux Tutorial](https://fprime.jpl.nasa.gov/latest/tutorials-led-blinker/docs/led-blinker/) which will allow you to test on Arduino-based microcontrollers using the [`fprime-arduino` toolchain](https://github.com/fprime-community/fprime-arduino.git) instead of `fprime-arm-linux`. 

This version uses a scaled down deployment of F´ to account for the limited resources available on baremetal hardware.

To run through the tutorial, please visit the F´ website and look for the tutorial section: https://fprime.jpl.nasa.gov

## Prerequisites

In order to run through this tutorial, users should first do the following:

1. Follow the [Hello World Tutorial](https://fprime.jpl.nasa.gov/latest/tutorials-hello-world/docs/hello-world/  )
2. Ensure F´ tools have been [bootstrapped](https://fprime.jpl.nasa.gov/latest/tutorials-hello-world/docs/hello-world/#1-creating-an-f-project)
3. Acquire and set up the appropriate [hardware](https://fprime.jpl.nasa.gov/latest/tutorials-arduino-led-blinker/docs/arduino-led-blinker/#appendix-hardware-requirements) for this tutorial
<!-- 4. Follow the [arduino-cli installation guide](https://github.com/fprime-community/fprime-arduino/blob/main/docs/arduino-cli-install.md) -->

## Instructions
1. Clone the GitHub repository: 
```sh
fprime-bootstrap clone https://github.com/CubeSTEP/fprime-nucleoh723zg-reference.git
```

> [!NOTE]
> If `fprime-bootstrap` is not installed, run `pip install fprime-bootstrap`.
> A python virtual environment can be used.

2. Navigate into the GitHub repsitory and activate the virtual environment
```sh
source fprime-venv/bin/activate
```

3. Follow the [arduino-cli installation guide](https://github.com/fprime-community/fprime-arduino/blob/main/docs/arduino-cli-install.md)

> [!NOTE]
> Only the STM board manager URLs and packages need to be configured/installed

4. Install the following modules
```sh
pip install setuptools
pip install legacy-cgi
```

5. Run the following commands to generate and build the deployment
```sh
fprime-util generate
fprime-util build -j4
```

6. Flash board using this file path:
```
./build-artifacts/nucleo_H723ZG/LedBlinker/bin/LedBlinker.elf.hex
```

> [!NOTE]
> The board can be flashed with ST-LINK. STM32CubeProgrammer provides a UI to flash the board.

> [!NOTE]
> Still need to find a way to flash the board through the CLI.

7. Run `fprime-gds`
```
fprime-gds -n --dictionary ./build-artifacts/nucleo_H723ZG/LedBlinker/dict/LedBlinkerTopologyDictionary.json --communication-selection uart --uart-device /dev/cu.usbmodem141203 --uart-baud 115200
```

> [!NOTE]
> `/dev/cu.usbmodem141203` might need to be replaced with the correct port. On macOS, this can be done by running the following command: `ls -l /dev/cu.usb*`

## Contributing

If you would like to contribute to this tutorial, please open a pull request.

If you would like to add support for a new board not already listed in the [board list](https://github.com/fprime-community/fprime-arduino/blob/main/docs/board-list.md), feel free to open a pull request to [`fprime-arduino`](https://github.com/fprime-community/fprime-arduino).

## Resources
- [Discussions](https://github.com/nasa/fprime/discussions)
- [Submit an Issue](https://github.com/nasa/fprime/issues)
- [F´ Community](https://github.com/fprime-community)