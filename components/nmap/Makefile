
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2011, 2017, Oracle and/or its affiliates. All rights reserved.
#
BUILD_BITS= 64
# Can't use the Studio compilers as they don't support the GNU 
# __attribute__ extension
COMPILER= gcc
include ../../make-rules/shared-macros.mk

COMPONENT_NAME=         nmap
COMPONENT_VERSION=      7.60
COMPONENT_PROJECT_URL=	http://nmap.org/
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tgz
COMPONENT_ARCHIVE_HASH= \
    sha256:330d94228f3196dc7481990435703ba1ab67bb95016ea073a11a361aa76f65ef
COMPONENT_ARCHIVE_URL=  $(COMPONENT_PROJECT_URL)dist/$(COMPONENT_ARCHIVE)
COMPONENT_ANITYA_ID=	2096

TPNO=			37398

TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

COMPONENT_PRE_CONFIGURE_ACTION = \
	($(CLONEY) $(SOURCE_DIR) $(@D))

PKG_MACROS +=		PYVER=$(PYTHON_VERSION)

CONFIGURE_OPTIONS  +=   LIBS="$(LIBSOCKET) $(LIBNSL)"

# Fix 64-bit linking via compiler.
LDFLAGS += $(CC_BITS)

CONFIGURE_OPTIONS  +=   PYTHON="$(PYTHON.$(PYTHON_VERSION))"
CONFIGURE_OPTIONS  +=   --srcdir=$(BUILD_DIR_64)
CONFIGURE_OPTIONS  +=   --localstatedir=$(VARDIR)
CONFIGURE_OPTIONS  +=   --without-localdirs 
CONFIGURE_OPTIONS  +=   --with-zenmap 
CONFIGURE_OPTIONS  +=   --with-openssl
CONFIGURE_OPTIONS  +=   --with-libpcap
CONFIGURE_OPTIONS  +=   --with-libpcre
CONFIGURE_OPTIONS  +=   --with-liblua 
CONFIGURE_OPTIONS  +=   --with-ncat 
CONFIGURE_OPTIONS  +=   --with-ndiff

# The nmap libdnet-stripped configure script can't properly handle
# finding / using three Solaris network header files. We override this.
# When CR #26315554 is fixed, these three lines can be removed.
CONFIGURE_OPTIONS  +=	ac_cv_header_net_pfvar_h=yes
CONFIGURE_OPTIONS  +=	ac_cv_header_net_route_h=yes
CONFIGURE_OPTIONS  +=	ac_cv_header_netinet_in_vars_h=yes

REQUIRED_PACKAGES += library/libssh2
REQUIRED_PACKAGES += library/pcre
REQUIRED_PACKAGES += library/python/pygobject-27
REQUIRED_PACKAGES += library/python/pygtk2-27
REQUIRED_PACKAGES += library/security/openssl
REQUIRED_PACKAGES += runtime/lua
REQUIRED_PACKAGES += runtime/python-27
REQUIRED_PACKAGES += system/library/gcc/gcc-c-runtime
REQUIRED_PACKAGES += system/library/gcc/gcc-c++-runtime
REQUIRED_PACKAGES += system/library/libpcap
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += system/network/bpf
