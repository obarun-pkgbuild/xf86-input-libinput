# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/xf86-input-libinput
# 						 Maintainer: Laurent Carlier <lordheavym@gmail.com>

pkgname=xf86-input-libinput
pkgver=0.26.0
pkgrel=2
pkgdesc="Generic input driver for the X.Org server based on libinput"
arch=('x86_64')
license=('custom')
url="http://xorg.freedesktop.org/"
depends=('libinput>=1.2.0')
makedepends=('xorg-server-devel' 'X-ABI-XINPUT_VERSION=24.1' 'libxi' 'libx11' 'resourceproto' 'scrnsaverproto')
conflicts=('xorg-server<1.19.0' 'X-ABI-XINPUT_VERSION<24' 'X-ABI-XINPUT_VERSION>=25')
groups=('xorg-drivers')
source=(https://xorg.freedesktop.org/releases/individual/driver/${pkgname}-${pkgver}.tar.bz2)
sha512sums=('b52a27e916f7e86576500ef2bc3ce640676f5a710543755865a723628c0e01a575989460853bac184ed696961e3f8fca72ecba8ad4625be8cd9e31f9a55f5e97')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${pkgname}-${pkgver}

  ./configure --prefix=/usr --disable-static
  make
}

package() {
  cd ${pkgname}-${pkgver}

  make DESTDIR="${pkgdir}" install

  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/"
}

