#
# ${R_HOME}/src/library/grDevices/src/Makefile

pkg = grDevices

VPATH = ../../../../../src/library/grDevices/src
srcdir = ../../../../../src/library/grDevices/src
top_srcdir = ../../../../..

top_builddir = ../../../..
subdir = src/library/$(pkg)/src
R_HOME = $(top_builddir)
R_SHARE_DIR = $(R_HOME)/share
R_INCLUDE_DIR = $(R_HOME)/include

SOURCES_C = axis_scales.c chull.c devices.c init.c stubs.c colors.c \
  devCairo.c devPicTeX.c devPS.c \
  devQuartz.c # qdBitmap.c qdPDF.c
SOURCES_M = # qdCocoa.m

DEPENDS = $(SOURCES_C:.c=.d) $(SOURCES_M:.m=.d)
OBJECTS = $(SOURCES_C:.c=.o) $(SOURCES_M:.m=.o)

SHLIB = $(pkg).so

ZLIB_CPPFLAGS =  -I$(top_srcdir)/src/extra/zlib
# need Defn.h etc, and config.h
PKG_CPPFLAGS =-I../../../include -I$(top_srcdir)/src/include -DHAVE_CONFIG_H $(ZLIB_CPPFLAGS)

#AQUA_LIBS=-framework AppKit
R_ZLIBS=$(top_builddir)/src/extra/zlib/libz.a
#R_ZLIBS=-lz
PKG_LIBS = $(AQUA_LIBS) $(R_ZLIBS)

all: Makedeps
	@$(MAKE) shlib  cairodevice

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

cairodevice:
	@(cd cairo && $(MAKE))

include $(R_HOME)/etc${R_ARCH}/Makeconf
include $(top_srcdir)/share/make/shlib.mk
LTO = 

mostlyclean: clean
clean:
	@-rm -rf .libs _libs
	@-rm -f Makedeps *.d *.o *$(SHLIB_EXT)
	@(cd cairo && $(MAKE) clean)
distclean: clean
	@-rm -f Makefile
	@(cd cairo && $(MAKE) distclean)
maintainer-clean: distclean

## Automagically generated dependencies:
axis_scales.o: ../../../../../src/library/grDevices/src/axis_scales.c \
 ../../../include/config.h ../../../../include/R.h \
 ../../../../include/Rconfig.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/library/grDevices/src/grDevices.h
chull.o: ../../../../../src/library/grDevices/src/chull.c \
 ../../../include/config.h ../../../../include/R_ext/Boolean.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Complex.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h
devices.o: ../../../../../src/library/grDevices/src/devices.c \
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
init.o: ../../../../../src/library/grDevices/src/init.c \
 ../../../include/config.h ../../../../include/R.h \
 ../../../../include/Rconfig.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/library/grDevices/src/grDevices.h \
 ../../../../include/R_ext/Rdynload.h
stubs.o: ../../../../../src/library/grDevices/src/stubs.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/Internal.h \
 ../../../../../src/library/grDevices/src/grDevices.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h
colors.o: ../../../../../src/library/grDevices/src/colors.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/library/grDevices/src/grDevices.h
devCairo.o: ../../../../../src/library/grDevices/src/devCairo.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../include/R_ext/Rdynload.h
devPicTeX.o: ../../../../../src/library/grDevices/src/devPicTeX.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/rlocale.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../../src/include/Fileio.h \
 ../../../../../src/library/grDevices/src/grDevices.h
devPS.o: ../../../../../src/library/grDevices/src/devPS.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h ../../../../include/R_ext/Riconv.h \
 ../../../../include/Rmath.h ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rconfig.h \
 ../../../../../src/include/Fileio.h \
 ../../../../../src/library/grDevices/src/grDevices.h \
 ../../../../../src/extra/zlib/zlib.h \
 ../../../../../src/extra/zlib/zconf.h ../../../../include/Rversion.h
devQuartz.o: ../../../../../src/library/grDevices/src/devQuartz.c \
 ../../../include/config.h \
 ../../../../../src/library/grDevices/src/grDevices.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/GraphicsEngine.h \
 ../../../../include/R_ext/GraphicsDevice.h \
 ../../../../include/R_ext/QuartzDevice.h
