#
# ${R_HOME}/src/nmath/Makefile

VPATH = ../../../src/nmath
srcdir = ../../../src/nmath
top_srcdir = ../../..

top_builddir = ../..
subdir = src/nmath

include $(top_builddir)/Makeconf

## <NOTE>
## Keep these in sync with ./standalone/Makefile.in and *.win!
SOURCES = \
	mlutils.c \
	d1mach.c i1mach.c \
	fmax2.c fmin2.c fprec.c fround.c ftrunc.c \
	sign.c fsign.c \
	imax2.c imin2.c \
	chebyshev.c log1p.c expm1.c lgammacor.c gammalims.c stirlerr.c bd0.c \
	gamma.c lgamma.c gamma_cody.c beta.c lbeta.c polygamma.c cospi.c \
	bessel_i.c bessel_j.c bessel_k.c bessel_y.c \
	choose.c \
	snorm.c sexp.c \
	dgamma.c pgamma.c qgamma.c rgamma.c \
	dbeta.c pbeta.c qbeta.c rbeta.c \
	dunif.c punif.c qunif.c runif.c \
	dnorm.c pnorm.c qnorm.c rnorm.c \
	dlnorm.c plnorm.c qlnorm.c rlnorm.c \
	df.c pf.c qf.c rf.c dnf.c \
	dt.c pt.c qt.c rt.c dnt.c \
	dchisq.c pchisq.c qchisq.c rchisq.c rnchisq.c \
	dbinom.c pbinom.c qbinom.c rbinom.c \
	rmultinom.c \
	dcauchy.c pcauchy.c qcauchy.c rcauchy.c \
	dexp.c pexp.c qexp.c rexp.c \
	dgeom.c pgeom.c qgeom.c rgeom.c \
	dhyper.c phyper.c qhyper.c rhyper.c \
	dnbinom.c pnbinom.c qnbinom.c rnbinom.c \
	dpois.c ppois.c qpois.c rpois.c \
	dweibull.c pweibull.c qweibull.c rweibull.c \
	dlogis.c plogis.c qlogis.c rlogis.c \
	dnchisq.c pnchisq.c qnchisq.c \
	dnbeta.c pnbeta.c qnbeta.c \
	pnf.c pnt.c qnf.c qnt.c \
	ptukey.c qtukey.c \
	toms708.c wilcox.c \
	signrank.c
## </NOTE>
DEPENDS = $(SOURCES:.c=.d)
OBJECTS = $(SOURCES:.c=.o)
HEADERS = bessel.h dpq.h nmath.h

distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = Makefile.in Makefile.win $(SOURCES) $(HEADERS)

SUBDIRS_WITH_NO_BUILD = standalone

#ALL_CFLAGS = $(ALL_CFLAGS_LO)

all: R

Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status $(SOURCES)
	@cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@

Makedeps: Makefile $(DEPENDS)
	@cat $(DEPENDS) >> Makefile
	@touch $@

R: Makedeps
	@$(MAKE) libnmath.a

libnmath.a: $(OBJECTS)
	rm -rf $@
	$(AR) cr $@ $(OBJECTS)
	$(RANLIB) $@

mostlyclean: clean
clean:
	@(cd standalone; $(MAKE) clean)
	@-rm -rf .libs _libs
	@-rm -f Makedeps *.d *.o *.a *.lo *.la stamp-lo
distclean: clean
	@(cd standalone; $(MAKE) distclean)
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
	  ((cd $(srcdir); $(TAR) -c -f - $(DISTDIR_TAR_EXCLUDE) $${d}) \
	      | (cd $(distdir); $(TAR) -x -f -)) \
	    || exit 1; \
        done

## Automagically generated dependencies:

mlutils.o: ../../../src/nmath/mlutils.c ../../src/include/config.h \
 ../../../src/nmath/nmath.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
