#
# ${R_HOME}/src/extra/blas/Makefile

VPATH = ../../../../src/extra/blas
srcdir = ../../../../src/extra/blas
top_srcdir = ../../../..

top_builddir = ../../..
subdir = src/extra/blas
R_HOME = $(top_builddir)

include $(top_builddir)/Makeconf

ALL_CFLAGS = $(ALL_CFLAGS_LO)
ALL_FFLAGS = $(ALL_FFLAGS_LO)

SOURCES = blas00.c blas.f cmplxblas.f

Rblas_la = libRblas$(DYLIB_EXT)
##  is used on Mac OS X
## first for internal BLAS
Rblas_la_LIBADD =  $(FLIBS_IN_SO)
## then external one
Rblas_la_LIBADD0 = 

all: Makefile  R

Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status $(SOURCES_C)
	@cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@

R:
	@$(MAKE) $(Rblas_la)
	@$(MAKE) rhome="$(abs_top_builddir)" Rblas_install

blas_OBJS=blas.o  cmplxblas.o
$(Rblas_la): $(blas_OBJS) # xerbla.o
	$(DYLIB_LINK) -o $(Rblas_la) $(blas_OBJS) $(Rblas_la_LIBADD) # xerbla.o

#$(Rblas_la): blas00.o
#	$(DYLIB_LINK) -o $(Rblas_la) $^  $(Rblas_la_LIBADD0)

Rblas_install: $(Rblas_la)
	@$(MKINSTALLDIRS) $(DESTDIR)$(Rexeclibdir)
	@$(SHELL) $(top_srcdir)/tools/copy-if-change $(Rblas_la) \
	  $(DESTDIR)$(Rexeclibdir)/$(Rblas_la)

Rblas_install-strip: $(Rblas_la)
	@$(MKINSTALLDIRS) $(DESTDIR)$(Rexeclibdir)
	@$(INSTALL) $(Rblas_la) $(DESTDIR)$(Rexeclibdir)/$(Rblas_la)
	@if test -n "$(STRIP_LIBS)"; then \
	  $(STRIP_LIBS) "$(DESTDIR)$(Rexeclibdir)/$(Rblas_la)" ;\
	fi

mostlyclean: clean
clean:
	@-rm -f *.o $(Rblas_la)
distclean: clean
	@-rm -f Makefile
maintainer-clean: distclean

install:  Rblas_install
install-strip:  Rblas_install-strip

uninstall TAGS info dvi check:

distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = Makefile.in Makefile.win Rblas.def \
  $(SOURCES) $(HEADERS) xerbla.c

distdir: $(DISTFILES)
	@for f in $(DISTFILES); do \
	  test -f $(distdir)/$${f} \
	    || ln $(srcdir)/$${f} $(distdir)/$${f} 2>/dev/null \
	    || cp -p $(srcdir)/$${f} $(distdir)/$${f}; \
	done

