# Maintainer: Mort Yao <soi@mort.ninja>
# Contributor: Balló György <ballogyor+arch at gmail dot com>

pkgname=fsharp
pkgver=4.0.1.5
pkgrel=1
pkgdesc="The Open Edition of the F# compiler, core library and tools"
arch=('any')
url="http://fsharp.org/"
license=('Apache')
depends=('mono>=4.0.3.20')
source=("$pkgname-$pkgver.tar.gz::https://github.com/fsharp/$pkgname/archive/$pkgver.tar.gz"
"Makefile")
md5sums=('5974b6df0aa6df01f153afadcbdc6061'
         '43db61306415c14794434aeadb60c643')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./autogen.sh --prefix=/usr
  cp $srcdir/Makefile $srcdir/fsharp-4.0.1.5/src/fsharp
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
  find "${pkgdir}" \
	 -name "*.xml" -exec sed -i -e "s|$srcdir||g" '{}' \;
}
