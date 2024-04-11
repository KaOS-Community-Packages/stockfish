pkgname=stockfish
pkgver=16.1
pkgrel=1
epoch=1
pkgdesc="A strong chess engine written by Tord Romstad, Marco Costalba, Joona Kiiski"
arch=('x86_64')
url="https://stockfishchess.org/"
license=('GPL3')
depends=('glibc')
source=("https://github.com/official-stockfish/Stockfish/archive/sf_$pkgver.zip")
sha512sums=('bfaa5c644d2acb8538b1a2c72fdf58c6b0ba6cbb3a4e1a335391faa1529f1069eca888295bd4eef0e887860185a3e0e18529ab609829738c420a0c810be5cca4')

build() {
    cd "Stockfish-sf_${pkgver}/src"

    if grep avx2 /proc/cpuinfo 2>&1; then
 _arch=x86-64-avx2
    else
 _arch=x86-64
    fi
    
    make profile-build ARCH=$_arch
}

package() {
    cd "Stockfish-sf_${pkgver}/src"
    make PREFIX="$pkgdir/usr" install
}
