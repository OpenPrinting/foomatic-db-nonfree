dnl Process this file with autoconf to produce a configure script.
AC_INIT(db/source/driver/Postscript-Lexmark.xml)

dnl If the user didn't specify the $sysconfdir on the command line, let it
dnl be /etc, not /usr/local/etc or /usr/etc
if [[ x$sysconfdir = 'x${prefix}/etc' ]]; then
  sysconfdir=/etc
fi

dnl Checks for programs.
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET

dnl Checks for programs/directories which are used by Foomtic
BINSEARCHPATH=/usr/bin:/bin:/usr/local/bin
DATASEARCHPATH=/usr/share:/usr/local/share:/usr/lib:/usr/local/lib:/opt

dnl Get the operating system and version number...
uname=`uname`
uversion=`uname -r | sed -e '1,$s/[[^0-9]]//g'`
if test x$uname = xIRIX64; then
  uname="IRIX"
fi

if test x$uname = xIRIX; then
  BINSEARCHPATH="/usr/freeware/bin:$BINSEARCHPATH"
  DATASEARCHPATH="/usr/freeware/share:$DATASEARCHPATH"
fi

dnl Check for Perl
AC_PATH_PROGS(PERL,perl,/usr/bin/perl,$BINSEARCHPATH)

dnl Path for Foomatic XML database (foomatic-db)
AC_PATH_DIRS(LIBDIR,foomatic/db/source,/usr/share/foomatic/db/source,$DATASEARCHPATH)
LIBDIR=`echo $LIBDIR | sed -e "s:/db/source$::"`
AC_PATH_DIRS(LOCAL_LIBDIR,db/source,../foomatic-db/db/source,./foomatic-db:./foomatic-db*:../foomatic-db:../foomatic-db*:../foomatic-db-engine/foomatic-db:../foomatic-db-engine*/foomatic-db*:../foomatic-db-engine:../foomatic-db-engine*)
LOCAL_LIBDIR=`echo $LOCAL_LIBDIR | sed -e "s:/db/source$::"`

AC_OUTPUT(Makefile)

dnl Finished
echo "Finished configuring."
echo "then 'make install' to install it."
