# Maintainer: Joe User <joe.user@example.com>
pkgname=wlroots0.18-westmere
pkgver=0.18.2
pkgrel=2
pkgdesc="wlroots with westmere patches"
arch=('x86_64')
url="https://swaywm.org/"
license=('MIT')
depends=('libinput' 'libxkbcommon' 'pixman' 'mesa' 'libdrm' 'wayland')
makedepends=('wayland-protocols' 'wayland' 'vulkan-headers' 'xorg-xwayland')
optdepends=('swaync: simple sway notification demon')
source=("https://github.com/AlieeLinux/wlroots0.18-westmere/releases/download/wlr/wlroots-0.18.2.tar.gz")
sha256sums=('cf776c169169f279808d9eabc6583f484338dcd454c966a285ff178c88c105d4')
provides=("wlroots0.18")
replaces=("wlroots0.18")
conflicts=('wlroots0.18')

build() {
        export CFLAGS="-march=westmere -mtune=nehalem -O2 -pipe -fstack-protector-strong -fno-plt -fPIC"
        export CXXFLAGS="${CFLAGS}"
        tar -xvf "wlroots-0.18.2.tar.gz" -C "$srcdir"
        cd "$srcdir/wlroots-0.18.2"
        mkdir build
        arch-meson build --prefix=/usr -Dc_args="$CFLAGS" -Dcpp_args="$CFLAGS" -Dxwayland=disabled
        ninja -C build -j $(nproc)
}
package() {
        cd "$srcdir/wlroots-0.18.2"
        DESTDIR="$pkgdir/" ninja -C build install -j2
}
