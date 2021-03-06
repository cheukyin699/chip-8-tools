### Introduction

This shouldn't be too too difficult to follow. Let's start!

### Building

Create a new directory to build the project. `mkdir build` should do just fine.
After this, execute the following commands:

```sh
cd build        # Or the directory that you created
cmake ..
make
```

If all is successful, you will see 3 executables:

```sh
Chip8_Assembler
Chip8_Emulator
Chip8_Disassembler
```

### Running the Emulator

Let's use one of the test programs to run on the emulator! As you can see in the
`c8games` directory, there are a ton of programs that you can play around with.
I will be using PONG2 for this example. To run PONG2, execute the command:

```sh
./Chip8_Emulator ../c8games/PONG2
```

Pretty straight-forward.
