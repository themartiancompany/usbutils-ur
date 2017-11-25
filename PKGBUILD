# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Tom Gundersen <teg@jklm.no>
# Contributor: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>
pkgname=usbutils
pkgver=009
pkgrel=1
pkgdesc="USB Device Utilities"
arch=(x86_64)
license=('GPL')
groups=('base')
depends=('libusb' 'hwids')
optdepends=('python2: for lsusb.py usage'
            'coreutils: for lsusb.py usage')
url="http://linux-usb.sourceforge.net/"
source=("http://www.kernel.org/pub/linux/utils/usb/usbutils/${pkgname}-${pkgver}.tar.xz"
        fix-python2.patch)
md5sums=('a7cf9e8903041987efa5e5e0080e0b4d'
         '45c9e0fe5581b44a18b613977911aa2a')

build() {
  cd $srcdir/$pkgname-$pkgver
  # patch lsusb.py to use correct usb.ids file and python2 interpreter
  patch -Np1 -i $srcdir/fix-python2.patch
  ./configure --prefix=/usr --datadir=/usr/share/hwdata --disable-zlib
  make
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make DESTDIR=$pkgdir install
  # this is now in the hwids package
  rm -rf $pkgdir/usr/{share/hwdata,sbin}
}
