Created 2016-09-27

Debug / Rebuild Win32::OLE to "fix" the problem with threads
crashing when they were finished and detached or joined.

To build:

	perl Makefile.pl
	dmake
	dmake install

Changes are all in OLE.xs indentifiable with search for "prh"




