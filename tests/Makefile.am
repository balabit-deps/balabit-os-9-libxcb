########################
## tests/Makefile.am
########################
SUBDIRS = 
EXTRA_DIST = CheckLog.xsl
AM_MAKEFLAGS = -k
AM_CFLAGS = -Wall @CHECK_CFLAGS@ -I$(top_srcdir)/src
LDADD = @CHECK_LIBS@ $(top_builddir)/src/libxcb.la

if HAVE_CHECK
TESTS = check_all
check_PROGRAMS = check_all
check_all_SOURCES =  check_all.c check_suites.h check_public.c

check-local: check-TESTS
	$(RM) CheckLog.html
	if test x$(HTML_CHECK_RESULT) = xyes; then \
		$(XSLTPROC) $(srcdir)/CheckLog.xsl CheckLog*.xml > CheckLog.html; \
	else \
		touch CheckLog.html; \
	fi

CheckLog.html: $(check_PROGRAMS)
	$(MAKE) $(AM_MAKEFLAGS) check;

endif

clean-local::
	$(RM) CheckLog.html CheckLog*.txt CheckLog*.xml
