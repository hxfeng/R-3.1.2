#
# ${R_HOME}/src/library/stats/src/Makefile

pkg = stats

VPATH = ../../../../../src/library/stats/src
srcdir = ../../../../../src/library/stats/src
top_srcdir = ../../../../..

top_builddir = ../../../..
subdir = src/library/$(pkg)/src
R_HOME = $(top_builddir)
## for $(R_HOME)/etc${R_ARCH}/Makeconf
R_SHARE_DIR = $(R_HOME)/share

SOURCES_C = init.c kmeans.c \
  ansari.c bandwidths.c chisqsim.c d2x2xk.c fexact.c kendall.c ks.c \
  line.c smooth.c \
  prho.c swilk.c \
  ksmooth.c loessc.c monoSpl.c isoreg.c Srunmed.c \
  dblcen.c distance.c hclust-utils.c \
  nls.c rWishart.c \
  HoltWinters.c PPsum.c arima.c burg.c filter.c \
  mAR.c pacf.c starma.c port.c family.c sbart.c \
  approx.c loglin.c lowess.c massdist.c splines.c lm.c \
  complete_cases.c cov.c deriv.c fft.c fourier.c model.c optim.c optimize.c \
  integrate.c random.c distn.c zeroin.c rcont.c influence.c

SOURCES_F = bsplvd.f bvalue.f bvalus.f loessf.f ppr.f qsbart.f \
  sgram.f sinerp.f sslvrg.f stxwx.f \
  hclust.f kmns.f \
  eureka.f stl.f portsrc.f lminfl.f
DEPENDS = $(SOURCES_C:.c=.d)
OBJECTS = $(SOURCES_C:.c=.o) $(SOURCES_F:.f=.o)

# need config.h
PKG_CPPFLAGS = -I../../../include -I$(top_srcdir)/src/include -DHAVE_CONFIG_H
PKG_CFLAGS = -fopenmp $(C_VISIBILITY)
PKG_FFLAGS = $(F77_VISIBILITY)

SHLIB = $(pkg).so

## <FIXME>
## We should really add FLIBS to SHLIB_LIBADD, but we need to include
## the shlib Makeconf at a later stage, and its default value would
## override our setting.
PKG_LIBS = -fopenmp $(LAPACK_LIBS) $(BLAS_LIBS) $(FLIBS)
## </FIXME>


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

## Meeded with i386 gcc 4.5.0 -- PR#14427
portsrc_FFLAGS=$(FPICFLAGS) $(SHLIB_FFLAGS) -g -O2 -ffloat-store
portsrc.o: portsrc.f
	$(F77) $(portsrc_FFLAGS) -c $< -o $@

mostlyclean: clean
clean:
	@-rm -rf .libs _libs
	@-rm -f Makedeps *.d *.o *$(SHLIB_EXT)
distclean: clean
	@-rm -f Makefile
maintainer-clean: distclean

## Automagically generated dependencies:
init.o: ../../../../../src/library/stats/src/init.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/modreg.h \
 ../../../../../src/library/stats/src/nls.h \
 ../../../../../src/library/stats/src/port.h \
 ../../../../../src/library/stats/src/stats.h \
 ../../../../../src/library/stats/src/statsR.h \
 ../../../../../src/library/stats/src/ts.h \
 ../../../../../src/include/R_ext/Rdynload.h \
 ../../../../../src/include/R_ext/Visibility.h
kmeans.o: ../../../../../src/library/stats/src/kmeans.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/modreg.h \
 ../../../../../src/include/Rinternals.h
ansari.o: ../../../../../src/library/stats/src/ansari.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rmath.h \
 ../../../../../src/library/stats/src/stats.h \
 ../../../../../src/include/Rinternals.h
bandwidths.o: ../../../../../src/library/stats/src/bandwidths.c \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h
chisqsim.o: ../../../../../src/library/stats/src/chisqsim.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h ../../../include/Rmath.h \
 ../../../../../src/library/stats/src/stats.h
d2x2xk.o: ../../../../../src/library/stats/src/d2x2xk.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rmath.h \
 ../../../../../src/include/Rinternals.h
fexact.o: ../../../../../src/library/stats/src/fexact.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rmath.h \
 ../../../../../src/include/Rinternals.h
kendall.o: ../../../../../src/library/stats/src/kendall.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rmath.h \
 ../../../../../src/include/Rinternals.h
ks.o: ../../../../../src/library/stats/src/ks.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h ../../../include/Rmath.h
line.o: ../../../../../src/library/stats/src/line.c \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h \
 ../../../../../src/library/stats/src/statsR.h
smooth.o: ../../../../../src/library/stats/src/smooth.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h
prho.o: ../../../../../src/library/stats/src/prho.c \
 ../../../include/Rmath.h ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h
swilk.o: ../../../../../src/library/stats/src/swilk.c \
 ../../../include/Rmath.h ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h
ksmooth.o: ../../../../../src/library/stats/src/ksmooth.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h
loessc.o: ../../../../../src/library/stats/src/loessc.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h
monoSpl.o: ../../../../../src/library/stats/src/monoSpl.c \
 ../../../../../src/library/stats/src/modreg.h \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h
isoreg.o: ../../../../../src/library/stats/src/isoreg.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/modreg.h \
 ../../../../../src/include/Rinternals.h
