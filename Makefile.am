## Process this file with automake to get Makefile.in

AUTOMAKE_OPTIONS = gnu

SUBDIRS =  m4 lib src doc

ACLOCAL_AMFLAGS = -I m4 

EXTRA_DIST = have.h system.h COPYING.README

ChangeLog:
	git log > ChangeLog

deb:
	dpkg-buildpackage -rfakeroot

rpm: dist
	cp $(distdir).tar.gz /usr/src/redhat/SOURCES/
	cp redhat/tinc.spec /usr/src/redhat/SOURCES/
	cd /usr/src/redhat/SOURCES/ && rpm -bb tinc.spec

release:
	rm -f ChangeLog
	$(MAKE) ChangeLog
	echo "Please edit the NEWS file now..."
	/usr/bin/editor NEWS
	$(MAKE) dist
