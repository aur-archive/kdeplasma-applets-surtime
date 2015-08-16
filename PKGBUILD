# Maintainer: Limao Luo <luolimao+AUR@gmail.com>

pkgname=kdeplasma-applets-surtime
pkgver=1.0.0
_srcname=plasma-SurTime_$pkgver
pkgrel=4
pkgdesc="A collection of analog and digital clocks"
arch=(i686 x86_64)
url=http://kde-apps.org/content/show.php/SurTime?content=153555
license=(LGPL3)
depends=(kdebase-workspace)
makedepends=(cmake automoc4)
install=$pkgname.install
source=(http://kde-apps.org/CONTENT/content-files/153555-$_srcname.tar.gz)
sha256sums=('134d9c8b70b46e849c723599bee034222a1ffdbd336d070640fa601882a906fa')
sha512sums=('fdce6339c90b2f17b09af562062da6fed0cab713606aa1f15028bbf9377aba7d4362039f01b646fb211c9fbfba0e34c43675c36ba66791931975b662a89d2906')

prepare() {
    sed -i 's:/share/icons/:&hicolor/:g' $_srcname/CMakeLists.txt
}

build() {
    install -d $pkgname-build/
    cd $pkgname-build/
    cmake ../$_srcname/ \
        -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) \
        -DCMAKE_BUILD_TYPE=Release \
        -DQT_QMAKE_EXECUTABLE=qmake-qt4
    make
}

package() {
    make -C $pkgname-build DESTDIR="$pkgdir" install
}
