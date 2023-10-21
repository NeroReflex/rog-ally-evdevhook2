# Maintainer: Valeri Ochinski <v19930312@gmail.com>

pkgname=evdevhook2-git
pkgver=1.0.1.r1.g3635e5a
pkgrel=1
pkgdesc="Cemuhook UDP server for devices with modern Linux drivers"
arch=('x86_64')
url="https://github.com/v1993/evdevhook2"
license=('GPL3')
groups=()
depends=('glib2' 'zlib' 'libudev.so' 'libevdev.so' 'libgee-0.8.so')
optdepends=('upower: battery status reporting')
makedepends=('git' 'meson' 'vala')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=(
    'evdevhook2::git+https://github.com/v1993/evdevhook2.git'
    'evdevhook2.service'
    'rog-ally-bmi323.patch'
)
b2sums=(
    'SKIP'
    '7a663f816ba47dba76016cff4f156ac3267c9d35c9a87b4e5443c1e380b100f0f962d58cd57bc972c2d94058a867bef6946f282f97d315c990d49a614a87e87e' # evdevhook2.service
    'efe09cb738f35ac5e36742a06de97e764eb4246fd02c897f19b0cd2317eeac4120093e96bf487785b3b3528fe9aeffd477c7a5d82fa884bd9a8a5cab47ce54a9' # rog-ally-bmi323.patch
)

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	git describe --long --tags --abbrev=7 | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
    cd evdevhook2
    patch -Np1 -i ../rog-ally-bmi323.patch

    cd ..
	meson subprojects download --sourcedir="$srcdir/${pkgname%-git}"
}

build() {
	arch-meson "$srcdir/${pkgname%-git}" build
	meson compile -C build
}

package() {
	meson install -C build --destdir "$pkgdir"

    # systemd
    install -D -m644 evdevhook2.service   -t "${pkgdir}/usr/lib/systemd/user/"

    # LICENSE
    install -D -m644 evdevhook2/LICENSE    -t "${pkgdir}/usr/share/licenses/evdevhook2/"
}
