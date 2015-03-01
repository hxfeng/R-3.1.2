#
# ${R_HOME}/src/extra/tre/Makefile

VPATH = ../../../../src/extra/tre
srcdir = ../../../../src/extra/tre
top_srcdir = ../../../..

top_builddir = ../../..
subdir = src/extra/tre
R_HOME = $(top_builddir)

include $(top_builddir)/Makeconf

TRE_CPPFLAGS = -I$(srcdir)
ALL_CPPFLAGS = $(TRE_CPPFLAGS) $(R_XTRA_CPPFLAGS) $(CPPFLAGS) $(DEFS)

SOURCES = regcomp.c regerror.c regexec.c tre-ast.c tre-compile.c \
  tre-match-approx.c tre-match-backtrack.c tre-match-parallel.c \
  tre-mem.c tre-parse.c tre-stack.c xmalloc.c 

HEADERS = tre.h tre-ast.h tre-compile.h tre-config.h tre-internal.h \
  tre-match-utils.h tre-mem.h tre-parse.h tre-stack.h xmalloc.h

DEPENDS = $(SOURCES:.c=.d)
OBJECTS = $(SOURCES:.c=.o)
#ALL_CFLAGS = $(ALL_CFLAGS_LO) -fvisibility=hidden

distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = LICENSE Makefile.in Makefile.win R_changes \
  $(SOURCES) $(HEADERS)
noinst_LIBRARIES = libtre.a
libtre_a_SOURCES = $(SOURCES)
libtre_a_OBJECTS = $(OBJECTS)


all:  R

Makefile: $(srcdir)/Makefile.in \
  $(top_builddir)/config.status \
  $(SOURCES)
	@cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@

Makedeps: Makefile $(DEPENDS)
	@cat $(DEPENDS) >> Makefile
	@touch $@

R: Makefile 
	 @$(MAKE) Makedeps
	 @$(MAKE) $(noinst_LIBRARIES)

libtre.a: $(libtre_a_OBJECTS)
	rm -f $@
	$(AR) cr $@ $(libtre_a_OBJECTS)
	$(RANLIB) $@

mostlyclean: clean
clean:
	@-rm -f Makedeps *.d *.o *.lo *.a
distclean: clean
	@-rm -f Makefile dftables chartables.h
maintainer-clean: distclean

install install-strip uninstall TAGS info dvi check:

distdir: $(DISTFILES)
	@for f in $(DISTFILES); do \
	  test -f $(distdir)/$${f} \
	    || ln $(srcdir)/$${f} $(distdir)/$${f} 2>/dev/null \
	    || cp -p $(srcdir)/$${f} $(distdir)/$${f}; \
	done

## Automagically generated dependencies:

regcomp.o: ../../../../src/extra/tre/regcomp.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre.h \
 ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/xmalloc.h
regerror.o: ../../../../src/extra/tre/regerror.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h
regexec.o: ../../../../src/extra/tre/regexec.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/xmalloc.h
tre-ast.o: ../../../../src/extra/tre/tre-ast.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-ast.h \
 ../../../../src/extra/tre/tre-mem.h \
 ../../../../src/extra/tre/tre-internal.h ../../../../src/extra/tre/tre.h \
 ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-compile.h
tre-compile.o: ../../../../src/extra/tre/tre-compile.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-mem.h \
 ../../../../src/extra/tre/tre-stack.h \
 ../../../../src/extra/tre/tre-ast.h \
 ../../../../src/extra/tre/tre-compile.h \
 ../../../../src/extra/tre/tre-parse.h \
 ../../../../src/extra/tre/xmalloc.h
tre-match-approx.o: ../../../../src/extra/tre/tre-match-approx.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-match-utils.h \
 ../../../../src/extra/tre/xmalloc.h
tre-match-backtrack.o: ../../../../src/extra/tre/tre-match-backtrack.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-mem.h \
 ../../../../src/extra/tre/tre-match-utils.h \
 ../../../../src/extra/tre/xmalloc.h
tre-match-parallel.o: ../../../../src/extra/tre/tre-match-parallel.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-match-utils.h \
 ../../../../src/extra/tre/xmalloc.h
tre-mem.o: ../../../../src/extra/tre/tre-mem.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-mem.h ../../../../src/extra/tre/xmalloc.h
tre-parse.o: ../../../../src/extra/tre/tre-parse.c \
 ../../../src/include/config.h ../../../../src/extra/tre/xmalloc.h \
 ../../../../src/extra/tre/tre-mem.h ../../../../src/extra/tre/tre-ast.h \
 ../../../../src/extra/tre/tre-internal.h ../../../../src/extra/tre/tre.h \
 ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-compile.h \
 ../../../../src/extra/tre/tre-stack.h \
 ../../../../src/extra/tre/tre-parse.h
tre-stack.o: ../../../../src/extra/tre/tre-stack.c \
 ../../../src/include/config.h ../../../../src/extra/tre/tre-internal.h \
 ../../../../src/extra/tre/tre.h ../../../../src/extra/tre/tre-config.h \
 ../../../../src/extra/tre/tre-stack.h \
 ../../../../src/extra/tre/xmalloc.h
xmalloc.o: ../../../../src/extra/tre/xmalloc.c \
 ../../../src/include/config.h ../../../../src/extra/tre/xmalloc.h
