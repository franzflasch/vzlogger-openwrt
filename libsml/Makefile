include $(TOPDIR)/rules.mk

PKG_NAME:=libsml
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/volkszaehler/libsml.git
PKG_RELEASE:=1
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE
PKG_SOURCE_DATE:=2022-08-20
PKG_SOURCE_VERSION:=559ca1e3ff8de7645fc4372f632e42b64cec780f

include $(INCLUDE_DIR)/package.mk

define Package/libsml
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libsml
  URL:=volkszaehler.org
  DEPENDS:=+libuuid
endef

define Package/libsml/description
  libSML is a library which implements the Smart Message Language (SML) protocol 
  specified by VDE's Forum Netztechnik/Netzbetrieb (FNN). It can be utilized to 
  communicate to FNN specified Smart Meters or Smart Meter components (EDL/MUC).
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/sml \
		CC="$(TARGET_CC)" \
		LD="$(TARGET_CROSS)ld"
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) -a $(PKG_BUILD_DIR)/sml/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/sml/lib/libsml.{a,so*} $(1)/usr/lib/
	$(LN) libsml.so.$(PKG_VERSION) $(1)/usr/lib/libsml.so
endef

define Package/libsml/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/sml/lib/libsml.{a,so*} $(1)/usr/lib/
	$(LN) libsml.so.$(PKG_VERSION) $(1)/usr/lib/libsml.so
endef

$(eval $(call BuildPackage,libsml))
