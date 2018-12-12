pkgname=stockfish
pkgver=10
pkgrel=1
epoch=1
pkgdesc="A strong chess engine written by Tord Romstad, Marco Costalba, Joona Kiiski"
arch=('x86_64')
url="https://stockfishchess.org/"
license=('GPL3')
depends=('glibc')
source=("https://${pkgname}.s3.amazonaws.com/${pkgname}-${pkgver}-src.zip")
sha512sums=('959c4f3c497ba3108884dabc38de824f11781ae57b4ab5fdf25daf9a7fc0326e663adb1c081b8c8d57a7bf5f2e941369502a50a0c93135a001c6bd1af360d0f8')

build() {
    cd "$srcdir/src"

    if grep popcnt /proc/cpuinfo 2>&1; then
 _arch=x86-64-modern
    else
 _arch=x86-64
    fi
    
    make profile-build ARCH=$_arch
}

package() {
    cd "$srcdir/src"
    make PREFIX="$pkgdir/usr" install
}
