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

# Although this component is historically generic, GNOME distributes it
# directly now, presumably because the original author abandoned it and GNOME
# depends on it.
COMPONENT_NAME=		gmime
COMPONENT_VERSION=	2.6.23
COMPONENT_ARCHIVE_HASH= \
	sha256:7149686a71ca42a1390869b6074815106b061aaeaaa8f2ef8c12c191d9a79f6a
COMPONENT_BUGDB=        gnome/libraries
COMPONENT_ANITYA_ID=	13124

TPNO=			34659

# Needs gobject-introspection, not available on S11.
include $(WS_MAKE_RULES)/no-evaluation.mk

include $(WS_MAKE_RULES)/gnome-component.mk

CONFIGURE_OPTIONS += --disable-static
# Required for other components.
CONFIGURE_OPTIONS += --enable-introspection
# Required for other components.
CONFIGURE_OPTIONS += --enable-shared
# Required for other components.
CONFIGURE_OPTIONS += --enable-vala
# /usr/bin/mcs accepts the --version option, which causes configure to think
# it has found GNU Mono, and enable Mono support. On Solaris, mcs is an ELF
# utility, and Mono is not available. Explicitly disable it in order to
# sidestep the issue.
CONFIGURE_OPTIONS += --enable-mono=no

COMPONENT_TEST_MASTER = $(COMPONENT_TEST_RESULTS_DIR)/results-all.master
COMPONENT_TEST_TRANSFORMS += \
        '-n ' \
        '-e "/Testing/p" ' \
        '-e "/test/p" ' \
        '-e "/Fail/p" '

REQUIRED_PACKAGES += developer/documentation-tool/gtk-doc
REQUIRED_PACKAGES += developer/vala
REQUIRED_PACKAGES += library/desktop/gobject/gobject-introspection
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/security/gpgme
REQUIRED_PACKAGES += library/zlib
