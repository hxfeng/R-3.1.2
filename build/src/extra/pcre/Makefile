#
# ${R_HOME}/src/extra/pcre/Makefile

VPATH = ../../../../src/extra/pcre
srcdir = ../../../../src/extra/pcre
top_srcdir = ../../../..

top_builddir = ../../..
subdir = src/extra/pcre
R_HOME = $(top_builddir)

include $(top_builddir)/Makeconf

PCRE_CPPFLAGS = -I$(srcdir)
ALL_CPPFLAGS = $(PCRE_CPPFLAGS) $(R_XTRA_CPPFLAGS) $(CPPFLAGS) $(DEFS)

SOURCES = pcre_chartables.c pcre_compile.c pcre_config.c pcre_exec.c \
	pcre_fullinfo.c pcre_get.c pcre_globals.c pcre_jit_compile.c \
	pcre_maketables.c pcre_newline.c pcre_ord2utf8.c pcre_refcount.c \
	pcre_study.c pcre_tables.c pcre_ucd.c \
	pcre_valid_utf8.c pcre_version.c pcre_xclass.c

HEADERS = pcre_internal.h pcre.h ucp.h
DEPENDS = $(SOURCES:.c=.d)
OBJECTS = $(SOURCES:.c=.o)
#ALL_CFLAGS = $(ALL_CFLAGS_LO) -fvisibility=hidden

distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = LICENCE Makefile.in Makefile.win R_changes \
  $(SOURCES) $(HEADERS)

SUBDIRS_WITH_NO_BUILD = sljit


noinst_LIBRARIES =  libpcre.a
libpcre_a_SOURCES = $(SOURCES)
libpcre_a_OBJECTS = $(OBJECTS)


all: R

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

libpcre.a: $(libpcre_a_OBJECTS)
	rm -f $@
	$(AR) cr $@ $(libpcre_a_OBJECTS)
	$(RANLIB) $@

mostlyclean: clean
clean:
	@-rm -f Makedeps *.d *.o *.lo *.a
distclean: clean
	@-rm -f Makefile
maintainer-clean: distclean

install install-strip uninstall TAGS info dvi check:

distdir: $(DISTFILES)
	@for f in $(DISTFILES); do \
	  test -f $(distdir)/$${f} \
	    || ln $(srcdir)/$${f} $(distdir)/$${f} 2>/dev/null \
	    || cp -p $(srcdir)/$${f} $(distdir)/$${f}; \
	done
	@for d in $(SUBDIRS_WITH_NO_BUILD); do \
	  ((cd $(srcdir); $(TAR) -c -f - --exclude=.svn --exclude=CVS $${d}) \
	      | (cd $(distdir); $(TAR) -x -f -)) \
	    || exit 1; \
	done

## Automagically generated dependencies:

pcre_chartables.o: ../../../../src/extra/pcre/pcre_chartables.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_compile.o: ../../../../src/extra/pcre/pcre_compile.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_config.o: ../../../../src/extra/pcre/pcre_config.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_exec.o: ../../../../src/extra/pcre/pcre_exec.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_fullinfo.o: ../../../../src/extra/pcre/pcre_fullinfo.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_get.o: ../../../../src/extra/pcre/pcre_get.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_globals.o: ../../../../src/extra/pcre/pcre_globals.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_jit_compile.o: ../../../../src/extra/pcre/pcre_jit_compile.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h \
 ../../../../src/extra/pcre/sljit/sljitLir.c \
 ../../../../src/extra/pcre/sljit/sljitLir.h \
 ../../../../src/extra/pcre/sljit/sljitConfig.h \
 ../../../../src/extra/pcre/sljit/sljitConfigInternal.h \
 ../../../../src/extra/pcre/sljit/sljitUtils.c \
 ../../../../src/extra/pcre/sljit/sljitExecAllocator.c \
 ../../../../src/extra/pcre/sljit/sljitNativeX86_common.c \
 ../../../../src/extra/pcre/sljit/sljitNativeX86_64.c
pcre_maketables.o: ../../../../src/extra/pcre/pcre_maketables.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_newline.o: ../../../../src/extra/pcre/pcre_newline.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_ord2utf8.o: ../../../../src/extra/pcre/pcre_ord2utf8.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_refcount.o: ../../../../src/extra/pcre/pcre_refcount.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_study.o: ../../../../src/extra/pcre/pcre_study.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_tables.o: ../../../../src/extra/pcre/pcre_tables.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_ucd.o: ../../../../src/extra/pcre/pcre_ucd.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_valid_utf8.o: ../../../../src/extra/pcre/pcre_valid_utf8.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_version.o: ../../../../src/extra/pcre/pcre_version.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
pcre_xclass.o: ../../../../src/extra/pcre/pcre_xclass.c \
 ../../../src/include/config.h ../../../../src/extra/pcre/pcre_internal.h \
 ../../../../src/extra/pcre/pcre.h ../../../../src/extra/pcre/ucp.h
