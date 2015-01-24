lib_LTLIBRARIES = libguul-1.0.la

libguulincdir = $(includedir)/guul-1.0
libguulinc_HEADERS = guul.h

libguul_1_0_la_CFLAGS = $(GLIB_CFLAGS) $(PLATFORM_CFLAGS) $(UUID_CFLAGS)
libguul_1_0_la_LDFLAGS = -version $(LTVERSION) $(PLATFORM_LDFLAGS) $(UUID_LDFLAGS)
libguul_1_0_la_LIBADD = $(PLATFORM_LIBADD) $(UUID_LIBADD)
libguul_1_0_la_SOURCES = $(libguulinc_HEADERS) guul.c

MAINTAINERCLEANFILES = Makefile.in
