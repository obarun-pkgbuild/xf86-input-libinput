# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/xf86-input-libinput
# 						 Maintainer: Laurent Carlier <lordheavym@gmail.com>

pkgname=xf86-input-libinput
pkgver=0.27.1
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
sha512sums=('01379f5d71bf39214c4dff428173512df57fd12e782f3fcde757be923aa0dbf4e010a0395a81bd8e4fb518edc7e05ca1ee64b1e313eb4df5d4990315580609a1')
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

