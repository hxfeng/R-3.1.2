#
# ${R_HOME}/src/library/grid/src/Makefile

pkg = grid

VPATH = ../../../../../src/library/grid/src
srcdir = ../../../../../src/library/grid/src
top_srcdir = ../../../../..

top_builddir = ../../../..
subdir = src/library/$(pkg)/src
R_HOME = $(top_builddir)
R_SHARE_DIR = $(R_HOME)/share
R_INCLUDE_DIR = $(R_HOME)/include

SOURCES_C = gpar.c grid.c just.c layout.c matrix.c register.c state.c \
  unit.c util.c viewport.c

SOURCES_F =
DEPENDS = $(SOURCES_C:.c=.d)
OBJECTS = $(SOURCES_C:.c=.o) $(SOURCES_F:.f=.o)

PKG_CFLAGS=$(C_VISIBILITY)

SHLIB = $(pkg).so

all: Makedeps
	@$(MAKE) shlib

Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status
	@cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@

Makedeps: Makefile $(DEPENDS)
	@cat $(DEPENDS) >> Makefile
	@touch $@

shlib: $(SHLIB)
	@$(MKINSTALLDIRS) \
	  $(top_builddir)/library/$(pkg)/libs
	@$(SHELL) $(top_srcdir)/tools/copy-if-change $(SHLIB) \
	  $(top_builddir)/library/$(pkg)/libs/$(SHLIB)

include $(R_HOME)/etc${R_ARCH}/Makeconf
include $(top_srcdir)/share/make/shlib.mk
LTO = 

mostlyclean: clean
clean:
	@-rm -rf .libs _libs
	@-rm -f Makedeps *.d *.o *$(SHLIB_EXT)
distclean: clean
	@-rm -f Makefile
maintainer-clean: distclean

## Automagically generated dependencies:
gpar.o: ../../../../../src/library/grid/src/gpar.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
grid.o: ../../../../../src/library/grid/src/grid.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
just.o: ../../../../../src/library/grid/src/just.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
layout.o: ../../../../../src/library/grid/src/layout.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
matrix.o: ../../../../../src/library/grid/src/matrix.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
register.o: ../../../../../src/library/grid/src/register.c \
 ../../../../include/R_ext/Rdynload.h ../../../../include/R_ext/Boolean.h \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Complex.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h ../../../../include/Rmath.h \
 ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
state.o: ../../../../../src/library/grid/src/state.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
unit.o: ../../../../../src/library/grid/src/unit.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
util.o: ../../../../../src/library/grid/src/util.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
viewport.o: ../../../../../src/library/grid/src/viewport.c \
 ../../../../../src/library/grid/src/grid.h ../../../../include/Rconfig.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/Constants.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
