# Maintainer: Gaetan Bisson <bisson@archlinux.org>

pkgname=cromfs
pkgver=1.5.10.1
pkgrel=1
arch=('i686' 'x86_64')
pkgdesc='Compressed read-only filesystem based on FUSE'
url='http://bisqwit.iki.fi/source/cromfs.html'
license=('GPL')
depends=('fuse' 'lzo2')
source=("http://bisqwit.iki.fi/src/arch/${pkgname}-${pkgver}.tar.gz"
        'make-generic.patch')
sha1sums=('3d591530ea3a6ed9b6b53b3fcccf9c7c021efd13'
          'ae51f1d2446df20bcbaef6ac125b1756177725d4')

build() {
	cd "${srcdir}/${pkgname}-${pkgver}"

	patch -p1 -i ../make-generic.patch

	./configure
	make
}

package() {
	cd "${srcdir}/${pkgname}-${pkgver}"

	make DESTDIR="${pkgdir}" install
	install -d "${pkgdir}"/usr/{bin,share/doc/cromfs}
	install -m755 install/progs/* "${pkgdir}"/usr/bin/
	install -m644 install/docs/* "${pkgdir}"/usr/share/doc/cromfs/
}
