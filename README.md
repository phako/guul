# guul
Guul Unified UUID Library

Provide unified access to native UUID libraries.

To use, you can either compile it as a dynamic library or copy the sources to
your project (if it's compatible with LGPL2.1 code) and use the guul.m4 macro
in your configure script.

If you opted for inclusion, use

GUUL_CHECK_UUID([internal])

You will get
 * GUUL_CFLAGS - compiler flags if necessary
 * GUUL_LIBS - additional libraries if needed for platform
 * GUUL_PKG - the name of the pkg-config files needed
 * GUUL_FLAVOR - to indicate whatever flavor of UUID you're using
