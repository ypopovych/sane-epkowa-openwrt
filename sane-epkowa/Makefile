include $(TOPDIR)/rules.mk

PKG_NAME:=sane-epkowa
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ypopovych/sane-epkowa.git
PKG_SOURCE_VERSION:=1e37efe
PKG_SOURCE_DATE:=2021-09-15
PKG_VERSION:=$(PKG_SOURCE_DATE)-$(PKG_SOURCE_VERSION)

PKG_MAINTAINER:=Yehor Popovych <popovych.yegor@gmail.com>
PKG_LICENSE:=GPL-3.0

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/sane-epkowa
  TITLE:=A SANE Epson Epkowa backend
  URL:=https://github.com/ypopovych/sane-epkowa
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libsane +libltdl +libusb-1.0 +libxml2
endef

define Package/sane-epkowa/description
   SANE Epson Epkowa backend
endef

define Package/sane-epkowa/conffiles
	/etc/sane.d/dll.d/epkowa
	/etc/sane.d/epkowa.conf
endef

define Package/sane-epkowa/install 
	$(INSTALL_DIR) $(1)/usr/lib/sane/epkowa
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/usr/lib/sane/*.so $(1)/usr/lib/sane/
	$(INSTALL_DIR) $(1)/usr/share/sane/epkowa/device
	$(CP) $(PKG_BUILD_DIR)/ipkg-install/usr/share/sane/epkowa/device/* $(1)/usr/share/sane/epkowa/device/
	$(CP) $(PKG_BUILD_DIR)/ipkg-install/usr/share/sane/*.usbid $(1)/usr/share/sane/
	$(INSTALL_DIR) $(1)/etc/sane.d/dll.d
	$(CP) $(PKG_BUILD_DIR)/ipkg-install/usr/etc/sane.d/*.conf $(1)/etc/sane.d/
	$(CP) $(PKG_BUILD_DIR)/ipkg-install/usr/etc/sane.d/dll.d/* $(1)/etc/sane.d/dll.d/
endef

$(eval $(call BuildPackage,sane-epkowa))
