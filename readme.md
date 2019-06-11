# PROJ 6.1.0

Built with [rtools-packages](https://github.com/r-windows/rtools-packages/blob/master/mingw-w64-proj/PKGBUILD) and 
[rtools-backports](https://github.com/r-windows/rtools-backports/blob/master/mingw-w64-proj/PKGBUILD).

The dependency `libsqlite3.a` is not ABI sensitive so we use the same build for both toolchains. Example linkage:


```
VERSION = 6.1.0
RWINLIB = ../windows/proj-$(VERSION)
PKG_CPPFLAGS = -I$(RWINLIB)/include
TARGET = lib$(subst gcc,,$(COMPILED_BY))$(R_ARCH)

PKG_LIBS = \
	-L$(RWINLIB)/$(TARGET) \
	-L$(RWINLIB)/lib$(R_ARCH) \
	-lproj -lsqlite3

CXX_STD = CXX11
```