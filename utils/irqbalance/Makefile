# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=irqbalance
PKG_VERSION:=1.9.0
PKG_RELEASE:=3

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/Irqbalance/irqbalance.git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_MIRROR_HASH:=9af2e51d2696bc51400223dee2009071bee5f12b3a5050f18c7de23632e2190d

PKG_MAINTAINER:=Hannu Nyman <hannu.nyman@iki.fi>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include $(INCLUDE_DIR)/meson.mk

PKG_BUILD_DEPENDS += glib2

define Package/irqbalance
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=$(ICONV_DEPENDS) $(INTL_DEPENDS)
  TITLE:=IRQ usage balancing for multi-core systems
  URL:=https://github.com/Irqbalance/irqbalance
endef

define Package/irqbalance/description
 The purpose of irqbalance is to distribute hardware interrupts across
 processors/cores on a multiprocessor/multicore system in order to
 increase performance.
endef

#define Package/irqbalance/conffiles
#/etc/config/irqbalance
#endef

MESON_ARGS += \
	-Dcapng=disabled \
	-Dui=disabled

define Package/irqbalance/install
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/irqbalance $(1)/opt/sbin/
endef

$(eval $(call BuildPackage,irqbalance))