d1mach.o: ../../../src/nmath/d1mach.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
i1mach.o: ../../../src/nmath/i1mach.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
fmax2.o: ../../../src/nmath/fmax2.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
fmin2.o: ../../../src/nmath/fmin2.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
fprec.o: ../../../src/nmath/fprec.c ../../src/include/config.h \
 ../../../src/nmath/nmath.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
fround.o: ../../../src/nmath/fround.c ../../src/include/config.h \
 ../../../src/nmath/nmath.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
ftrunc.o: ../../../src/nmath/ftrunc.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
sign.o: ../../../src/nmath/sign.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
fsign.o: ../../../src/nmath/fsign.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
imax2.o: ../../../src/nmath/imax2.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
imin2.o: ../../../src/nmath/imin2.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
chebyshev.o: ../../../src/nmath/chebyshev.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
log1p.o: ../../../src/nmath/log1p.c ../../src/include/config.h \
 ../../../src/nmath/nmath.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
expm1.o: ../../../src/nmath/expm1.c ../../src/include/config.h \
 ../../../src/nmath/nmath.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
lgammacor.o: ../../../src/nmath/lgammacor.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
gammalims.o: ../../../src/nmath/gammalims.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
stirlerr.o: ../../../src/nmath/stirlerr.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
bd0.o: ../../../src/nmath/bd0.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
gamma.o: ../../../src/nmath/gamma.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
lgamma.o: ../../../src/nmath/lgamma.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
gamma_cody.o: ../../../src/nmath/gamma_cody.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
beta.o: ../../../src/nmath/beta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
lbeta.o: ../../../src/nmath/lbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
polygamma.o: ../../../src/nmath/polygamma.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
cospi.o: ../../../src/nmath/cospi.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
bessel_i.o: ../../../src/nmath/bessel_i.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/bessel.h \
 ../../../src/include/R_ext/Memory.h
bessel_j.o: ../../../src/nmath/bessel_j.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/bessel.h \
 ../../../src/include/R_ext/Memory.h
bessel_k.o: ../../../src/nmath/bessel_k.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/bessel.h \
 ../../../src/include/R_ext/Memory.h
bessel_y.o: ../../../src/nmath/bessel_y.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/bessel.h \
 ../../../src/include/R_ext/Memory.h
choose.o: ../../../src/nmath/choose.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
snorm.o: ../../../src/nmath/snorm.c ../../../src/include/R_ext/Random.h \
 ../../../src/include/R_ext/Boolean.h ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/RS.h \
 ../../../src/include/R_ext/Error.h ../../../src/include/R_ext/Print.h \
 ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
sexp.o: ../../../src/nmath/sexp.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dgamma.o: ../../../src/nmath/dgamma.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pgamma.o: ../../../src/nmath/pgamma.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qgamma.o: ../../../src/nmath/qgamma.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rgamma.o: ../../../src/nmath/rgamma.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dbeta.o: ../../../src/nmath/dbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pbeta.o: ../../../src/nmath/pbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qbeta.o: ../../../src/nmath/qbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rbeta.o: ../../../src/nmath/rbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dunif.o: ../../../src/nmath/dunif.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
punif.o: ../../../src/nmath/punif.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qunif.o: ../../../src/nmath/qunif.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
runif.o: ../../../src/nmath/runif.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dnorm.o: ../../../src/nmath/dnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pnorm.o: ../../../src/nmath/pnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qnorm.o: ../../../src/nmath/qnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rnorm.o: ../../../src/nmath/rnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dlnorm.o: ../../../src/nmath/dlnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
plnorm.o: ../../../src/nmath/plnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qlnorm.o: ../../../src/nmath/qlnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rlnorm.o: ../../../src/nmath/rlnorm.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
df.o: ../../../src/nmath/df.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pf.o: ../../../src/nmath/pf.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qf.o: ../../../src/nmath/qf.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rf.o: ../../../src/nmath/rf.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dnf.o: ../../../src/nmath/dnf.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
dt.o: ../../../src/nmath/dt.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pt.o: ../../../src/nmath/pt.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qt.o: ../../../src/nmath/qt.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rt.o: ../../../src/nmath/rt.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dnt.o: ../../../src/nmath/dnt.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
dchisq.o: ../../../src/nmath/dchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pchisq.o: ../../../src/nmath/pchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qchisq.o: ../../../src/nmath/qchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rchisq.o: ../../../src/nmath/rchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
rnchisq.o: ../../../src/nmath/rnchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dbinom.o: ../../../src/nmath/dbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pbinom.o: ../../../src/nmath/pbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qbinom.o: ../../../src/nmath/qbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rbinom.o: ../../../src/nmath/rbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rmultinom.o: ../../../src/nmath/rmultinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dcauchy.o: ../../../src/nmath/dcauchy.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pcauchy.o: ../../../src/nmath/pcauchy.c ../../src/include/config.h \
 ../../../src/nmath/nmath.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qcauchy.o: ../../../src/nmath/qcauchy.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rcauchy.o: ../../../src/nmath/rcauchy.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dexp.o: ../../../src/nmath/dexp.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pexp.o: ../../../src/nmath/pexp.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qexp.o: ../../../src/nmath/qexp.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rexp.o: ../../../src/nmath/rexp.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dgeom.o: ../../../src/nmath/dgeom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pgeom.o: ../../../src/nmath/pgeom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qgeom.o: ../../../src/nmath/qgeom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rgeom.o: ../../../src/nmath/rgeom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dhyper.o: ../../../src/nmath/dhyper.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
