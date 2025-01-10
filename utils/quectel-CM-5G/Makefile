include $(TOPDIR)/rules.mk

PKG_NAME:=quectel-cm
PKG_VERSION:=1.6.5
PKG_RELEASE:=2

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/quectel-CM-5G
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=WWAN
  TITLE:=Qconnector Manager for Quectel WWAN modules
  DEPENDS:= \
    +kmod-usb-net-cdc-mbim \
    +kmod-usb-net-qmi-wwan \
    +kmod-usb-net-qmi-wwan-fibocom \
    +kmod-usb-net-qmi-wwan-quectel \
    +kmod-usb-serial-option
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) -C "$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="$(EXTRA_CFLAGS)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		ARCH="$(LINUX_KARCH)" \
		M="$(PKG_BUILD_DIR)" \
		CC="$(TARGET_CC)"
endef

define Package/quectel-CM-5G/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/quectel-CM $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/quectel-{mbim,qmi}-proxy $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/lib/netifd/proto
	$(INSTALL_BIN) ./files/quectel.sh $(1)/lib/netifd/proto/

	$(INSTALL_DIR) $(1)/etc/hotplug.d/net
	$(INSTALL_BIN) ./files/smp-affinity-mhi-pcie.sh $(1)/etc/hotplug.d/net/21-smp-affinity-mhi-pcie
	$(INSTALL_BIN) ./files/smp-affinity-qmi-usb.sh $(1)/etc/hotplug.d/net/22-smp-affinity-qmi-usb
endef

$(eval $(call BuildPackage,quectel-CM-5G))
