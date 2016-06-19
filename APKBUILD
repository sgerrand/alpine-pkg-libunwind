# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=libunwind
pkgver=1.1
pkgrel=0
pkgdesc="Libunwind defines a portable and efficient C programming interface (API) to determine the call-chain of a program."
url="http://www.nongnu.org/libunwind/"
arch="all"
license="X11"
depends=""
depends_dev=""
makedepends="$depends_dev autoconf automake gcc libtool linux-headers"
install=""
subpackages="$pkgname-dev $pkgname-doc"
source="http://download.savannah.gnu.org/releases/$pkgname/$pkgname-$pkgver.tar.gz
		10-disable-tests.patch"

_builddir="$srcdir"/$pkgname-$pkgver
prepare() {
	local i
	cd "$_builddir"
	update_config_sub || return 1
	for i in $source; do
		case $i in
		*.patch) msg $i; patch -p1 -i "$srcdir"/$i || return 1;;
		esac
	done
}

build() {
	cd "$_builddir"
	./configure \
		--build=$CBUILD \
		--host=$CHOST \
		--prefix=/usr \
		--sysconfdir=/etc \
		--mandir=/usr/share/man \
		--localstatedir=/var \
		|| return 1
	make || return 1
}

package() {
	cd "$_builddir"
	make DESTDIR="$pkgdir" install || return 1
}

md5sums="fb4ea2f6fbbe45bf032cd36e586883ce  libunwind-1.1.tar.gz
1f6a9820ff7839cc44b285d2239fa69b  10-disable-tests.patch"
sha256sums="9dfe0fcae2a866de9d3942c66995e4b460230446887dbdab302d41a8aee8d09a  libunwind-1.1.tar.gz
920e037b775a05e762cc47b0bc361e403337db986e3d471b95933375738ee31f  10-disable-tests.patch"
sha512sums="bfe04f2bfac9f9e47c37f0b23ed2f264d8d3d3d6f1392fe9d794ee13cad216b3740979e922e4276fb65c1ccdc836fce48812cb5459ecdd2a89a621036a35d7c1  libunwind-1.1.tar.gz
6302a9ef7c785c459f2966af5a0367bf752e4c7ea6e4f6136f51d674a66b253aecb81072ffb65c3df1c2dd4f949413abbf13a6d5c425394e23aa6a09102bc187  10-disable-tests.patch"
