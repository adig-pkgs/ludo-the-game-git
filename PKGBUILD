# Maintainer: Aditya Gupta <ag15035 at gmail dot com>
pkgname=ludo-the-game-git
pkgver=v2.3.1.r0.bb8faea
pkgrel=1
pkgdesc="An implementation of the famous board game Ludo, using C++"
arch=('x86_64')
url="https://github.com/adi-g15/Ludo-The_Game"
license=('MIT')
depends=()
makedepends=('git' 'cmake' 'gcc')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=()
md5sums=()

pkgver() {
        cd "$srcdir/${pkgname%-git}"

	printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"
}

prepare() {
	if [[ ! -e "$srcdir/${pkgname%-git}" ]]; then
		git clone https://github.com/adi-g15/Ludo-The_Game "$srcdir/${pkgname%-git}" --depth=1
	else
		printf "$srcdir/${pkgname%-git} already exists ! Pulling latest commits...\n"
		cd "$srcdir/${pkgname%-git}"
		git pull
	fi
}

build() {
	cd "$srcdir/${pkgname%-git}"
        mkdir -p build && cd build
        rm -f CMakeCache.txt
	cmake .. -DCMAKE_BUILD_TYPE=Release
	cmake --build .
}

package() {
	cd "$srcdir/${pkgname%-git}"
        cd build
	DESTDIR="$pkgdir/" cmake --install .
}
