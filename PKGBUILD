# Maintainer: Wiseluster <chinaware@foxmail.com>

pkgname=vala
pkgver=0.35.1
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
sha256sums=('9ae6cdefd3409eabe4f072921844dc31f9d4488211b6d077fa48855fd00053fd')

prepare() {
  cd "${srcdir}"/${pkgname}-${pkgver}
  sed -i "s/\(PACKAGE_SUFFIX=-\).*/\1${pkgver%.*}/g" configure.ac
  autoreconf -ivf
}

build() {
  mkdir -p "${srcdir}/build-${CHOST}"
  cd "${srcdir}/build-${CHOST}"
  ../${pkgname}-${pkgver}/configure \
    --prefix=/usr \
    --build=${CHOST} \
    --host=${CHOST} \
    --enable-shared
  make
}

package() {
  cd "${srcdir}/build-${CHOST}"
  make -j1 DESTDIR="${pkgdir}" install
}
