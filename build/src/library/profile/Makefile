#
# ${R_HOME}/src/library/profile/Makefile

VPATH = ../../../../src/library/profile
srcdir = ../../../../src/library/profile
top_srcdir = ../../../..

top_builddir = ../../..
subdir = src/library/profile

include $(top_builddir)/Makeconf

distdir = $(top_builddir)/$(PACKAGE)-$(VERSION)/$(subdir)
DISTFILES = Common.R Makefile.in Rprofile.unix Rprofile.windows

all: Makefile $(srcdir)/Common.R $(srcdir)/Rprofile.$(R_OSTYPE)
	@$(ECHO) "building system startup profile"
	@$(MKINSTALLDIRS) $(top_builddir)/library/base/R
	@cat $(srcdir)/Common.R $(srcdir)/Rprofile.$(R_OSTYPE) \
	  > $(top_builddir)/library/base/R/Rprofile

Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status
	@cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@

mostlyclean: clean
clean:
distclean:
	-@rm -f Makefile
maintainer-clean: distclean

distdir: $(DISTFILES)
	@for f in $(DISTFILES); do \
	  test -f $(distdir)/$${f} \
	    || ln $(srcdir)/$${f} $(distdir)/$${f} 2>/dev/null \
	    || cp -p $(srcdir)/$${f} $(distdir)/$${f}; \
	done
