#
# ${R_HOME}/src/library/tools/src/Makefile

pkg = tools

VPATH = ../../../../../src/library/tools/src
srcdir = ../../../../../src/library/tools/src
top_srcdir = ../../../../..

top_builddir = ../../../..
subdir = src/library/$(pkg)/src
R_HOME = $(top_builddir)
R_SHARE_DIR = $(R_HOME)/share
R_INCLUDE_DIR = $(R_HOME)/include

SOURCES_C = text.c init.c Rmd5.c md5.c signals.c install.c getfmts.c http.c \
  gramLatex.c gramRd.c
DEPENDS = $(SOURCES_C:.c=.d)
OBJECTS = $(SOURCES_C:.c=.o)

# need config.h
PKG_CPPFLAGS = -I../../../include -I$(top_srcdir)/src/include \
  -DHAVE_CONFIG_H -I$(top_srcdir)/src/main
PKG_CFLAGS = $(C_VISIBILITY)

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

# suppress #line directives
YFLAGS=-l

$(srcdir)/gramRd.c: # $(srcdir)/gramRd.y
	@$(ECHO) "re-making gramRd.c"
	$(YACC) $(YFLAGS) $(srcdir)/gramRd.y
	$(SHELL) $(top_srcdir)/tools/move-if-change y.tab.c $(srcdir)/gramRd.c	
$(srcdir)/gramLatex.c: # $(srcdir)/gramLatex.y
	@$(ECHO) "re-making gramLatex.c"
	$(YACC) $(YFLAGS) $(srcdir)/gramLatex.y
	$(SHELL) $(top_srcdir)/tools/move-if-change y.tab.c $(srcdir)/gramLatex.c

## Automagically generated dependencies:
text.o: ../../../../../src/library/tools/src/text.c \
 ../../../../include/R.h ../../../../include/Rconfig.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h \
 ../../../../../src/library/tools/src/tools.h \
 ../../../../include/Rinternals.h
init.o: ../../../../../src/library/tools/src/init.c \
 ../../../../include/R.h ../../../../include/Rconfig.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h \
 ../../../../../src/library/tools/src/tools.h \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Rdynload.h
Rmd5.o: ../../../../../src/library/tools/src/Rmd5.c \
 ../../../../include/R.h ../../../../include/Rconfig.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h \
 ../../../../../src/library/tools/src/tools.h \
 ../../../../include/Rinternals.h \
 ../../../../../src/library/tools/src/md5.h
md5.o: ../../../../../src/library/tools/src/md5.c \
 ../../../../include/Rconfig.h ../../../../../src/library/tools/src/md5.h
signals.o: ../../../../../src/library/tools/src/signals.c \
 ../../../include/config.h ../../../../include/R.h \
 ../../../../include/Rconfig.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Constants.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Print.h \
 ../../../../include/R_ext/Random.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/RS.h \
 ../../../../../src/library/tools/src/tools.h \
 ../../../../include/Rinternals.h
install.o: ../../../../../src/library/tools/src/install.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h
getfmts.o: ../../../../../src/library/tools/src/getfmts.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/main/RBufferUtils.h
http.o: ../../../../../src/library/tools/src/http.c \
 ../../../../include/Rinternals.h ../../../../include/R_ext/Arith.h \
 ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Complex.h \
 ../../../../include/R_ext/Error.h ../../../../include/R_ext/Memory.h \
 ../../../../include/R_ext/Utils.h ../../../../include/R_ext/Print.h \
 ../../../../include/Rconfig.h \
 ../../../../../src/library/tools/src/tools.h
gramLatex.o: ../../../../../src/library/tools/src/gramLatex.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h ../../../../../src/include/Parse.h \
 ../../../../include/R_ext/Parse.h ../../../../../src/include/IOStuff.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rconfig.h
gramRd.o: ../../../../../src/library/tools/src/gramRd.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../include/R_ext/Complex.h ../../../../include/Rinternals.h \
 ../../../../include/R_ext/Arith.h ../../../../include/R_ext/libextern.h \
 ../../../../include/R_ext/Boolean.h ../../../../include/R_ext/Error.h \
 ../../../../include/R_ext/Memory.h ../../../../include/R_ext/Utils.h \
 ../../../../include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h ../../../../../src/include/Parse.h \
 ../../../../include/R_ext/Parse.h ../../../../../src/include/IOStuff.h \
 ../../../../include/R_ext/RS.h ../../../../include/Rconfig.h \
 ../../../../include/Rmath.h ../../../../../src/include/Rconnections.h \
 ../../../../include/R_ext/Connections.h
