#
# Copyright (C) 2009-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sslh
PKG_VERSION:=v1.22c
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://rutschle.net/tech/sslh/
PKG_HASH:=8e3742d14edf4119350cfdc7bb96b89134d9218eb6d2a6e1f70891ca18a649b1

PKG_MAINTAINER:=Jonathan McCrohan <jmccrohan@gmail.com>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

define Package/sslh
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  TITLE:=SSL/SSH multiplexer
  DEPENDS:=+libconfig +libcap +libpcre2
  URL:=https://rutschle.net/tech/sslh/README.html
endef

define Package/sslh/conffiles
/opt/etc/sslh.conf
endef

MAKE_FLAGS += \
  USELIBCAP=1

define Package/sslh/install
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sslh-fork $(1)/opt/sbin/sslh
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) files/S14$(PKG_NAME) $(1)/opt/etc/init.d
#	$(INSTALL_DIR) $(1)/etc/config
#	$(INSTALL_CONF) files/$(PKG_NAME).config $(1)/etc/config/$(PKG_NAME)
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/basic.cfg $(1)/opt/etc/sslh.conf
	$(INSTALL_DIR) $(1)/opt/var/empty
endef

$(eval $(call BuildPackage,sslh))
