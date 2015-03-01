#
# ${R_HOME}/src/library/graphics/src/Makefile

pkg = graphics

VPATH = ../../../../../src/library/graphics/src
srcdir = ../../../../../src/library/graphics/src
top_srcdir = ../../../../..

top_builddir = ../../../..
subdir = src/library/$(pkg)/src
R_HOME = $(top_builddir)
R_SHARE_DIR = $(R_HOME)/share
R_INCLUDE_DIR = $(R_HOME)/include

SOURCES_C = init.c base.c graphics.c par.c plot.c plot3d.c stem.c

DEPENDS = $(SOURCES_C:.c=.d)
OBJECTS = $(SOURCES_C:.c=.o)

PKG_CFLAGS = $(C_VISIBILITY)

SHLIB = $(pkg).so

# need Defn.h etc, and config.h
PKG_CPPFLAGS =-I../../../include -I$(top_srcdir)/src/include -DHAVE_CONFIG_H \
  -I$(top_srcdir)/src/main


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
init.o: ../../../../../src/library/graphics/src/init.c \
 ../../../include/config.h ../../../../include/R.h \
 ../../../../include/Rconfig.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rinternals.h \
 ../../../../../src/library/graphics/src/graphics.h \
 ../../../../include/R_ext/Rdynload.h
base.o: ../../../../../src/library/graphics/src/base.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/Graphics.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/include/Rgraphics.h \
 ../../../../../src/include/GraphicsBase.h
graphics.o: ../../../../../src/library/graphics/src/graphics.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/Graphics.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/include/Rgraphics.h \
 ../../../../../src/include/GraphicsBase.h ../../../../include/Rmath.h
par.o: ../../../../../src/library/graphics/src/par.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h ../../../../include/Rmath.h \
 ../../../../../src/include/Graphics.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/include/Rgraphics.h \
 ../../../../../src/library/graphics/src/graphics.h \
 ../../../../../src/library/graphics/src/par-common.c
plot.o: ../../../../../src/library/graphics/src/plot.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/Graphics.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/include/Rgraphics.h \
 ../../../../../src/include/Print.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/PrtUtil.h ../../../../include/Rmath.h \
 ../../../../../src/library/graphics/src/graphics.h
plot3d.o: ../../../../../src/library/graphics/src/plot3d.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h ../../../../include/Rmath.h \
 ../../../../../src/include/Graphics.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/include/Rgraphics.h \
 ../../../../../src/include/Print.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/PrtUtil.h \
 ../../../../../src/library/graphics/src/graphics.h \
 ../../../../../src/main/contour-common.h
stem.o: ../../../../../src/library/graphics/src/stem.c \
 ../../../include/config.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rmath.h
