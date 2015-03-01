#
# ${R_HOME}/src/main/Makefile

VPATH = ../../../src/main
srcdir = ../../../src/main
top_srcdir = ../../..

top_builddir = ../..
subdir = src/main
# next is needed for shared BLAS
R_HOME=$(top_builddir)

include $(top_builddir)/Makeconf

SOURCES_C = \
	CommandLineArgs.c \
	Rdynload.c Renviron.c RNG.c \
	agrep.c apply.c arithmetic.c array.c attrib.c \
	bind.c builtin.c \
	character.c coerce.c colors.c complex.c connections.c context.c cum.c \
	dcf.c datetime.c debug.c deparse.c devices.c \
	dotcode.c dounzip.c dstruct.c duplicate.c \
	edit.c engine.c envir.c errors.c eval.c \
	format.c \
	gevents.c gram.c gram-ex.c graphics.c grep.c \
	identical.c inlined.c inspect.c internet.c iosupport.c \
	lapack.c list.c localecharset.c logic.c \
	main.c mapply.c match.c memory.c \
	names.c \
	objects.c options.c \
	paste.c platform.c plot.c plot3d.c plotmath.c \
	print.c printarray.c printvector.c printutils.c qsort.c \
	random.c raw.c registration.c relop.c rlocale.c \
	saveload.c scan.c seq.c serialize.c sort.c source.c split.c \
	sprintf.c startup.c subassign.c subscript.c subset.c summary.c sysutils.c \
	times.c \
	unique.c util.c \
	version.c vfonts.c

SOURCES_F =  xxxpr.f

## If the substitutes are needed, the corresponding objects are put by
## configure in  
EXTRA_SOURCES_C = \
	Rmain.c alloca.c mkdtemp.c strdup.c strncasecmp.c

DEPENDS = $(SOURCES_C:.c=.d) $(EXTRA_SOURCES_C:.c=.d)
SOURCES = $(SOURCES_C) $(SOURCES_F)
OBJECTS = $(SOURCES_C:.c=.o) $(SOURCES_F:.f=.o)  
HEADERS = \
	RBufferUtils.h Rstrptime.h \
	arithmetic.h \
	basedecl.h \
	contour-common.h \
	datetime.h \
	gzio.h \
	qsort-body.c \
	rlocale_data.h \
	unzip.h \
	valid_utf8.h \
	xspline.c

distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = Makefile.in Makefile.win \
	$(HEADERS) \
	$(SOURCES_C) \
	$(EXTRA_SOURCES_C) \
	$(SOURCES_F) \
	gram.y

ZLIB_CPPFLAGS =  -I$(top_srcdir)/src/extra/zlib
BZLIB_CPPFLAGS =  -I$(top_srcdir)/src/extra/bzip2
PCRE_CPPFLAGS =  -I$(top_srcdir)/src/extra/pcre
TRE_CPPFLAGS =  -I$(top_srcdir)/src/extra
XDR_CPPFLAGS = # -I$(top_srcdir)/src/extra/xdr
XDR_CPPFLAGS = 
XZ_CPPFLAGS = #  -I$(top_srcdir)/src/extra/xz/api

ALL_CPPFLAGS = $(ZLIB_CPPFLAGS) $(BZLIB_CPPFLAGS) $(PCRE_CPPFLAGS) \
  $(TRE_CPPFLAGS) $(XDR_CPPFLAGS) $(XZ_CPPFLAGS) $(R_XTRA_CPPFLAGS) $(CPPFLAGS) $(DEFS)
#ALL_CFLAGS = $(ALL_CFLAGS_LO)
#ALL_FFLAGS = $(ALL_FFLAGS_LO)


## use an explicit library: there might be an unsatisfactory -lz around
R_ZLIBS =  ../extra/zlib/libz.a
R_BZLIBS =  ../extra/bzip2/libbz2.a
R_PCRE =  ../extra/pcre/libpcre.a
R_TRE =  ../extra/tre/libtre.a
R_XDR = # ../extra/xdr/libxdr.a
R_XZ = #  ../extra/xz/liblzma.a
R_LIBINTL = # ../extra/intl/libintl.a
R_TZONE = # ../extra/tzone/libtz.a

