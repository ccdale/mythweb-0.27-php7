# $Id$
# Maintainer: Chris Allison <chris.allison@hotmail.com>
#
## from original PKGBUILD for mythplugins
## Maintainer: Jonathan Conder <jonno.conder@gmail.com>
## Contributor: Giovanni Scafora <giovanni@archlinux.org>

pkgbase=mythplugins
pkgname=('mythplugins-mythweb-php7')
pkgver=0.27.5
pkgrel=3
arch=('i686' 'x86_64')
url="http://www.mythtv.org"
license=('GPL')
pkgdesc="Web interface for the MythTV scheduler"
depends=('mythtv')
optdepends=('lighttpd'
          'php-apache')
install='mythplugins-mythweb.install'
replaces=('mythplugins-mythweb')
makedepends=('mythtv')
source=("mythweb-$pkgver.tar.gz::https://github.com/MythTV/mythweb/archive/v$pkgver.tar.gz" "mythweb-php7.patch")
sha256sums=('5dc3fd9e60f59dea4264fb064b40d73f2534c99d0399da6223a42d2f563e9d13'
            'cef934f51c66eee45a89e4425e4c88c0c29741c49bd516a3c9a3dda1485f2cc1')

prepare() {
  cd "$srcdir/mythweb-$pkgver"

  sed -re 's@/usr/local.*/usr/share@/usr/share@' -i 'mythweb.php'

  patch -Np1 <../../mythweb-php7.patch
}

# build() {
#     :
# }

package() {
  mkdir -p "$pkgdir/var/lib/mythtv/mythweb"/{image_cache,php_sessions}
  cp -R "$srcdir/mythweb-$pkgver"/* "$pkgdir/var/lib/mythtv/mythweb"
  chown -R http:http "$pkgdir/var/lib/mythtv/mythweb"
  chmod g+rw "$pkgdir/var/lib/mythtv/mythweb"/{image_cache,php_sessions}
}
