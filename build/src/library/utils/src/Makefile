#
# ${R_HOME}/src/library/utils/src/Makefile

pkg = utils

VPATH = ../../../../../src/library/utils/src
srcdir = ../../../../../src/library/utils/src
top_srcdir = ../../../../..

top_builddir = ../../../..
subdir = src/library/$(pkg)/src
R_HOME = $(top_builddir)
R_SHARE_DIR = $(R_HOME)/share
R_INCLUDE_DIR = $(R_HOME)/include

SOURCES_C = init.c io.c size.c sock.c stubs.c utils.c

DEPENDS = $(SOURCES_C:.c=.d)
OBJECTS = $(SOURCES_C:.c=.o)

PKG_CFLAGS = $(C_VISIBILITY)

SHLIB = $(pkg).so

XZ_CPPFLAGS = #  -I$(top_srcdir)/src/extra/xz/api
# need Defn.h etc, and config.h
PKG_CPPFLAGS =-I../../../include -I$(top_srcdir)/src/include -DHAVE_CONFIG_H \
  -I$(top_srcdir)/src/main $(XZ_CPPFLAGS)


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
init.o: ../../../../../src/library/utils/src/init.c \
 ../../../include/config.h ../../../../include/R.h \
 ../../../../include/Rconfig.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rinternals.h \
 ../../../../../src/library/utils/src/utils.h \
 ../../../../include/R_ext/Rdynload.h
io.o: ../../../../../src/library/utils/src/io.c ../../../include/config.h \
 ../../../../../src/include/Defn.h ../../../../include/R_ext/Complex.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/Fileio.h \
 ../../../../../src/include/Rconnections.h \
 ../../../../include/R_ext/Connections.h \
 ../../../../../src/include/Print.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/PrtUtil.h ../../../../../src/include/rlocale.h \
 ../../../../../src/main/RBufferUtils.h
size.o: ../../../../../src/library/utils/src/size.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h
sock.o: ../../../../../src/library/utils/src/sock.c \
 ../../../../include/R.h ../../../../include/Rconfig.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rinternals.h
stubs.o: ../../../../../src/library/utils/src/stubs.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/Internal.h ../../../../include/Rinterface.h \
 ../../../../include/R_ext/RStartup.h \
 ../../../../../src/include/Rdynpriv.h \
 ../../../../include/R_ext/Rdynload.h \
 ../../../../../src/include/Rmodules/RX11.h \
 ../../../../../src/include/Rconnections.h \
 ../../../../include/R_ext/Connections.h
utils.o: ../../../../../src/library/utils/src/utils.c \
 ../../../include/config.h ../../../../include/R.h \
 ../../../../include/Rconfig.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rinternals.h \
 ../../../../../src/library/utils/src/utils.h