Srunmed.o: ../../../../../src/library/stats/src/Srunmed.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/modreg.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/Trunmed.c
dblcen.o: ../../../../../src/library/stats/src/dblcen.c \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h
distance.o: ../../../../../src/library/stats/src/distance.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rmath.h \
 ../../../../../src/library/stats/src/stats.h \
 ../../../../../src/include/Rinternals.h
hclust-utils.o: ../../../../../src/library/stats/src/hclust-utils.c \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h \
 ../../../../../src/library/stats/src/statsR.h
nls.o: ../../../../../src/library/stats/src/nls.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/nls.h
rWishart.o: ../../../../../src/library/stats/src/rWishart.c \
 ../../../include/config.h ../../../../../src/include/R.h \
 ../../../include/Rconfig.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h ../../../include/Rmath.h \
 ../../../../../src/include/R_ext/Lapack.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/library/stats/src/stats.h \
 ../../../../../src/library/stats/src/statsR.h
HoltWinters.o: ../../../../../src/library/stats/src/HoltWinters.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/ts.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/stats.h
PPsum.o: ../../../../../src/library/stats/src/PPsum.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h
arima.o: ../../../../../src/library/stats/src/arima.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/ts.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/stats.h \
 ../../../../../src/library/stats/src/statsR.h
burg.o: ../../../../../src/library/stats/src/burg.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h
filter.o: ../../../../../src/library/stats/src/filter.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/ts.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/stats.h
mAR.o: ../../../../../src/library/stats/src/mAR.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/library/stats/src/ts.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/stats.h
pacf.o: ../../../../../src/library/stats/src/pacf.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/ts.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/stats.h
starma.o: ../../../../../src/library/stats/src/starma.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/ts.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/stats.h
port.o: ../../../../../src/library/stats/src/port.c \
 ../../../../../src/library/stats/src/port.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/BLAS.h
family.o: ../../../../../src/library/stats/src/family.c \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/library/stats/src/stats.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/library/stats/src/statsR.h
sbart.o: ../../../../../src/library/stats/src/sbart.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rmath.h \
 ../../../../../src/library/stats/src/modreg.h \
 ../../../../../src/include/Rinternals.h
approx.o: ../../../../../src/library/stats/src/approx.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/library/stats/src/statsR.h
loglin.o: ../../../../../src/library/stats/src/loglin.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/statsR.h
lowess.o: ../../../../../src/library/stats/src/lowess.c \
 ../../../include/config.h ../../../include/Rmath.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h
massdist.o: ../../../../../src/library/stats/src/massdist.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h
splines.o: ../../../../../src/library/stats/src/splines.c \
 ../../../include/config.h ../../../../../src/include/R.h \
 ../../../include/Rconfig.h ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/statsR.h
lm.o: ../../../../../src/library/stats/src/lm.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/library/stats/src/statsR.h
complete_cases.o: ../../../../../src/library/stats/src/complete_cases.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h
cov.o: ../../../../../src/library/stats/src/cov.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h ../../../include/Rmath.h \
 ../../../../../src/library/stats/src/statsR.h
deriv.o: ../../../../../src/library/stats/src/deriv.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h
fft.o: ../../../../../src/library/stats/src/fft.c \
 ../../../include/config.h ../../../include/Rmath.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/include/R_ext/Complex.h
fourier.o: ../../../../../src/library/stats/src/fourier.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/library/stats/src/statsR.h
model.o: ../../../../../src/library/stats/src/model.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/library/stats/src/statsR.h
optim.o: ../../../../../src/library/stats/src/optim.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/library/stats/src/statsR.h
optimize.o: ../../../../../src/library/stats/src/optimize.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/library/stats/src/statsR.h ../../../include/Rmath.h
integrate.o: ../../../../../src/library/stats/src/integrate.c \
 ../../../include/config.h ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/BLAS.h
random.o: ../../../../../src/library/stats/src/random.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h \
 ../../../../../src/include/R_ext/Random.h ../../../include/Rmath.h \
 ../../../../../src/library/stats/src/statsR.h \
 ../../../../../src/library/stats/src/stats.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h
distn.o: ../../../../../src/library/stats/src/distn.c \
 ../../../include/config.h ../../../../../src/include/Defn.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/Rinlinedfuns.h \
 ../../../../../src/include/Errormsg.h ../../../include/Rmath.h \
 ../../../../../src/library/stats/src/statsR.h
zeroin.o: ../../../../../src/library/stats/src/zeroin.c \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/include/R_ext/Complex.h
rcont.o: ../../../../../src/library/stats/src/rcont.c \
 ../../../include/config.h ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Applic.h \
 ../../../../../src/include/R_ext/RS.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/BLAS.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Utils.h
influence.o: ../../../../../src/library/stats/src/influence.c \
 ../../../../../src/include/R.h ../../../include/Rconfig.h \
 ../../../../../src/include/R_ext/Arith.h \
 ../../../../../src/include/R_ext/libextern.h \
 ../../../../../src/include/R_ext/Boolean.h \
 ../../../../../src/include/R_ext/Complex.h \
 ../../../../../src/include/R_ext/Constants.h \
 ../../../../../src/include/R_ext/Error.h \
 ../../../../../src/include/R_ext/Memory.h \
 ../../../../../src/include/R_ext/Print.h \
 ../../../../../src/include/R_ext/Random.h \
 ../../../../../src/include/R_ext/Utils.h \
 ../../../../../src/include/R_ext/RS.h \
 ../../../../../src/include/Rinternals.h \
 ../../../../../src/library/stats/src/statsR.h
