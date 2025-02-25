include $(TOPDIR)/rules.mk

PKG_NAME:=nghttp2
PKG_VERSION:=1.44.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://github.com/nghttp2/nghttp2/releases/download/v$(PKG_VERSION)
PKG_HASH:=5699473b29941e8dafed10de5c8cb37a3581edf62ba7d04b911ca247d4de3c5d

PKG_MAINTAINER:=Hans Dedecker <dedeckeh@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libnghttp2
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Library implementing the framing layer of HTTP/2
  ABI_VERSION:=14
endef

define Package/libnghttp2/description
 C library implementing the framing layer of the HTTP/2 protocol. It can be used to build a HTTP/2-capable HTTP client or server
endef

CMAKE_OPTIONS += \
        -DENABLE_LIB_ONLY=ON

define Build/InstallDev
	$(call Build/InstallDev/cmake,$(1))
	$(SED) 's,/opt/include,$$$${prefix}/include,g' $(1)/opt/lib/pkgconfig/libnghttp2.pc
	$(SED) 's,/opt/lib,$$$${prefix}/lib,g' $(1)/opt/lib/pkgconfig/libnghttp2.pc
endef

define Package/libnghttp2/install
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libnghttp2.so.* $(1)/opt/lib
endef

$(eval $(call BuildPackage,libnghttp2))
