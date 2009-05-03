# Maintainer: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=0.81
pkgrel=1
pkgdesc="USB Device Utilities"
arch=(i686 x86_64)
license=('GPL')
groups=('base')
makedepends=('wget')
depends=('glibc' 'libusb')
url="http://linux-usb.sourceforge.net/"
source=(http://downloads.sourceforge.net/sourceforge/linux-usb/usbutils-$pkgver.tar.gz)
md5sums=('ba5e44d49ebf382015e96f43ce982abb')

build() {
  cd $startdir/src/$pkgname-$pkgver
  rm usb.ids
  wget http://www.linux-usb.org/usb.ids
  ./configure --prefix=/usr --datadir=/usr/share/hwdata --disable-zlib
  make || return 1
  make DESTDIR=$startdir/pkg install
}

