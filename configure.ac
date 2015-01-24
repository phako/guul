AC_PREREQ([2.64])
AC_INIT([guul],
        [0.1],
        [https://github.com/phako/guul/issues],
        [guul],
        [https://github.com/phako/guul])

AC_CONFIG_HEADERS([config.h])
AC_CONFIG_SRCDIR([guul.c])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])

AC_CANONICAL_HOST
AC_CANONICAL_TARGET

AM_INIT_AUTOMAKE([1.11 tar-ustar no-dist-gzip dist-xz foreign -Wno-portability])
AM_MAINTAINER_MODE([enable])

AM_SILENT_RULES([yes])

AC_PROG_CC
AC_HEADER_STDC

LT_PREREQ([2.2])
LT_INIT

PKG_PROG_PKG_CONFIG([0.24])

PKG_CHECK_MODULES([GLIB],[glib-2.0])
GUUL_CHECK_UUID

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
