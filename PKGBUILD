# Maintainer: William Giokas <1007380@gmail.com>
# Contributor: Matt Parnell /ilikenwf <parwok@gmail.com>

pkgname=libxft-git
_pkgname=libXft
pkgver=2.3.1.r3.gc5e760a
pkgrel=4
pkgdesc="FreeType-based font drawing library for X"
arch=('i686' 'x86_64')
license=('custom')
url="http://xorg.freedesktop.org/"
depends=('libx11' 'freetype2' 'fontconfig>=2.6.0' 'libxrender')
makedepends=('pkg-config' 'xorg-util-macros')
provides=('libxft'
          # soprovides:
          'libXft.so'
          )
conflicts=('libxft')

source=("git://git.freedesktop.org/git/xorg/lib/libXft")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  git describe --long --always | sed -E 's/libXft-//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/$_pkgname"
  ./autogen.sh --prefix=/usr --sysconfdir=/etc --sbindir=/usr/bin
  make
}

package() {
  cd "$srcdir/$_pkgname"
  make DESTDIR="${pkgdir}" install
  install -d -m755 "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/"
}
