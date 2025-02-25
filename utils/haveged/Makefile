#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=haveged
PKG_VERSION:=1.9.18
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/jirka-h/haveged/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=b835fa02b52ee7d06276e028571cadcb14d08f5e5a4b5767adf81451f70561c7
PKG_BUILD_DIR:=$(BUILD_DIR)/haveged-$(PKG_VERSION)
PKG_LICENSE:=GPLv3

PKG_MAINTAINER:=Hannu Nyman <hannu.nyman@iki.fi>

PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk

define Package/haveged
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libhavege
  TITLE:=Feeds the kernel entropy pool by timing CPU loops.
  URL:=http://www.issihosts.com/haveged/
endef

define Package/libhavege
  CATEGORY:=Libraries
  TITLE:=Library for haveged
  URL:=http://www.issihosts.com/haveged/
endef

CONFIGURE_ARGS+= \
      --enable-daemon=yes \
      --enable-threads=no \
      --enable-olt=no

define Build/InstallDev
	$(INSTALL_DIR) $(1)/opt/include
	$(CP) $(PKG_BUILD_DIR)/src/havege.h $(1)/opt/include/
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_BUILD_DIR)/src/.libs/libhavege.{a,so*} $(1)/opt/lib/
endef

define Package/haveged/install
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/S02haveged $(1)/opt/etc/init.d/
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/.libs/haveged $(1)/opt/sbin/
endef

define Package/libhavege/install
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_BUILD_DIR)/src/.libs/libhavege.so* $(1)/opt/lib/
endef

$(eval $(call BuildPackage,haveged))
$(eval $(call BuildPackage,libhavege))
