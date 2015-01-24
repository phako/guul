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

GUUL_LIBS=
GUUL_CFLAGS=
AC_MSG_CHECKING([for uuid library])
case "$host" in
    *-*-mingw*)
        uuid_found=windows
        AC_DEFINE([GUUL_PLATFORM_WINDOWS],[1],[Compiling for windows])
        GUUL_LIBS=-lrpcrt4
        ;;
    *darwin*)
        uuid_found=macosx
        AC_DEFINE([GUUL_PLATFORM_OSX],[1],[Compiling for OS X])
        ;;
    *bsd*)
        uuid_found=bsd
        ;;
    *)
        uuid_found=generic
        ;;
esac

dnl do fallback if we have a BSD that does not have the necessary functions
AS_IF([test "x$uuid_found" = "xbsd"],
      [AC_SEARCH_LIBS([uuid_to_string], [c],
        [UUID_LIBS=
         AC_DEFINE([GUUL_PLATFORM_BSD],[1],[Compiling for BSD flavor])
        ],
        [uuid_found=generic])
      ])

dnl for other platforms, use libuuid from the e2fs project
AS_IF([test "x$uuid_found" = "xgeneric"],
      [PKG_CHECK_MODULES(UUID, [uuid],
        [
          AC_DEFINE([GUUL_PLATFORM_GENERIC],[1],[Using external library])
          GUUL_LIBS="$UUID_LIBS"
          GUUL_CFLAGS="$UUID_CFLAGS"
        ],
        [AC_MSG_ERROR([none])
      ])
])

AC_SUBST(GUUL_LIBS)
AC_SUBST(GUUL_CFLAGS)
AC_MSG_RESULT([using flavor $uuid_found])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
