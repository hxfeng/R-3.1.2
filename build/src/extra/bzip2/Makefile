#
# ${R_HOME}/src/extra/bzip2/Makefile

VPATH = ../../../../src/extra/bzip2
srcdir = ../../../../src/extra/bzip2
top_srcdir = ../../../..

top_builddir = ../../..
subdir = src/extra/bzip2
R_HOME = $(top_builddir)

include $(top_builddir)/Makeconf

BZIP2_CPPFLAGS = -I$(srcdir)
ALL_CPPFLAGS = $(BZIP2_CPPFLAGS) $(R_XTRA_CPPFLAGS) $(CPPFLAGS) $(DEFS)

SOURCES = blocksort.c bzlib.c bzcompress.c crctable.c decompress.c \
  huffman.c randtable.c
HEADERS = bzlib.h bzlib_private.h
DEPENDS = $(SOURCES:.c=.d)
OBJECTS = $(SOURCES:.c=.o)
#ALL_CFLAGS = $(ALL_CFLAGS_LO) -fvisibility=hidden

distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = LICENSE Makefile.in Makefile.win R_changes \
  $(SOURCES) $(HEADERS)
noinst_LIBRARIES = libbz2.a
#noinst_LIBRARIES =  libbz2.a
libbz2_a_SOURCES = $(SOURCES)
libbz2_a_OBJECTS = $(OBJECTS)


all: R

Makefile: $(srcdir)/Makefile.in \
  $(top_builddir)/config.status \
  $(SOURCES)
	@cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@

Makedeps: Makefile $(DEPENDS)
	@cat $(DEPENDS) >> Makefile
	@touch $@

R: Makedeps
	@$(MAKE) $(noinst_LIBRARIES)

libbz2.a: $(libbz2_a_OBJECTS)
	rm -f $@
	$(AR) cr $@ $(libbz2_a_OBJECTS)
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

## Automagically generated dependencies:

blocksort.o: ../../../../src/extra/bzip2/blocksort.c \
 ../../../../src/extra/bzip2/bzlib_private.h \
 ../../../src/include/config.h ../../../../src/extra/bzip2/bzlib.h
bzlib.o: ../../../../src/extra/bzip2/bzlib.c \
 ../../../../src/extra/bzip2/bzlib_private.h \
 ../../../src/include/config.h ../../../../src/extra/bzip2/bzlib.h
bzcompress.o: ../../../../src/extra/bzip2/bzcompress.c \
 ../../../../src/extra/bzip2/bzlib_private.h \
 ../../../src/include/config.h ../../../../src/extra/bzip2/bzlib.h
crctable.o: ../../../../src/extra/bzip2/crctable.c \
 ../../../../src/extra/bzip2/bzlib_private.h \
 ../../../src/include/config.h ../../../../src/extra/bzip2/bzlib.h
decompress.o: ../../../../src/extra/bzip2/decompress.c \
 ../../../../src/extra/bzip2/bzlib_private.h \
 ../../../src/include/config.h ../../../../src/extra/bzip2/bzlib.h
huffman.o: ../../../../src/extra/bzip2/huffman.c \
 ../../../../src/extra/bzip2/bzlib_private.h \
 ../../../src/include/config.h ../../../../src/extra/bzip2/bzlib.h
randtable.o: ../../../../src/extra/bzip2/randtable.c \
 ../../../../src/extra/bzip2/bzlib_private.h \
 ../../../src/include/config.h ../../../../src/extra/bzip2/bzlib.h
