# Maintainer: Wiseluster <chinaware@foxmail.com>

pkgname=vala
pkgver=0.34.4
pkgrel=1
pkgdesc="Compiler for the GObject type system"
arch=('i686' 'x86_64')
url="https://wiki.gnome.org/Projects/Vala"
license=("LGPL")
makedepends=("gcc"
             "pkg-config"
             "libxslt")
depends=("glib2")
source=(https://download.gnome.org/sources/${pkgname}/${pkgver%.*}/${pkgname}-${pkgver}.tar.xz)
sha256sums=('6b17bd339414563ebc51f64b0b837919ea7552d8a8ffa71cdc837d25c9696b83')

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  autoreconf -fiv
}

build() {
  mkdir -p "${srcdir}/build-${CHOST}"
  cd "${srcdir}/build-${CHOST}"
  ../${pkgname}-${pkgver}/configure \
    --prefix=/usr \
    --build=${CHOST} \
    --host=${CHOST} \
    --target=${CHOST} \
    --enable-shared
  make -j1
}

package() {
  cd "${srcdir}/build-${CHOST}"
  make -j1 DESTDIR="${pkgdir}" install
}
