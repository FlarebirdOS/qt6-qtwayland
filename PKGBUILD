pkgname=qt6-qtwayland
pkgver=6.10.0
pkgrel=2
pkgdesc="Provides APIs for Wayland"
arch=('x86_64')
url="https://www.qt.io"
license=(
    'GPL-3.0-only'
    'LGPL-3.0-only'
    'LicenseRef-Qt-Commercial'
    'Qt-GPL-exception-1.0'
)
depends=(
    'gcc-libs'
    'glibc'
    'libglvnd'
    'libxkbcommon'
    'qt6-qtbase'
    'qt6-qtdeclarative'
    'qt6-qtsvg'
    'wayland'
)
makedepends=(
    'cmake'
    'git'
    'ninja'
    'vulkan-headers'
)
source=(git+https://code.qt.io/qt/${pkgname#*-}#tag=v${pkgver})
sha256sums=(fd3dfcedcc7fe901bcfd40358fb536a33100b6164615b9e67e8e04bea9ba35fd)

build() {
    cd ${pkgname#*-}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D INSTALL_LIBDIR=lib64
        -D CMAKE_MESSAGE_LOG_LEVEL=STATUS
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build
}

package() {
    cd ${pkgname#*-}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
