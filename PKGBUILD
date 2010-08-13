# Maintainer: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=0.90
pkgrel=1
pkgdesc="USB Device Utilities"
arch=(i686 x86_64)
license=('GPL')
groups=('base')
makedepends=('wget')
depends=('glibc' 'libusb')
url="http://linux-usb.sourceforge.net/"
source=(http://www.kernel.org/pub/linux/utils/usb/$pkgname/$pkgname-$pkgver.tar.gz)

build() {
  cd $srcdir/$pkgname-$pkgver
  rm usb.ids
  wget http://www.linux-usb.org/usb.ids
  ./configure --prefix=/usr --datadir=/usr/share/hwdata --disable-zlib
  make || return 1
  make DESTDIR=$pkgdir install
  # fix pkgconfig file
  mkdir -p $pkgdir/usr/lib
  mv $pkgdir/usr/share/hwdata/pkgconfig $pkgdir/usr/lib/
}
md5sums=('53f0269e2cba704d5a35dfe291511292')
