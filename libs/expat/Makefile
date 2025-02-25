#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=expat
PKG_VERSION:=2.4.7
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=@SF/expat
PKG_HASH:=9875621085300591f1e64c18fd3da3a0eeca4a74f884b9abac2758ad1bd07a7d

PKG_MAINTAINER:=Ted Hess <thess@kitschensync.net>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING
PKG_CPE_ID:=cpe:/a:libexpat:expat

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libexpat
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=An XML parsing library
  URL:=https://libexpat.github.io/
endef

define Package/libexpat/description
 A fast, non-validating, stream-oriented XML parsing library.
endef

CMAKE_OPTIONS += \
	-DDOCBOOK_TO_MAN=OFF \
	-DEXPAT_BUILD_TOOLS=OFF \
	-DEXPAT_BUILD_EXAMPLES=OFF \
	-DEXPAT_BUILD_TESTS=OFF \
	-DEXPAT_BUILD_DOCS=OFF \
	-DEXPAT_WITH_LIBBSD=OFF \
	-DEXPAT_ENABLE_INSTALL=ON \
	-DEXPAT_DTD=OFF \
	-DEXPAT_NS=OFF \
	-DEXPAT_DEV_URANDOM=OFF

# XXX * Linux (including <3.17) / BSD / macOS (including <10.7) (/dev/urandom): XML_DEV_URANDOM
TARGET_CFLAGS += -DXML_DEV_URANDOM

define Package/libexpat/install
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libexpat.so.* $(1)/opt/lib/
endef

$(eval $(call BuildPackage,libexpat))
