# 2017 - 2021 Cezary Jackiewicz <cezary@eko.one.pl>
# 2014 lovewilliam <ztong@vt.edu>
# sms tool for various of 3g/4g modem
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sms-tool
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/obsy/sms_tool
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2025-03-16
PKG_SOURCE_VERSION:=a322b5497ab10890d00bc1e4b8dcd6ba9a37a474
PKG_MIRROR_HASH:=ad3408761253be4bef415806a22216d37462ed2a80fdcb4ac7dbf3232dd71b4e

PKG_MAINTAINER:=Andrey Butirsky <butirsky@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE-2.0.txt

include $(INCLUDE_DIR)/package.mk

define Package/sms-tool
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=SMS tool for 3G/4G modems
	URL:=https://github.com/obsy/sms_tool
endef

define Package/sms-tool/description
	SMS Tool for 3G/4G modem
endef

define Package/sms-tool/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sms_tool $(1)/usr/bin/
endef

$(eval $(call BuildPackage,sms-tool))
