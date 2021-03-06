#
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
# Copyright (c) 2015, 2017, Oracle and/or its affiliates. All rights reserved.
#

BUILD_BITS =            32_and_64
# All components using gobject-introspection must be built with gcc as
# gobject-introspection does not produce correct results when using Studio.
COMPILER =              gcc
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		totem-pl-parser
COMPONENT_VERSION=	3.10.7
COMPONENT_PROJECT_URL=  https://github.com/GNOME/totem-pl-parser
COMPONENT_ARCHIVE_HASH= \
	sha256:9c8285bc3131faa309d5cba5a919d5166abc2b8cc5a0c850fe861be8b14e089c
COMPONENT_BUGDB=        gnome/multimedia
COMPONENT_ANITYA_ID=	13163

TPNO=			34606

TEST_TARGET  = $(NO_TESTS)

# Needs gobject-introspection, not available on S11.3
include $(WS_MAKE_RULES)/no-evaluation.mk

include $(WS_MAKE_RULES)/gnome-component.mk

# Assumes GNU xgettext in PATH
CONFIGURE_ENV += PATH=$(GNUBIN):$(PATH)

# Required so that configure can find and use 64-bit version of config program.
CONFIGURE_ENV.64 += ac_cv_path_LIBGCRYPT_CONFIG=$(USRBINDIR64)/libgcrypt-config

CONFIGURE_OPTIONS += --disable-quvi
CONFIGURE_OPTIONS += --disable-static
# Required for other components.
CONFIGURE_OPTIONS += --enable-introspection
CONFIGURE_OPTIONS += --enable-libarchive
CONFIGURE_OPTIONS += --enable-libgcrypt
CONFIGURE_OPTIONS += --enable-shared
CONFIGURE_OPTIONS += --with-pic

REQUIRED_PACKAGES += developer/documentation-tool/gtk-doc
REQUIRED_PACKAGES += library/desktop/gobject/gobject-introspection
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/gmime
REQUIRED_PACKAGES += library/libarchive
REQUIRED_PACKAGES += library/libsoup
REQUIRED_PACKAGES += library/libxml2
REQUIRED_PACKAGES += system/library/security/libgcrypt