MAIN_LIBS = ../unix/libunix.a ../appl/libappl.a ../nmath/libnmath.a
MAIN_OBJS = `ls ../unix/*.o ../appl/*.o ../nmath/*.o`
EXTRA_STATIC_LIBS = \
  $(R_ZLIBS) $(R_BZLIBS) $(R_PCRE) $(R_TRE) $(R_XDR) $(R_XZ) $(R_LIBINTL) $(R_TZONE)
STATIC_LIBS = $(MAIN_LIBS) $(EXTRA_STATIC_LIBS)

EXTRA_LIBS = $(BLAS_LIBS) $(FLIBS) $(R_XTRA_LIBS)  $(READLINE_LIBS) $(LIBS)

R_binary = R.bin
R_bin_OBJECTS = Rmain.o $(OBJECTS)
R_bin_LDADD = $(MAIN_OBJS) $(EXTRA_STATIC_LIBS) $(EXTRA_LIBS)
## Linked against -lRblas becasue -lR is and otherwise ld complains.
#R_bin_LDADD = -lR -lRblas
R_bin_DEPENDENCIES = libR.a # $(top_builddir)/etc/R.exp

libR_la = libR$(DYLIB_EXT)
libR_la_OBJECTS = $(OBJECTS)
libR_la_LIBADD =  $(MAIN_OBJS) $(EXTRA_STATIC_LIBS) $(EXTRA_LIBS) # # -Wl,-bE:$(top_builddir)/etc/R.exp
libR_la_DEPENDENCIES = $(STATIC_LIBS) $(R_TZONE) # # $(top_builddir)/etc/R.exp

## The next is needed for OS X only at present
LIBR_LDFLAGS = 


all: R

Makefile: $(srcdir)/Makefile.in \
  $(top_builddir)/config.status \
  ../include/config.h \
  ../include/Rversion.h \
  $(SOURCES_C) $(EXTRA_SOURCES_C)
	@cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@

Makedeps: Makefile $(DEPENDS)
	@cat $(DEPENDS) >> Makefile
	@touch $@

## This target has been changed to ensure that R.bin and libR get
## installed in the build tree if necessary, even if the corresponding 
## objects are not re-made.
## Note that dependencies in the test Makefiles used to depend on these objects,
## so copy-if-change is used.
R: Makedeps
#	@$(MAKE) install-lib-local
#	@$(MAKE) install-static-local
	@$(MAKE) install-bin-local


## is this portable?  Documented as GNU extension.
../include/config.h ../include/Rversion.h:
	(cd $(@D); $(MAKE) $(@F))

$(R_binary): $(R_bin_OBJECTS) $(R_bin_DEPENDENCIES)
	$(MAIN_LINK) -o $@ $(R_bin_OBJECTS) $(R_bin_LDADD)

