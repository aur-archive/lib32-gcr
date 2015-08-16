# Maintainer: ZavonAJ <zavonaj.linux@gmail.com>

_pkgbase=gcr
pkgname=lib32-${_pkgbase}
pkgver=3.12.2
pkgrel=1
pkgdesc="A library for bits of crypto UI and parsing (32 bit)"
arch=(x86_64)
url="http://www.gnome.org"
license=('GPL2')
depends=('lib32-gtk3' 'lib32-p11-kit' "${_pkgbase}")
# lib32-fontconfig lib32-mesa lib32-libxrender lib32-libpng lib32-libgcrypt
makedepends=('intltool' 'gcc-multilib' 'gobject-introspection')
options=(!libtool)
install=gcr.install
source=(http://download.gnome.org/sources/${_pkgbase}/3.12/${_pkgbase}-${pkgver}.tar.xz)
sha256sums=('456e20615ab178aa92eeabdea64dcce535c10d5af189171d9375291a2447d21c')

build() {
  export CC='gcc -m32'
  export CXX='g++ -m32'
  export PKG_CONFIG_PATH='/usr/lib32/pkgconfig'
  
  cd ${_pkgbase}-${pkgver}
  ./configure --prefix=/usr \
    --disable-static \
    --disable-update-mime \
    --disable-schemas-compile \
    --libdir=/usr/lib32 \
    --libexec=/usr/lib32/${_pkgbase}
  make
}

package() {
  make -C ${_pkgbase}-${pkgver} DESTDIR="${pkgdir}" install
  rm -rf "${pkgdir}"/usr/{bin,include,share}
}

