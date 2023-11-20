Created 2016-09-27

Debug / Rebuild Win32::OLE to "fix" the problem with threads
crashing when they were finished and detached or joined.

To build:

	perl Makefile.pl
	dmake
	dmake install

Changes are all in OLE.xs indentifiable with search for "prh"

To use:

	In a program that uses Win32::OLE and threads,
	call Win32::OLE::prhSetThreadNum(1) at the top
	of the program, before creating (and particularly
	finishing) any threads.

	This will cause Win32::OLE::AtExit(pTHX_ void *pVoid)
	to short return, and not free the libraries and
	destroy memory.

	Presumably, all of this will happen automatically
	in the (main) Perl interpreter when it really exits.