libR.a: $(OBJECTS) $(STATIC_LIBS)
	-@mkdir libs
	@(cd libs; for l in $(STATIC_LIBS); do $(AR) x ../$$l; done)
	@rm -rf $@
	$(AR) cr $@ $(OBJECTS) libs/*o
	$(RANLIB) $@
	@rm -rf libs

install-bin-local: $(R_binary)
	@$(MAKE) rhome="$(abs_top_builddir)" install-bin

install-static-local: libR.a
	@$(MAKE) rhome="$(abs_top_builddir)" install-static

$(top_builddir)/etc/R.exp: $(OBJECTS) $(MAIN_LIBS)
	@$(SHELL) $(top_srcdir)/tools/ldAIX4 -o $@ $(OBJECTS) $(MAIN_LIBS)

## is this portable?  Documented as GNU extension.
$(MAIN_LIBS):
	(cd $(@D); $(MAKE) $(@F))

../extra/bzip2/libbz2.a ../extra/pcre/libpcre.a ../extra/pcre/libtre.a\
  ../extra/xdr/libxdr.a ../extra/zlib/libz.a ../extra/xv/liblzma.a \
  ../extra/intl/libintl.a:
	(cd $(@D); $(MAKE))


libR: $(libR_la)

$(libR_la): $(libR_la_OBJECTS) $(libR_la_DEPENDENCIES)
	$(DYLIB_LINK) $(LIBR_LDFLAGS) -o $@ $(libR_la_OBJECTS) $(libR_la_LIBADD)

install-lib-local: $(libR_la)
	@$(MAKE) rhome="$(abs_top_builddir)" install-lib


# suppress #line directives
YFLAGS=-l

$(srcdir)/gram.c: # $(srcdir)/gram.y
	@$(ECHO) "re-making gram.c"
	$(YACC) $(YFLAGS) $(srcdir)/gram.y
	$(SHELL) $(top_srcdir)/tools/move-if-change y.tab.c $(srcdir)/gram.c	

install: installdirs
	@$(MAKE) install-bin
	@if test -f $(libR_la); then $(MAKE) install-lib; fi
#	@$(MAKE) install-static
## may not need $(rhome)/lib if not static/shared libR, external blas and lapack.
installdirs:
	@$(MKINSTALLDIRS) "$(DESTDIR)$(Rexecbindir2)"
install-bin: installdirs
	@$(SHELL) $(top_srcdir)/tools/copy-if-change $(R_binary) "$(DESTDIR)$(Rexecbindir2)/R"
install-lib: installdirs
	@$(MKINSTALLDIRS) "$(DESTDIR)$(Rexeclibdir)"
	@$(SHELL) $(top_srcdir)/tools/copy-if-change $(libR_la) "$(DESTDIR)$(Rexeclibdir)/$(libR_la)"
install-static: installdirs
	@$(MKINSTALLDIRS) "$(DESTDIR)$(Rexeclibdir)"
	@$(SHELL) $(top_srcdir)/tools/copy-if-change libR.a "$(DESTDIR)$(Rexeclibdir)/libR.a"
install-strip: installdirs
	@${INSTALL_PROGRAM} -s $(R_binary) "$(DESTDIR)$(Rexecbindir2)/R"
	@if test -f $(libR_la); then $(MAKE) install-lib; fi
	@if test -n "$(STRIP_LIBS)"; then \
	  if test -f $(libR_la); then $(STRIP_LIBS) "$(DESTDIR)$(Rexeclibdir)/$(libR_la)"; fi; \
	fi
#	@$(MAKE) install-strip-static
install-strip-static: installdirs
	@$(MAKE) install-static
	@if test -n "$(STRIP_STATIC_LIBS)"; then \
	  if test -f libR.a; then $(STRIP_STATIC_LIBS) "$(DESTDIR)$(Rexeclibdir)/libR.a"; fi; \
	fi
uninstall:
	@rm -f "$(DESTDIR)$(Rexecbindir)/exec/$(R_ARCH)/R" "$(DESTDIR)$(Rexecbindir)/R.bin"
	@rm -f "$(DESTDIR)$(Rexeclibdir)/libR$(DYLIB_EXT)"
	@rm -f "$(DESTDIR)$(Rexeclibdir)/libR.a"

mostlyclean: clean
clean:
	@-rm -f $(top_builddir)/etc/R.exp
	@-rm -rf .libs _libs
	@-rm -f *core Makedeps *.d *.o *.lo *.la *$(DYLIB_EXT) \
	  $(R_binary) libR.a
distclean: clean
	@-rm -f Makefile
maintainer-clean: distclean
	@$(ECHO) "This command is intended for maintainers to use; it"
	@$(ECHO) "deletes files that may need special rules to rebuild"
	@-rm -f $(srcdir)/gram.c $(srcdir)/gramLatex.c $(srcdir)/gramRd.c

tags: TAGS
TAGS: $(SOURCES) $(EXTRA_SOURCES_C) $(HEADERS)
	etags $(SOURCES) $(EXTRA_SOURCES_C) $(HEADERS)

## Unused targets
info dvi check:

distdir: $(DISTFILES)
	@for f in $(DISTFILES); do \
	  test -f $(distdir)/$${f} \
	    || ln $(srcdir)/$${f} $(distdir)/$${f} 2>/dev/null \
	    || cp -p $(srcdir)/$${f} $(distdir)/$${f}; \
	done

## Automagically generated dependencies:

CommandLineArgs.o: ../../../src/main/CommandLineArgs.c \
 ../../src/include/config.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/Complex.h ../../../src/include/Rinternals.h \
 ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/R_ext/RStartup.h
Rdynload.o: ../../../src/main/Rdynload.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/Rdynpriv.h \
 ../../../src/include/R_ext/Rdynload.h
Renviron.o: ../../../src/main/Renviron.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Rinterface.h \
 ../../../src/include/R_ext/RStartup.h ../../../src/include/Fileio.h
RNG.o: ../../../src/main/RNG.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/Random.h \
 ../../../src/include/R_ext/Rdynload.h
agrep.o: ../../../src/main/agrep.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/extra/tre/tre.h ../../../src/extra/tre/tre-config.h
apply.o: ../../../src/main/apply.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
arithmetic.o: ../../../src/main/arithmetic.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Itermacros.h \
 ../../../src/main/arithmetic.h
array.o: ../../../src/main/array.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h ../../../src/include/R_ext/Applic.h \
 ../../../src/include/R_ext/BLAS.h
attrib.o: ../../../src/main/attrib.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h
bind.o: ../../../src/main/bind.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/main/RBufferUtils.h
builtin.o: ../../../src/main/builtin.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/include/Fileio.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h
character.o: ../../../src/main/character.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/include/rlocale.h ../../../src/main/RBufferUtils.h
coerce.o: ../../../src/main/coerce.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/Print.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/PrtUtil.h
colors.o: ../../../src/main/colors.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h
complex.o: ../../../src/main/complex.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/main/arithmetic.h
connections.o: ../../../src/main/connections.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Fileio.h ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h \
 ../../../src/include/R_ext/R-ftp-http.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h ../../../src/include/R_ext/Riconv.h \
 ../../../src/main/gzio.h ../../../src/extra/zlib/zlib.h \
 ../../../src/extra/zlib/zconf.h ../../../src/extra/bzip2/bzlib.h
context.o: ../../../src/main/context.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
cum.o: ../../../src/main/cum.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
dcf.o: ../../../src/main/dcf.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h ../../../src/extra/tre/tre.h \
 ../../../src/extra/tre/tre-config.h
datetime.o: ../../../src/main/datetime.c ../../src/include/config.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Error.h ../../../src/include/R_ext/Memory.h \
 ../../../src/include/R_ext/Utils.h ../../../src/include/R_ext/Print.h \
 ../../../src/include/Rinlinedfuns.h ../../../src/include/Errormsg.h \
 ../../../src/include/Internal.h ../../../src/main/Rstrptime.h
debug.o: ../../../src/main/debug.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
deparse.o: ../../../src/main/deparse.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/include/Fileio.h \
 ../../../src/main/RBufferUtils.h ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h
devices.o: ../../../src/main/devices.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Graphics.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h \
 ../../../src/include/Rgraphics.h ../../../src/include/GraphicsBase.h
dotcode.o: ../../../src/main/dotcode.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/Rdynpriv.h \
 ../../../src/include/R_ext/Rdynload.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h
dounzip.o: ../../../src/main/dounzip.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Fileio.h \
 ../../../src/main/unzip.h ../../../src/extra/zlib/zlib.h \
 ../../../src/extra/zlib/zconf.h ../../../src/extra/bzip2/bzlib.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h
dstruct.o: ../../../src/main/dstruct.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
duplicate.o: ../../../src/main/duplicate.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h
edit.o: ../../../src/main/edit.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/include/Fileio.h \
 ../../../src/include/Parse.h ../../../src/include/R_ext/Parse.h \
 ../../../src/include/IOStuff.h ../../../src/include/Rinterface.h \
 ../../../src/include/R_ext/RStartup.h
engine.o: ../../../src/main/engine.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h \
 ../../../src/include/R_ext/Applic.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h ../../../src/include/R_ext/BLAS.h \
 ../../src/include/Rmath.h ../../../src/include/rlocale.h \
 ../../../src/main/xspline.c
envir.o: ../../../src/main/envir.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/Callbacks.h
errors.o: ../../../src/main/errors.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Startup.h ../../../src/include/R_ext/RStartup.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h \
 ../../../src/include/Rinterface.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h ../../src/include/Rmath.h \
 ../../../src/include/rlocale.h
eval.o: ../../../src/main/eval.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Rinterface.h ../../../src/include/R_ext/RStartup.h \
 ../../../src/include/Fileio.h
format.o: ../../../src/main/format.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../src/include/Rmath.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h
gevents.o: ../../../src/main/gevents.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../src/include/Rmath.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h
gram.o: ../../../src/main/gram.c ../../src/include/config.h \
 ../../../src/include/IOStuff.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/Complex.h ../../../src/include/Rinternals.h \
 ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Fileio.h \
 ../../../src/include/Parse.h ../../../src/include/R_ext/Parse.h \
 ../../../src/include/rlocale.h ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h
gram-ex.o: ../../../src/main/gram-ex.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
graphics.o: ../../../src/main/graphics.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Graphics.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h \
 ../../../src/include/Rgraphics.h ../../src/include/Rmath.h
grep.o: ../../../src/main/grep.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/extra/tre/tre.h ../../../src/extra/tre/tre-config.h \
 ../../../src/extra/pcre/pcre.h
identical.o: ../../../src/main/identical.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
inlined.o: ../../../src/main/inlined.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
inspect.o: ../../../src/main/inspect.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
internet.o: ../../../src/main/internet.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h ../../../src/include/Rdynpriv.h \
 ../../../src/include/R_ext/Rdynload.h \
 ../../../src/include/R_ext/R-ftp-http.h \
 ../../../src/include/Rmodules/Rinternet.h
iosupport.o: ../../../src/main/iosupport.c ../../src/include/config.h \
 ../../../src/include/IOStuff.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/Complex.h ../../../src/include/Rinternals.h \
 ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
lapack.o: ../../../src/main/lapack.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Rdynpriv.h \
 ../../../src/include/R_ext/Rdynload.h \
 ../../../src/include/Rmodules/Rlapack.h
list.o: ../../../src/main/list.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
localecharset.o: ../../../src/main/localecharset.c \
 ../../src/include/config.h
logic.o: ../../../src/main/logic.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
main.o: ../../../src/main/main.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Errormsg.h \
 ../../../src/include/Internal.h ../../../src/include/Rinterface.h \
 ../../../src/include/R_ext/RStartup.h ../../../src/include/IOStuff.h \
 ../../../src/include/Fileio.h ../../../src/include/Parse.h \
 ../../../src/include/R_ext/Parse.h ../../../src/include/Startup.h \
 ../../../src/include/R_ext/Callbacks.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h
mapply.o: ../../../src/main/mapply.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
match.o: ../../../src/main/match.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
memory.o: ../../../src/main/memory.c ../../src/include/config.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/include/R_ext/Error.h ../../../src/include/R_ext/Print.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Memory.h \
 ../../../src/include/R_ext/Utils.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h \
 ../../../src/include/R_ext/Rdynload.h \
 ../../../src/include/R_ext/Rallocators.h ../../src/include/Rmath.h \
 ../../../src/main/RBufferUtils.h
names.o: ../../../src/main/names.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/main/arithmetic.h \
 ../../../src/include/Rinterface.h ../../../src/include/R_ext/RStartup.h
objects.o: ../../../src/main/objects.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h
options.o: ../../../src/main/options.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h
paste.o: ../../../src/main/paste.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/main/RBufferUtils.h
platform.o: ../../../src/main/platform.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Rinterface.h ../../../src/include/R_ext/RStartup.h \
 ../../../src/include/Fileio.h ../../../src/extra/tre/tre.h \
 ../../../src/extra/tre/tre-config.h
plot.o: ../../../src/main/plot.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Graphics.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h \
 ../../../src/include/Rgraphics.h ../../../src/include/Print.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/PrtUtil.h \
 ../../src/include/Rmath.h
plot3d.o: ../../../src/main/plot3d.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/Graphics.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h \
 ../../../src/include/Rgraphics.h ../../../src/include/Print.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/PrtUtil.h \
 ../../../src/main/contour-common.h
plotmath.o: ../../../src/main/plotmath.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/rlocale.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h
print.o: ../../../src/main/print.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/include/Fileio.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h ../../../src/include/S.h \
 ../../src/include/Rconfig.h ../../../src/include/R_ext/Constants.h \
 ../../../src/include/R_ext/RS.h
printarray.o: ../../../src/main/printarray.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Print.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/PrtUtil.h
printvector.o: ../../../src/main/printvector.c ../../src/include/config.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/Complex.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Print.h \
 ../../../src/include/Defn.h ../../../src/include/Errormsg.h \
 ../../../src/include/R_ext/PrtUtil.h
printutils.o: ../../../src/main/printutils.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../src/include/Rmath.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h \
 ../../../src/main/RBufferUtils.h ../../../src/include/rlocale.h
qsort.o: ../../../src/main/qsort.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h ../../../src/main/qsort-body.c
random.o: ../../../src/main/random.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/R_ext/Random.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/Internal.h
raw.o: ../../../src/main/raw.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h
registration.o: ../../../src/main/registration.c \
 ../../src/include/config.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/Complex.h ../../../src/include/Rinternals.h \
 ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/R_ext/Rdynload.h \
 ../../../src/include/R_ext/Applic.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h ../../../src/include/R_ext/BLAS.h \
 ../../../src/include/R_ext/Linpack.h \
 ../../../src/include/R_ext/Callbacks.h ../../../src/include/Rdynpriv.h \
 ../../../src/main/basedecl.h
relop.o: ../../../src/main/relop.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h
rlocale.o: ../../../src/main/rlocale.c ../../src/include/config.h \
 ../../../src/include/rlocale.h ../../../src/main/rlocale_data.h \
 ../../../src/include/R_ext/Riconv.h
saveload.o: ../../../src/main/saveload.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Rinterface.h ../../../src/include/R_ext/RStartup.h \
 ../../src/include/Rmath.h ../../../src/include/Fileio.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/main/RBufferUtils.h ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h
scan.o: ../../../src/main/scan.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Fileio.h ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h ../../../src/include/Print.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/PrtUtil.h \
 ../../../src/include/rlocale.h ../../../src/main/RBufferUtils.h
seq.o: ../../../src/main/seq.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/main/RBufferUtils.h
serialize.o: ../../../src/main/serialize.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../src/include/Rmath.h \
 ../../../src/include/Fileio.h ../../src/include/Rversion.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h
sort.o: ../../../src/main/sort.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h
source.o: ../../../src/main/source.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Fileio.h ../../../src/include/IOStuff.h \
 ../../../src/include/Parse.h ../../../src/include/R_ext/Parse.h \
 ../../../src/include/Rconnections.h \
 ../../../src/include/R_ext/Connections.h
split.o: ../../../src/main/split.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
sprintf.o: ../../../src/main/sprintf.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/main/RBufferUtils.h ../../../src/include/R_ext/RS.h \
 ../../src/include/Rconfig.h
startup.o: ../../../src/main/startup.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Fileio.h \
 ../../../src/include/Startup.h ../../../src/include/R_ext/RStartup.h
subassign.o: ../../../src/main/subassign.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h
subscript.o: ../../../src/main/subscript.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h
subset.o: ../../../src/main/subset.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
summary.o: ../../../src/main/summary.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
sysutils.o: ../../../src/main/sysutils.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/Riconv.h ../../../src/include/Rinterface.h \
 ../../../src/include/R_ext/RStartup.h ../../../src/main/RBufferUtils.h
times.o: ../../../src/main/times.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h
unique.o: ../../../src/main/unique.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/include/R_ext/Random.h
util.o: ../../../src/main/util.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../../src/include/Print.h ../../../src/include/Defn.h \
 ../../../src/include/R_ext/PrtUtil.h ../../../src/include/R_ext/Riconv.h \
 ../../../src/main/valid_utf8.h ../../../src/include/R_ext/Applic.h \
 ../../../src/include/R_ext/RS.h ../../src/include/Rconfig.h \
 ../../../src/include/R_ext/BLAS.h ../../src/include/Rmath.h
version.o: ../../../src/main/version.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Internal.h \
 ../../src/include/Rversion.h
vfonts.o: ../../../src/main/vfonts.c ../../src/include/config.h \
 ../../../src/include/Defn.h ../../../src/include/R_ext/Complex.h \
 ../../../src/include/Rinternals.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Memory.h ../../../src/include/R_ext/Utils.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/Rinlinedfuns.h \
 ../../../src/include/Errormsg.h ../../../src/include/Rdynpriv.h \
 ../../../src/include/R_ext/Rdynload.h \
 ../../../src/include/R_ext/GraphicsEngine.h \
 ../../../src/include/R_ext/GraphicsDevice.h \
 ../../../src/include/Rmodules/Rvfonts.h
Rmain.o: ../../../src/main/Rmain.c ../../../src/include/Rinterface.h \
 ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RStartup.h
alloca.o: ../../../src/main/alloca.c ../../src/include/config.h
mkdtemp.o: ../../../src/main/mkdtemp.c ../../src/include/config.h
strdup.o: ../../../src/main/strdup.c ../../src/include/config.h
strncasecmp.o: ../../../src/main/strncasecmp.c ../../src/include/config.h
