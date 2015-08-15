# Maintainer: shad0w73 <shad0w73@maills.de>
pkgname=brother-dcpj715w-cups
pkgver=1.1.3
pkgrel=2
license=('GPL2' 'custom:Brother Industries')
pkgdesc="CUPS driver for Brother DCP-J715W printer"
url="http://solutions.brother.com/linux/en_us/index.html"

arch=('i686' 'x86_64')

depends=('a2ps' 'cups')
if test "$CARCH" == "x86_64"; then
  depends+=('lib32-glibc')
else
  depends+=('glibc')
fi

install=brother-dcpj715w.install
source=("http://www.brother.com/pub/bsc/linux/dlf/dcpj715wcupswrapper-1.1.3-1.i386.rpm" \
        "http://www.brother.com/pub/bsc/linux/dlf/dcpj715wlpr-1.1.3-1.i386.rpm" \
        fix_lp.patch)
md5sums=('116b6abd6f347752873ce4597830120e'
         '8e41b6ad92b96e9003237e4f3e7362b3'
         '11618b5102743e3878ef1eebee317513')

build() {
  cd "$srcdir"
	patch -Np0 < fix_lp.patch
}

package() {
	install -d $pkgdir/usr/bin
	install -d $pkgdir/var/spool/lpd
  install -Dm755 "$srcdir"/usr/bin/brprintconf_dcpj715w "$pkgdir"/usr/bin/
	cp -R $srcdir/opt $pkgdir/
}
