# Maintainer: prurigro
# Ported from Kreed's inadyn-fork PKGBUILD and associated files

pkgname=inadyn-fork-git
pkgver=20130306
pkgrel=1
pkgdesc="Simple dynamic DNS client - fork of the original INADYN implementation from Narcis Ilisei"
url='http://github.com/troglobit/inadyn'
arch=('i686' 'x86_64')
license=('GPL')
conflicts=('inadyn-opendns' 'inadyn' 'inadyn-fork')
provides=('inadyn')
backup=(etc/inadyn.conf)

source=(inadyn.conf
        inadyn.service)
sha256sums=('9196481a3c6875a0ead3a318608877ef49402c968f162f13a2f92d6882008c41'
            '4587f4ae2a4215f9ba67d5b3b7d0aa120a9ebd31677472fa68d8792f42d7135f')

build() {
    pushd "$srcdir"
        git clone https://github.com/troglobit/inadyn.git
        pushd inadyn
            make
        popd
    popd
}

package() {
    pushd "$srcdir"/inadyn
        make prefix=/usr DESTDIR="$pkgdir" install
        install -Dm644 ../inadyn.conf "$pkgdir"/etc/inadyn.conf
        install -Dm644 ../inadyn.service "$pkgdir"/usr/lib/systemd/system/inadyn.service
    popd
}
