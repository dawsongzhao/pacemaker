#
# Copyright (C) 2004 Andrew Beekhof
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
#
include $(top_srcdir)/Makefile.common

## libraries
lib_LTLIBRARIES	= libcrmcluster.la 

libcrmcluster_la_LDFLAGS = -version-info 6:1:2

libcrmcluster_la_CFLAGS  = $(CFLAGS_HARDENED_LIB)
libcrmcluster_la_LDFLAGS += $(LDFLAGS_HARDENED_LIB)

libcrmcluster_la_LIBADD  = $(top_builddir)/lib/common/libcrmcommon.la $(top_builddir)/lib/fencing/libstonithd.la $(CLUSTERLIBS)

libcrmcluster_la_SOURCES = election.c cluster.c membership.c
if BUILD_CS_SUPPORT
libcrmcluster_la_SOURCES += cpg.c
if BUILD_CS_PLUGIN
libcrmcluster_la_SOURCES += legacy.c
else
libcrmcluster_la_SOURCES += corosync.c
endif
endif
if BUILD_HEARTBEAT_SUPPORT
libcrmcluster_la_SOURCES += heartbeat.c
#libcrmcluster_la_LIBADD  += -ldl
endif

clean-generic:
	rm -f *.log *.debug *.xml *~
