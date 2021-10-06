#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rmlint
PKG_VERSION:=2.10.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/sahib/rmlint/tar.gz/v${PKG_VERSION}?
PKG_HASH:=10e72ba4dd9672d1b6519c0c94eae647c5069c7d11f1409a46e7011dd0c6b883

PKG_MAINTAINER:=Alexandra Alter <alexandra.alter@protonmail.com>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_BUILD_DEPENDS:=scons/host

include $(INCLUDE_DIR)/package.mk
include ../../devel/scons/scons.mk

define Package/rmlint
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:= rmlint
  URL:=https://github.com/sahib/rmlint
  DEPENDS+= +glib2
endef

define Package/rmlint/description
  Extremely fast tool to remove duplicates and other lint from your filesystem
endef

SCONS_VARS = \
        CFLAGS="$(TARGET_CFLAGS) $(EXTRA_CFLAGS) -L$(STAGING_DIR)/usr/lib" \
        LINKFLAGS="$(TARGET_LDFLAGS)"

SCONS_OPTIONS += \
        implicit_link=no
        chrpath=no
        manbuild=no
        sysroot="$(TOOLCHAIN_DIR)" \
        target="$(TARGET_CROSS:-=)"

define Package/rmlint/install
        $(INSTALL_DIR) $(1)/usr/bin
        $(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/rmlint $(1)/usr/bin/
endef

$(eval $(call BuildPackage,rmlint))
