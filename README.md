# Pintos

Code from [pintos-os.org](http://pintos-os.org/). See `LICENSE` and `AUTHORS` for more information. Pintos is an educational operating system for the x86. Pintos was developed for Stanford's CS 140 operating systems course as a successor to Nachos, a less realistic educational operating system.

# Installation

On my machine running Fedora 29, I installed Pintos as follows (`...` is the **absolute** path to Pintos):

1. Install `qemu` (it's going to be `qemu-system-x86_64`)

2. Download and extract the latest `Pintos` from the official git repository

3. Set `GDBMACROS` (line 4) in `.../src/utils/pintos-gdb` to `.../src/misc/gdb-macros` and test the configuration by running `.../src/utils/pintos-gdb`

4. Compile the utilities in `.../src/utils` with `make`, probably after removing obsolete headers in some source files

5. Change `SIMULATOR` (line 7) in `.../src/threads/Make.vars` to `-qemu`

6. Compile the kernel in `.../src/threads/` with `make`

7. Edit `.../src/utils/pintos`:

    * line 103: `$sim = "qemu" ...`
    * line 257: `... find_file ('.../src/threads/build/kernel.bin')`
    * line 621: `my (@cmd) = ('qemu-system-x86_64')` or whatever your `qemu` command is

8. Edit `.../src/utils/Pintos.pm`:

    * line 362: `... find_file ('.../src/threads/build/loader.bin')`

9. `$cd .../src/utils` and run `$pintos run alarm-multiple` to verify your install
