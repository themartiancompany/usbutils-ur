# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Tom Gundersen <teg@jklm.no>
# Contributor: Judd Vinet <jvinet@zeroflux.org>
# Contributor: Curtis Campbell <curtisjamescampbell@hotmail.com>

pkgname=usbutils
pkgver=016
pkgrel=1
pkgdesc="A collection of USB tools to query connected USB devices"
arch=(x86_64)
url="https://git.kernel.org/pub/scm/linux/kernel/git/gregkh/usbutils.git/"
license=('GPL-2.0-only' 'GPL-2.0-or-later' 'GPL-3.0-only')
depends=(glibc hwdata)
makedepends=(libusb systemd)
optdepends=(
  'coreutils: for lsusb.py usage'
  'python: for lsusb.py usage'
  'sh: for usb-devices'
)
source=(https://www.kernel.org/pub/linux/utils/usb/usbutils/$pkgname-$pkgver.tar{.xz,.sign})
sha512sums=('4483038bf91c056cd2977f5e7f449c0a62d9152d6f5d64ab7bde438ab9c1c56fe524ba10b35781c2828edd0fe89379dbaed78fa7ffe78903cae0c4e3c460f9a0'
            'SKIP')
b2sums=('2f3af61e5a7abf48cdf0a4aebc901ca1570007b54d11ae74572e16bdeb2d8e73844d76af54bd812d6d4b84ddaf6e956132ecc9a8a2849a7bffc0643e29115a49'
        'SKIP')
validpgpkeys=('647F28654894E3BD457199BE38DBBDC86092693E')  # Greg Kroah-Hartman <gregkh@linuxfoundation.org>

prepare() {
  cd $pkgname-$pkgver
  autoreconf -fiv
}

build() {
  cd $pkgname-$pkgver
  ./configure \
    --prefix=/usr \
    --datadir=/usr/share/hwdata
  make
}

package() {
  depends+=(
    libusb libusb-1.0.so
    systemd-libs libudev.so
  )

  cd $pkgname-$pkgver
  make DESTDIR="$pkgdir" install
  install -vDm 755 usbreset -t "$pkgdir/usr/bin"
  install -vDm 644 NEWS -t "$pkgdir/usr/share/doc/$pkgname/"
}
