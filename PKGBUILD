# Maintainer: Charles Bos <charlesbos1 AT gmail>
# Contributor: Guillaume ALAUX <guillaume@archlinux.org>
# Contributor: Kevin Piche <kevin@archlinux.org>
# Contributor: Aaron Griffin <aaron@archlinux.org>
# Contributor: dorphell <dorphell@archlinux.org>

pkgname=easytag-resopt
_realname=easytag
pkgver=2.2.4
pkgrel=2
pkgdesc='Simple application for viewing and editing tags in audio files (patched for devices with smaller screens)'
arch=('i686' 'x86_64')
license=('GPL')
url='http://easytag.sourceforge.net/'
makedepends=('intltool' 'itstool')
depends=('id3lib' 'libid3tag' 'gtk3' 'libvorbis' 'flac' 'speex' 'wavpack' 'taglib'
         'desktop-file-utils' 'hicolor-icon-theme' 'opusfile')
provides=(${_realname}=${pkgver})
conflicts=(${_realname})
install=${_realname}.install
source=(http://download.gnome.org/sources/${_realname}/${pkgver:0:3}/${_realname}-${pkgver}.tar.xz
        resolution.patch)
sha256sums=('458329ab17e07fac5e92a2d732f0f4e9b12ea8aa31707506b39d3b2428d0c091'
            '7fcf7c310f15feb92d0734f7eede29f2bde24951bb4186019e2791362fec4f01')

prepare() {
  cd "${srcdir}/${_realname}-${pkgver}"
  patch -Np1 -i "${srcdir}/resolution.patch"
}

build() {
  cd "${srcdir}/${_realname}-${pkgver}"
  ./configure --prefix=/usr
  make
}

check() {
  cd "${srcdir}/${_realname}-${pkgver}"
  make -k check
}

package() {
  cd "${srcdir}/${_realname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
}