phyper.o: ../../../src/nmath/phyper.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qhyper.o: ../../../src/nmath/qhyper.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rhyper.o: ../../../src/nmath/rhyper.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
dnbinom.o: ../../../src/nmath/dnbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pnbinom.o: ../../../src/nmath/pnbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qnbinom.o: ../../../src/nmath/qnbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rnbinom.o: ../../../src/nmath/rnbinom.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dpois.o: ../../../src/nmath/dpois.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
ppois.o: ../../../src/nmath/ppois.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qpois.o: ../../../src/nmath/qpois.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rpois.o: ../../../src/nmath/rpois.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dweibull.o: ../../../src/nmath/dweibull.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pweibull.o: ../../../src/nmath/pweibull.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qweibull.o: ../../../src/nmath/qweibull.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rweibull.o: ../../../src/nmath/rweibull.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dlogis.o: ../../../src/nmath/dlogis.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
plogis.o: ../../../src/nmath/plogis.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qlogis.o: ../../../src/nmath/qlogis.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
rlogis.o: ../../../src/nmath/rlogis.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h
dnchisq.o: ../../../src/nmath/dnchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pnchisq.o: ../../../src/nmath/pnchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qnchisq.o: ../../../src/nmath/qnchisq.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
dnbeta.o: ../../../src/nmath/dnbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pnbeta.o: ../../../src/nmath/pnbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qnbeta.o: ../../../src/nmath/qnbeta.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pnf.o: ../../../src/nmath/pnf.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
pnt.o: ../../../src/nmath/pnt.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qnf.o: ../../../src/nmath/qnf.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qnt.o: ../../../src/nmath/qnt.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
ptukey.o: ../../../src/nmath/ptukey.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
qtukey.o: ../../../src/nmath/qtukey.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
toms708.o: ../../../src/nmath/toms708.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
wilcox.o: ../../../src/nmath/wilcox.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h \
 ../../../src/include/R_ext/Utils.h ../../../src/include/R_ext/Complex.h
signrank.o: ../../../src/nmath/signrank.c ../../../src/nmath/nmath.h \
 ../../src/include/config.h ../../src/include/Rconfig.h \
 ../../src/include/Rmath.h ../../../src/include/R_ext/Boolean.h \
 ../../../src/include/R_ext/RS.h ../../../src/include/R_ext/Error.h \
 ../../../src/include/R_ext/Print.h ../../../src/include/R_ext/Arith.h \
 ../../../src/include/R_ext/libextern.h ../../../src/nmath/dpq.h
