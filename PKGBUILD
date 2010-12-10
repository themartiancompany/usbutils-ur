# Maintainer: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=0.91
pkgrel=4
pkgdesc="USB Device Utilities"
arch=(i686 x86_64)
license=('GPL')
groups=('base')
makedepends=('wget')
depends=('glibc' 'libusb' 'libusb-compat')
url="http://linux-usb.sourceforge.net/"
source=(http://www.kernel.org/pub/linux/utils/usb/$pkgname/$pkgname-$pkgver.tar.gz)
md5sums=('49de2403b40bf3a9863faaa8d3858deb')

build() {
  cd $srcdir/$pkgname-$pkgver
  rm usb.ids
  wget http://www.linux-usb.org/usb.ids
  ./configure --prefix=/usr --datadir=/usr/share/hwdata --disable-zlib
  make 
  make DESTDIR=$pkgdir install
  # fix pkgconfig file
  mkdir -p $pkgdir/usr/lib
  mv $pkgdir/usr/share/pkgconfig $pkgdir/usr/lib/
}
