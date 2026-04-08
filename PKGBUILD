# Maintainer: Andy Alt <arch_stanton5995 at proton.me>
# Contributor: Oliver Jaksch <arch-aur at com-in dot de>

pkgname=rmw
pkgver=0.9.5
pkgrel=1
pkgdesc="trash/recycle bin utility for the command line"
arch=('x86_64')
url="https://theimpossibleastronaut.com/rmw-website/"
license=('GPL-3.0-or-later')
depends=(
  'glibc'
  'ncurses'
)
optdepends=('canfigger: use system-installed version')
makedepends=(
  'meson'
  'ninja'
)

source=("https://github.com/theimpossibleastronaut/rmw/releases/download/v${pkgver}/${pkgname}-${pkgver}.tar.xz")
sha256sums=('5fa336da39228d4ef6d1314fd86b5dfb0622e80485ebf7b78152198278090050')

build() {
  arch-meson $pkgname-$pkgver build -Db_sanitize=none
  meson compile -C build
}

package() {
  DESTDIR="$pkgdir" meson install -C build
  install -Dm 644 "${pkgname}-${pkgver}/COPYING" -t "${pkgdir}/usr/share/licenses/${pkgname}"
  rm -f "${pkgdir}/usr/share/doc/${pkgname}/COPYING"
}
