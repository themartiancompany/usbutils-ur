# Maintainer: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=002
pkgrel=1
pkgdesc="USB Device Utilities"
arch=(i686 x86_64)
license=('GPL')
groups=('base')
makedepends=('wget')
depends=('glibc' 'libusb')
url="http://linux-usb.sourceforge.net/"
source=(http://www.kernel.org/pub/linux/utils/usb/$pkgname/$pkgname-$pkgver.tar.gz)
md5sums=('05610d15c3c8c8ada3d691c320ca784a')

build() {
  cd $srcdir/$pkgname-$pkgver
  rm usb.ids
  wget http://www.linux-usb.org/usb.ids
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
