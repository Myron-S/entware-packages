#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libmad
PKG_VERSION:=0.16.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/tenacityteam/libmad/tar.gz/$(PKG_VERSION)?
PKG_HASH:=6c14c2f4dcf7fd32e447eef99d6c53faded52e22f95e223e6f58844030851b99

PKG_MAINTAINER:=Ted Hess <thess@kitschensync.net>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_CPE_ID:=cpe:/a:underbit:mad_libmad

CMAKE_INSTALL:=1
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libmad
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=An high-quality MPEG audio decoding library
  URL:=http://www.underbit.com/products/mad/
endef

define Package/libmad/description
	MAD is a high-quality MPEG audio decoder. It currently supports
	MPEG-1 and the MPEG-2 extension to lower sampling frequencies,
	as well as the de facto MPEG 2.5 format. All three audio layers -
	Layer I, Layer II, and Layer III (i.e. MP3) - are fully implemented.
endef

CMAKE_OPTIONS += \
	-DOPTIMIZE=SPEED

TARGET_CFLAGS:= $(filter-out -O%,$(TARGET_CFLAGS)) -O2

define Package/libmad/install
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libmad.so.* $(1)/opt/lib/
endef

$(eval $(call BuildPackage,libmad))
