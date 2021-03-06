### Introduction

The Chip-8 Disassembler outputs mnemonics that are the slightly modified
versions of http://devernay.free.fr/hacks/chip8/C8TECH10.HTM. Raw data that is
entered is outputted on a separate line. This way, we ensure compatibility with the
assembler.

### Usage

```
./Chip9_Disassembler [options] <filename>

Options:
  -c, --clean          Does not show the address of where the commands
                       are in memory. Only assembler is outputted.

  -n, --no-padding     Does not add 0x200 to addresses

  -h, --help           Shows this helpful message
```

### Output

With no options, the disassembler outputs the disassembled code into `stdout`
in this format for easy reading:

```
0200: JP 0202
0202: JP 0200
0204: 0000
```

As you can see, there is a 0x200 offset because of where the code is loaded
in memory (and also for easier and less-options debugging).

To remove the padding, add option `-n`.

To remove the addresses altogether, add option `-c`.

To write to file, use the `>` on the command.

```sh
./Chip8_Disassembler file > f.asm
```

