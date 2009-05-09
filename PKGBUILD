# Maintainer: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=0.82
pkgrel=1
pkgdesc="USB Device Utilities"
arch=(i686 x86_64)
license=('GPL')
groups=('base')
makedepends=('wget')
depends=('glibc' 'libusb')
url="http://linux-usb.sourceforge.net/"
source=(http://downloads.sourceforge.net/sourceforge/linux-usb/usbutils-$pkgver.tar.gz)
md5sums=('6e393cc7423b5d228fa3d34c21481ae4')

build() {
  cd $startdir/src/$pkgname-$pkgver
  rm usb.ids
  wget http://www.linux-usb.org/usb.ids
  ./configure --prefix=/usr --datadir=/usr/share/hwdata --disable-zlib
  make || return 1
  make DESTDIR=$startdir/pkg install
}
