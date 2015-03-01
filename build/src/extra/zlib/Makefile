#
# ${R_HOME}/src/extra/zlib/Makefile

VPATH = ../../../../src/extra/zlib
srcdir = ../../../../src/extra/zlib
top_srcdir = ../../../..

top_builddir = ../../..
subdir = src/extra/zlib
R_HOME = $(top_builddir)

include $(top_builddir)/Makeconf

ZLIB_CPPFLAGS = -I$(srcdir)  -DUSE_MMAP
ALL_CPPFLAGS = $(ZLIB_CPPFLAGS) $(R_XTRA_CPPFLAGS) $(CPPFLAGS) $(DEFS)
## need to be PIC for use in grDevices
ALL_CFLAGS = $(R_XTRA_CFLAGS) $(R_OPENMP_CFLAGS) $(MAIN_CFLAGS) $(CFLAGS) $(CPICFLAGS)

SOURCES = adler32.c compress.c crc32.c deflate.c infback.c \
  inffast.c inflate.c inftrees.c trees.c uncompr.c zutil.c
HEADERS = crc32.h deflate.h inffast.h inffixed.h inflate.h inftrees.h \
  trees.h zconf.h zlib.h zutil.h
DEPENDS = $(SOURCES:.c=.d)
OBJECTS = $(SOURCES:.c=.o)
#ALL_CFLAGS = $(ALL_CFLAGS_LO) -fvisibility=hidden


distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = R_changes README Makefile.in Makefile.win Rzlib.def \
  $(SOURCES) $(HEADERS)
noinst_LIBRARIES =  libz.a
libz_a_SOURCES = $(SOURCES)
libz_a_OBJECTS = $(OBJECTS)


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

libz.a: $(libz_a_OBJECTS)
	rm -f $@
	$(AR) cr $@ $(libz_a_OBJECTS)
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

adler32.o: ../../../../src/extra/zlib/adler32.c \
 ../../../../src/extra/zlib/zutil.h ../../../../src/extra/zlib/zlib.h \
 ../../../../src/extra/zlib/zconf.h ../../../src/include/config.h
compress.o: ../../../../src/extra/zlib/compress.c \
 ../../../../src/extra/zlib/zlib.h ../../../../src/extra/zlib/zconf.h \
 ../../../src/include/config.h
crc32.o: ../../../../src/extra/zlib/crc32.c \
 ../../../../src/extra/zlib/zutil.h ../../../../src/extra/zlib/zlib.h \
 ../../../../src/extra/zlib/zconf.h ../../../src/include/config.h \
 ../../../../src/extra/zlib/crc32.h
deflate.o: ../../../../src/extra/zlib/deflate.c \
 ../../../../src/extra/zlib/deflate.h ../../../../src/extra/zlib/zutil.h \
 ../../../../src/extra/zlib/zlib.h ../../../../src/extra/zlib/zconf.h \
 ../../../src/include/config.h
infback.o: ../../../../src/extra/zlib/infback.c \
 ../../../../src/extra/zlib/zutil.h ../../../../src/extra/zlib/zlib.h \
 ../../../../src/extra/zlib/zconf.h ../../../src/include/config.h \
 ../../../../src/extra/zlib/inftrees.h \
 ../../../../src/extra/zlib/inflate.h \
 ../../../../src/extra/zlib/inffast.h \
 ../../../../src/extra/zlib/inffixed.h
inffast.o: ../../../../src/extra/zlib/inffast.c \
 ../../../../src/extra/zlib/zutil.h ../../../../src/extra/zlib/zlib.h \
 ../../../../src/extra/zlib/zconf.h ../../../src/include/config.h \
 ../../../../src/extra/zlib/inftrees.h \
 ../../../../src/extra/zlib/inflate.h \
 ../../../../src/extra/zlib/inffast.h
inflate.o: ../../../../src/extra/zlib/inflate.c \
 ../../../../src/extra/zlib/zutil.h ../../../../src/extra/zlib/zlib.h \
 ../../../../src/extra/zlib/zconf.h ../../../src/include/config.h \
 ../../../../src/extra/zlib/inftrees.h \
 ../../../../src/extra/zlib/inflate.h \
 ../../../../src/extra/zlib/inffast.h \
 ../../../../src/extra/zlib/inffixed.h
inftrees.o: ../../../../src/extra/zlib/inftrees.c \
 ../../../../src/extra/zlib/zutil.h ../../../../src/extra/zlib/zlib.h \
 ../../../../src/extra/zlib/zconf.h ../../../src/include/config.h \
 ../../../../src/extra/zlib/inftrees.h
trees.o: ../../../../src/extra/zlib/trees.c \
 ../../../../src/extra/zlib/deflate.h ../../../../src/extra/zlib/zutil.h \
 ../../../../src/extra/zlib/zlib.h ../../../../src/extra/zlib/zconf.h \
 ../../../src/include/config.h ../../../../src/extra/zlib/trees.h
uncompr.o: ../../../../src/extra/zlib/uncompr.c \
 ../../../../src/extra/zlib/zlib.h ../../../../src/extra/zlib/zconf.h \
 ../../../src/include/config.h
zutil.o: ../../../../src/extra/zlib/zutil.c \
 ../../../../src/extra/zlib/zutil.h ../../../../src/extra/zlib/zlib.h \
 ../../../../src/extra/zlib/zconf.h ../../../src/include/config.h
