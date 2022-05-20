# Maintainer: Antonio Rojas <arojas@archlinux.org> 
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=dragon-git
pkgver=22.04.1
pkgrel=1
pkgdesc='A multimedia player where the focus is on simplicity, instead of features'
arch=(x86_64)
url='https://apps.kde.org/dragonplayer/'
license=(GPL)
depends=(hicolor-icon-theme kparts-git phonon-qt5-git)
makedepends=(extra-cmake-modules-git kdoctools-git)
groups=(kde-applications-git kde-multimedia-git)
source=(git+https://invent.kde.org/multimedia/dragon.git)
sha256sums=('SKIP')
#validpgpkeys=(CA262C6C83DE4D2FB28A332A3A6A4DB839EAA6D7  # Albert Astals Cid <aacid@kde.org>
#              F23275E4BF10AFC1DF6914A6DBD2CE893E2D1C87  # Christoph Feck <cfeck@kde.org>
#              D81C0CB38EB725EF6691C385BB463350D6EF31EF) # Heiko Becker <heiko.becker@kde.org>
#options=(debug)

#pkgver() {
#  cd ${pkgname%-git}
#  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
#}

pkgver() {
  cd ${srcdir}/${pkgname%-git}
  _ver="$(cat CMakeLists.txt | grep RELEASE_SERVICE_VERSION | cut -d '"' -f2 | tr '\n' '.' | cut -d "." -f 1-3)"
  echo "$(echo ${_ver}).r$(git rev-list --count HEAD)"
}

build() { 
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

