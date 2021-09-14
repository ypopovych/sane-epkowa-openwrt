include $(TOPDIR)/rules.mk

PKG_NAME:=sane-epkowa
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=http://172.16.1.174:3333/epkowa.git
PKG_SOURCE_VERSION:=ea89443
PKG_SOURCE_DATE:=2021-09-14
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
  DEPENDS:=+libsane +libltdl +libusb-1.0
endef

define Package/sane-epkowa/description
   SANE Epson Epkowa backend
endef

define Package/sane-epkowa/conffiles
	/etc/sane.d/epkowa.conf
endef

define Package/sane-epkowa/install 
	$(INSTALL_DIR) $(1)/usr/lib/sane
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/libsane-epkowa.so $(1)/usr/lib/sane/
	$(INSTALL_DIR) $(1)/etc/sane.d
	$(CP) $(SOURCE)/data/epkowa.conf $(1)/etc/sane.d/
endef

$(eval $(call BuildPackage,sane-epkowa))
