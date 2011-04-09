# Maintainer: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=002
pkgrel=2
pkgdesc="USB Device Utilities"
arch=(i686 x86_64)
license=('GPL')
groups=('base')
makedepends=('wget')
depends=('glibc' 'libusb')
optdepends=('python2: for lsusb.py usage'
           'coreutils: for lsusb.py usage')
url="http://linux-usb.sourceforge.net/"
source=(http://www.kernel.org/pub/linux/utils/usb/$pkgname/$pkgname-$pkgver.tar.gz
        fix-python2.patch)
md5sums=('05610d15c3c8c8ada3d691c320ca784a'
         '45766196895b4cc50b53cd56e1bbf3d1')

build() {
  cd $srcdir/$pkgname-$pkgver
  rm usb.ids
  wget http://www.linux-usb.org/usb.ids
  # patch lsusb.py to use correct usb.ids file and python2 interpreter
  patch -Np1 -i ../fix-python2.patch
  ./configure --prefix=/usr --datadir=/usr/share/hwdata --disable-zlib
  make
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make DESTDIR=$pkgdir install
  # fix pkgconfig file
  mkdir -p $pkgdir/usr/lib
  mv $pkgdir/usr/share/pkgconfig $pkgdir/usr/lib/
}
