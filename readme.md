# PROJ 6.3.1

Built with and [rtools-backports](https://github.com/r-windows/rtools-backports/blob/master/mingw-w64-proj/PKGBUILD).
Both `libproj` and `libsqlite3` are not ABI sensitive so we use the same build for both toolchains. Example linkage:


```
VERSION = 6.3.1
RWINLIB = ../windows/proj-$(VERSION)
PKG_CPPFLAGS = -I$(RWINLIB)/include
TARGET = lib$(subst gcc,,$(COMPILED_BY))$(R_ARCH)

PKG_LIBS = \
	-L$(RWINLIB)/$(TARGET) \
	-L$(RWINLIB)/lib$(R_ARCH) \
	-lproj -lsqlite3

CXX_STD = CXX11
```