#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# Abandoned in 2004

include $(TOPDIR)/rules.mk

PKG_NAME:=ssldump
PKG_VERSION:=0.9b3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/$(PKG_NAME)/$(PKG_NAME)/$(PKG_VERSION)
PKG_MD5SUM:=ac8c28fe87508d6bfb06344ec496b1dd

include $(INCLUDE_DIR)/package.mk

define Package/ssldump
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libopenssl +libpcap
  TITLE:=a SSLv3/TLS network protocol analyzer
  URL:=http://ssldump.sourceforge.net/
endef

define Package/ssldump/description
	ssldump is an SSLv3/TLS network protocol analyzer. It identifies TCP connections on the chosen network interface
	and attempts to interpret them as SSLv3/TLS traffic. When it identifies SSLv3/TLS traffic, it decodes the records
	and displays them in a textual form to stdout. If provided with the appropriate keying material, it will also decrypt
	the connections and display the application data traffic.
endef

CONFIGURE_ARGS += \
	--enable-static \
	--enable-shared \
	--with-openssl-inc="$(STAGING_DIR)/opt/include" \
	--with-openssl-lib="$(STAGING_DIR)/opt/lib" \
	--with-pcap-inc="$(STAGING_DIR)/opt/include" \
	--with-pcap-lib="$(STAGING_DIR)/opt/lib" \

#TARGET_CFLAGS+="-DR_TRACE_ERRORS"

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		all
endef


define Package/ssldump/install
	$(INSTALL_DIR) $(1)/opt/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ssldump $(1)/opt/sbin/
endef

$(eval $(call BuildPackage,ssldump))
