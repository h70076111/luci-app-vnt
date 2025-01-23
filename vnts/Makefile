include $(TOPDIR)/rules.mk

PKG_NAME:=vnts
PKG_VERSION:=1.2.12

ifeq ($(ARCH),mipsel)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=mipsel-unknown-linux-musl-$(PKG_VERSION)
endif
ifeq ($(ARCH),mips)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=mips-unknown-linux-musl-$(PKG_VERSION)
endif
ifeq ($(ARCH),arm)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=arm-unknown-linux-musleabi-$(PKG_VERSION)
endif
ifeq ($(BOARD),kirkwood)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=arm-unknown-linux-musleabi-$(PKG_VERSION)
endif
ifeq ($(ARCH),armv7)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=armv7-unknown-linux-musleabi-$(PKG_VERSION)
endif
ifeq ($(ARCH),aarch64)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=aarch64-unknown-linux-musl-$(PKG_VERSION)
endif
ifeq ($(ARCH),arm64)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=aarch64-unknown-linux-musl-$(PKG_VERSION)
endif
ifeq ($(ARCH),armv8)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=aarch64-unknown-linux-musl-$(PKG_VERSION)
endif
ifeq ($(ARCH),i386)
	PKG_VERSION:=1.2.11
	APP_ARCH:=i686-unknown-linux-musl-$(PKG_VERSION)
endif
ifeq ($(ARCH),x86_64)
	PKG_VERSION:=v$(PKG_VERSION)
	APP_ARCH:=x86_64-unknown-linux-musl-$(PKG_VERSION)
endif

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	TITLE:=An efficient VPN 
	DEPENDS:=@(i386||x86_64||arm||aarch64||mipsel||mips)
	URL:=https://github.com/vnt-dev/vnts
endef

define Package/$(PKG_NAME)/description
  简便高效的异地组网、内网穿透工具（服务端）
endef

define Build/Prepare
	[ ! -f $(PKG_BUILD_DIR)/$(PKG_NAME)-$(APP_ARCH).tar.gz ] && wget https://github.com/vnt-dev/vnts/releases/download/$(PKG_VERSION)/$(PKG_NAME)-$(APP_ARCH).tar.gz -O $(PKG_NAME)-$(APP_ARCH).tar.gz
	tar -xzvf $(PKG_NAME)-$(APP_ARCH).tar.gz -C $(PKG_BUILD_DIR)
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/vnts $(1)/usr/bin/vnts
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
