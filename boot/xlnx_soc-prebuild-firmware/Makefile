include $(TOPDIR)/rules.mk

PKG_NAME:=xlnx_soc-prebuilt-firmware
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/Xilinx/soc-prebuilt-firmware.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=xlnx_rel_v2025.1
PKG_HASH:=5d94916507ae8c4c86126edf666bc799f9f088d0f383490d88e7ba474aa04460
PKG_VERSION:=2025.1

PKG_MAINTAINER:=Robbe Gaeremynck <robbe.gaeremynck@outlook.com>

include $(INCLUDE_DIR)/host-build.mk
PKG_BUILD_DIR:=$(HOST_BUILD_DIR)
include $(INCLUDE_DIR)/package.mk

define Package/pmufw
	SECTION:=boot
	CATEGORY:=Firmware
	TITLE:=Power Management Unit Firmware (PMUFW) for zynqmp
	DEPENDS:= \
		+microblaze_binutils
endef

TOOLCHAIN_DIR=$(STAGING_DIR_HOST)/../toolchain-microblaze
TARGET:=microblaze-xilinx-elf
CROSS_COMPILE:=$(TARGET)-

define Build/Compile
	:
endef

define Build/InstallDev
	mkdir -p $(STAGING_DIR_IMAGE)
	$(TOOLCHAIN_DIR)/bin/$(CROSS_COMPILE)objcopy -O binary $(PKG_BUILD_DIR)/zcu102-zynqmp/pmufw.elf $(STAGING_DIR_IMAGE)/pmufw.bin
endef

define Package/pmufw/install
	:
endef

$(eval $(call BuildPackage,pmufw))
