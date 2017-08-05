# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/xf86-input-libinput
# 						 Maintainer: Laurent Carlier <lordheavym@gmail.com>

pkgname=xf86-input-libinput
pkgver=0.25.1
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
sha512sums=('9a8d16bdffb73a5318d22e352826c410ccb6f8c7ade31c23823bd6c17202bb67e917dfe8d4cab6e54fdf15f201d14d80b6306cedc5f93f66989edfcab5082ece')
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

