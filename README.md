# SPDY-for-iPhone

SPDY-for-iPhone is a project to create an easy to use library for SPDY.  A
pre-built binary is available in install/lib/libSPDY.a.

To use libSPDY.a:

1. Copy both install/lib/libSPDY.a and install/include/SPDY/SPDY.h into your
project.
2. Add the CFNetwork and SystemConfiguration frameworks to your list of
libraries to link against.
3. Follow the API in SPDY.h.


## Building libSPDY.a

libSPDY.a has a few external dependencies.  These are included as git
submodules and built using the venerable make.  The external libraries are:

- spdylay
- openssl (Included until Apple releases iOS with an NPN enabled OpenSSL)
- zlib

The external libraries require the following programs to build:
- pkgconfig
- automake
- autoconf
- libtool

I typically install these programs through MacPorts (http://www.macports.org/).
Fink or homebrew should also have these packages.

To build build the external libraries and libSPDY.a run the following commands:
```
$ git submodule init
$ git submodule update
$ make
```

## Build errors

- Syntax error in configure
    - Problem:

   ```
   ./configure: line 15731: syntax error near unexpected token `0.20'
   ./configure: line 15731: `PKG_PROG_PKG_CONFIG(0.20)'
   ```

    - Solution: Go back and install pkgconfig and delete spdylay/configure.

- Test button doesn't work in xcode 4.3.1
    - Problem:
      Lexical or Preprocessor issue
      NS_AVAILABLE' macro redefined
    - Solution: Run the tests with make check from the command line.
