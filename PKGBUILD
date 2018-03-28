# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/xf86-input-libinput
# 						 Maintainer: Laurent Carlier <lordheavym@gmail.com>

pkgname=xf86-input-libinput
pkgver=0.27.0
pkgrel=3
pkgdesc="Generic input driver for the X.Org server based on libinput"
arch=('x86_64')
license=('custom')
url="http://xorg.freedesktop.org/"
depends=('libinput>=1.2.0')
makedepends=('xorg-server-devel' 'X-ABI-XINPUT_VERSION=24.1' 'libxi' 'libx11' 'resourceproto' 'scrnsaverproto')
conflicts=('xorg-server<1.19.0' 'X-ABI-XINPUT_VERSION<24' 'X-ABI-XINPUT_VERSION>=25')
groups=('xorg-drivers')
source=(https://xorg.freedesktop.org/releases/individual/driver/${pkgname}-${pkgver}.tar.bz2
        fix-left-handed-property-not-set-on-all-pointers.patch)
sha512sums=('716a9b43438acd6b7c6a834a08ecec244fecdc31e77241998414bf1748781026cd6c6e85947155c44400e0192769a714dfbfa0ed42ba3677347cd89ac1081743'
            '6f77002753c1f219cb46bd83fa0c500d8772db71e080ce6107b4887d582cb567c81e237a1bb91e639ffc0f751443a4170282e437f30ad7c9405acbaf033943dc')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

 
prepare() {
  cd ${pkgname}-${pkgver}

  # https://bugs.freedesktop.org/show_bug.cgi?id=105667
  patch -Np1 -i ../fix-left-handed-property-not-set-on-all-pointers.patch
}

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

