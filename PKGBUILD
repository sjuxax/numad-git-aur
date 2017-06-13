# Maintainer: Paul Dunn <pwjdunn AT gmail DOT com>

pkgname=numad-git
_pkgname=numad
pkgver=r20.abd1802
pkgrel=1
pkgdesc="numad is a deamon that monitors NUMA topology and usage and distributes loads for good locality for the purpose of providing the best performance, by avoiding unnecessary latency."
arch=('x86_64' 'i686')
license=('LGPL')
url="https://pagure.io/numad.git"
options=()
depends=('libsystemd')
makedepends=('cmake' 'git')
source=("git+https://pagure.io/numad.git")
md5sums=('SKIP')

build() {
	cd "${srcdir}/${_pkgname}"
	make
}

pkgver() {
	cd "${srcdir}/${_pkgname}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	install -Dm755 $srcdir/numad/numad "$pkgdir/usr/bin/numad"
	install -Dm644 $srcdir/numad/numad.8 $pkgdir/usr/share/man/man8
	install -Dm644 $srcdir/numad/numad.service $pkgdir/usr/lib/systemd/system/numad.service
}
