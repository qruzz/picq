# picq - the one stop shop for PIC development.

picq is a complete cli for developing embedded systems on the Microchip PIC16 and PIC18 microcontrollers.
It bundles the sdcc compiler, which in turn bundles the gputils consisting of the gpasm assembler and gplink linker.
For flashing the executable hex files to the target microcontroller, picq is utilising the usbpicprog cli.

## Installation:
For linux picq can be installed through `apt-get` package manager. It is also available on the forked Homebrew, Linuxbrew:

```zsh	
sudo apt-get install picq
```

```zsh
brew update && brew install picq
```

For installation on macOS, the package is available on Homebrew:

```zsh
brew update && brew install picq
```

If for some reason, your not using a package manager, you can clone this git repository, and place the excecutable in your PATH.

The first time you run the program, it will check if you have the necessary packages installed. If not, it will install them for you. Therefore you should run it using sudo.

```zsh
sudo picq
```

## Usage:

```zsh
picq [OPTIONS...] <file_name> [<file_name>...]
```

#### Options:

```
-h --help          Display the help screen.
-v --version       Display version of cli.
--verbose          Run as verbosem, showing more information.
-t --target        Specify the target microprocessor.
-c --compile-only  Only compile the files. Dont flash to chip.
-p --port          Specify the port on which to flash.
-b --baud          Specify the BAUD rate. Default is 57600.
-a --asemble       Asemble an .asm file, link it and create an executable. Dont flash.
-f --flash         Flash a hex file to the microcontroller.
```

#### Example usage:

```
picq -c -t pic18f4550 main.c
picq -t pic18f4550 -p /dev/cu.usbmodemFD121 -b 9600 main.c
picq -c -t pic18f4550 main.c
picq -a -t pic18f4550 main.asm subfile.asm
picq -f -t pic18f4550 main.hex
```