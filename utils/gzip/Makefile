#
# Copyright (C) 2006-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gzip
PKG_VERSION:=1.11
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=@GNU/gzip
PKG_HASH:=9b9a95d68fdcb936849a4d6fada8bf8686cddf58b9b26c9c4289ed0c92a77907
PKG_LICENSE:=GPL-3.0-or-later
PKG_CPE_ID:=cpe:/a:gnu:gzip

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/gzip
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Compression
  TITLE:=gzip (GNU zip) is a compression utility.
  URL:=https://www.gnu.org/software/gzip/
  MAINTAINER:=Christian Beier <dontmind@freeshell.org>
#  ALTERNATIVES:=\
#    300:/bin/gunzip:/usr/libexec/gunzip-gnu \
#    300:/bin/gzip:/usr/libexec/gzip-gnu \
#    300:/bin/zcat:/usr/libexec/zcat-gnu
endef

define Package/gzip/description
	gzip (GNU zip) is a compression utility designed to be a \
	replacement for compress.
endef

CONFIGURE_VARS += \
	gl_cv_func_getopt_gnu=yes \
	ac_cv_search_clock_gettime=no

define Package/gzip/install
	$(SED) 's,/bin/bash,/bin/sh,g' $(PKG_INSTALL_DIR)/opt/bin/{gunzip,zcat}
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/{gunzip,gzip,zcat} $(1)/opt/bin/
endef

$(eval $(call BuildPackage,gzip))
