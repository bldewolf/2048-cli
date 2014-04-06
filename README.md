#2048-pxe

A gutted version of the cli version of the game
[2048](https://github.com/gabrielecirulli/2048) for your PXE boot server.

![Screenshot](http://i.imgur.com/yzIeJjt.png)

### To install

Place the already-built 2048_curses.elf and syslinux's mboot.c32 and friends in
your PXE directory.  Place this target in your pxelinux.cfg/default or
something:

	label 2048
	menu label 2048
	kernel mboot.c32
	append 2048_curses.elf

### To build

Vaguely follow the steps in the [Tint guide](http://www.coreboot.org/Tint) to
get libpayload (we want lpgcc) built.  Once lpgcc works, hit the source with it:

	lpgcc 2048_curses.c -o 2048_curses.elf -Wall -Os

The resulting binary should be good enough for mboot.c32 to take care of.

Oh, and it should still be okay to compile it on regular systems with:

	gcc -o 2048_curses 2048_curses.c -lcurses -O2 -Wall

## License
This code is licensed under the [MIT License](https://github.com/Tiehuis/2048-cli/blob/master/LICENSE).
