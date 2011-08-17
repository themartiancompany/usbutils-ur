# Maintainer: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=004
pkgrel=1
_usb_ids_date=2011.08.17
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
        fix-python2.patch
        usb.ids-${_usb_ids_date})  # from http://linux-usb.sourceforge.net/usb.ids
md5sums=('481e1de453bcabbd5f43125bb4df2ab7'
         '45766196895b4cc50b53cd56e1bbf3d1'
         'f04c301b5363ef618f0ec776deff3117')

build() {
  cd $srcdir/$pkgname-$pkgver
  rm usb.ids
  cp $srcdir/usb.ids-${_usb_ids_date} usb.ids
  # patch lsusb.py to use correct usb.ids file and python2 interpreter
  patch -Np1 -i $srcdir/fix-python2.patch
  ./configure --prefix=/usr --datadir=/usr/share/hwdata --disable-zlib
  make
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make DESTDIR=$pkgdir install
  # fix pkgconfig file
  install -dm755 $pkgdir/usr/lib
  mv $pkgdir/usr/share/pkgconfig $pkgdir/usr/lib/
}
md5sums=('481e1de453bcabbd5f43125bb4df2ab7'
         '45766196895b4cc50b53cd56e1bbf3d1'
         'f04c301b5363ef618f0ec776deff3117')
