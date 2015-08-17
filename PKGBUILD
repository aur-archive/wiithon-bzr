# Maintainer: Eduardo Parra Mazuecos <eduparra90 at gmail dot com>
# Maintainer: peace4all <markspost at rocketmail dot com>
# Contributer: Eikichi

pkgname=wiithon-bzr
pkgver=511
pkgrel=3
pkgdesc="Wiithon - WBFS Partition Manager"
arch=('i686' 'x86_64')
url="https://launchpad.net/wiithon"
license=('GPL3')
depends=('python2-sqlalchemy' 'python' 'unzip' 'gnome-icon-theme' 'pygtk' 'glibc' 'imagemagick')
makedepends=('bzr')
 if test "$CARCH" == x86_64; then
  makedepends+=('gcc-multilib' 'binutils')
 fi
install=$pkgname.install
options=('!libtool')
source=('bzr+lp:wiithon')
md5sums=('SKIP')
makeflags=-j1

pkgver() {
  cd ${srcdir}/wiithon
  bzr revno
}

build() {
  cd ${srcdir}/wiithon

  sed -i -e "s|#![ ]*/usr/bin/python|#!/usr/bin/python2|" \
	-e "s|#![ ]*/usr/bin/env python|#!/usr/bin/env python2|" \
	$(find . -name '*.py')

  make
}

package() {
  cd ${srcdir}/wiithon
  install -d ${pkgdir}/usr/{bin,games}
  make DESTDIR=${pkgdir} install
  mv ${pkgdir}/usr/games/wiithon* ${pkgdir}/usr/share/wiithon/
  ln -s /usr/share/wiithon/wiithon.py ${pkgdir}/usr/bin/wiithon
  rm -d "${pkgdir}/usr/games"
}
