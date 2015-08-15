# Maintainer: David Manouchehri <david@davidmanouchehri.com>
# Contributor: Felipe Contreras <felipe.contreras@gmail.com>

pkgname=git-remote-hg-git
_gitname=$(printf ${pkgname%%-git})
_gitbranch=master
_gitauthor=fingolfin
pkgver=r199.185852e
pkgrel=1
pkgdesc="Transparent bidirectional bridge between Git and Mercurial for Git"
arch=('i686' 'x86_64')
url="https://github.com/$_gitauthor/$_gitname"
license=('GPL2')
depends=('git' 'mercurial')
optdepends=('hg-git') # Not sure if it actually depends or not
makedepends=('asciidoc')
provides=("$_gitname")
conflicts=("$_gitname")
source=("git://github.com/$_gitauthor/$_gitname.git#branch=$_gitbranch")
sha512sums=('SKIP')

pkgver() {
  cd "$srcdir/$_gitname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/$_gitname"
  make all doc
}

check() {
  cd "$srcdir/$_gitname"
  #make test # Broken
}

package() {
  cd "$srcdir/$_gitname"
  make prefix=/usr DESTDIR="$pkgdir" install install-doc
}
