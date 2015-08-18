pkgname=yong
pkgver=2.3.0
pkgrel=3
_realver="$pkgver"
pkgdesc="A Chinese input method."
arch=("i686" "x86_64")
url="http://yong.dgod.net/"
license=("freeware")
source=("http://yoooo-blog.qiniudn.com/yong-lin-${pkgver}-${pkgrel}.7z")
makedepends=("p7zip")
sha1sums=('ff2f5226d5a322f5770c15373b4c89fcd596628c')
 
build() {
    cd $srcdir/$pkgname
    [[ "$CARCH" = "x86_64" ]] && mv l64/* .
    rm -rf l64
    mv yong.chm README.txt doc
}
 
package() {
    mkdir -p $pkgdir/usr/bin/
    mkdir -p $pkgdir/usr/lib/gtk-2.0/2.10.0/immodules/
    mkdir -p $pkgdir/usr/lib/gtk-3.0/3.0.0/immodules/
    mv $srcdir/yong $pkgdir/usr/lib
    cd $pkgdir/usr/bin/
    ln -sf ../lib/yong/yong .
    ln -sf ../lib/yong/yong-config .
    ln -sf ../lib/yong/yong-vim .
    cd $pkgdir/usr/lib
    ln -sf yong/libl.so .
    mv yong/gtk-im/im-yong-gtk2.so $pkgdir/usr/lib/gtk-2.0/2.10.0/immodules/
    mv yong/gtk-im/im-yong-gtk3.so $pkgdir/usr/lib/gtk-3.0/3.0.0/immodules/
    rmdir yong/gtk-im/
     
    IBUS_D=/usr/share/ibus/component
    if [ -d $IBUS_D ]; then
        install -d $pkgdir$IBUS_D
        sed -i "s%\/usr\/share\/yong%\/usr\/lib\/yong%" $pkgdir/usr/lib/yong/yong.xml
        cp $pkgdir/usr/lib/yong/yong.xml $pkgdir$IBUS_D/yong.xml
    fi
}
 
# vim:set ts=4 sw=4 et:
