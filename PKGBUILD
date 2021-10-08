pkgname=pcmanfm
pkgver=1.3.2
pkgrel=1
pkgdesc="Extremely fast and lightweight file manager"
arch=(x86_64)
url=https://github.com/m-bartlett/pcmanfm-hide-menubar
upstream=https://github.com/lxde/pcmanfm
license=(GPL)
depends=(libfm-gtk2 lxmenu-data)
makedepends=(git intltool)
optdepends=('gvfs: mount local and remote drives'
            'xarchiver: manage archives')
provides=($pkgname)
conflicts=($pkgname)
source=($pkgname::git+${url}.git)
sha256sums=(SKIP)

# pkgver() {
#   printf "r%s.%s" "$(git ls-remote ${upstream}.git | wc -l)" "$(git ls-remote ${upstream}.git | grep -m1 HEAD | cut -c1-7)"
# }
 
prepare() {
  mkdir -p upstream
  curl -L $upstream/archive/refs/tags/$pkgver.tar.gz | tar xvfz - --strip-components=1 -C upstream
  cp $pkgname/patch upstream/
  cd upstream
  git apply patch
  ./autogen.sh
}

build() {
  cd upstream
  ./configure --prefix=/usr --sysconfdir=/etc
  make
}

package() {
  cd upstream
  make DESTDIR="$pkgdir" install
}
