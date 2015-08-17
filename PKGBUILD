# Maintainer: cfrog <cfrog@hush.com>
pkgname=py3cairo-git
pkgver=20120513
pkgrel=1
pkgdesc="Python bindings for the cairo graphics library."
arch=(any)
url="http://cairographics.org/pycairo/"
license=('LGPL')
groups=()
depends=('python' 'cairo')
makedepends=('git')
provides=(py3cairo)
conflicts=()

_gitroot=git://git.cairographics.org/git/pycairo
_gitname=pycairo

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

}

package() {
  cd "$srcdir/$_gitname-build"
  python setup.py install --root="$pkgdir/" --optimize=1
}

