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

BUILD_BITS=		64

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		zenity
COMPONENT_VERSION=	3.24.0
COMPONENT_PROJECT_URL=	https://wiki.gnome.org/Projects/Zenity
COMPONENT_ARCHIVE_HASH= \
	sha256:6ff0a026ec94e5bc1b30f78df91e54f4f82fd982f4c29b52fe5dacc886a9f7f7
COMPONENT_ANITYA_ID=	13165

TPNO=			34565

# zenity is not unlockable in S11.3 gnome-incorporation
include $(WS_MAKE_RULES)/no-evaluation.mk

include $(WS_MAKE_RULES)/gnome-component.mk

# Ensures gdialog script specifies explicit version of perl.
CONFIGURE_ENV += PERL="$(PERL)"

CONFIGURE_OPTIONS += --enable-libnotify
CONFIGURE_OPTIONS += --enable-webkitgtk

# Assumes GNU msgfmt in PATH.
COMPONENT_BUILD_ENV += PATH="$(GNUBIN):$(PATH)"

REQUIRED_PACKAGES += library/desktop/gdk-pixbuf
REQUIRED_PACKAGES += library/desktop/gtk3
REQUIRED_PACKAGES += library/desktop/libnotify
REQUIRED_PACKAGES += library/desktop/pango
REQUIRED_PACKAGES += library/desktop/webkitgtk4
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += $(PERL_PKG)
REQUIRED_PACKAGES += x11/library/libx11
