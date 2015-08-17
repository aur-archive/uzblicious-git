# Maintainer: magnific0
pkgname=uzblicious-git
pkgver=20130214
pkgrel=1
pkgdesc="delicious bookmarking and more for uzbl"
arch=('x86_64' 'i686')
url="https://github.com/magnific0/uzblicious.git"
license=('GPL2')
depends=('dmenu' 'curl' 'uzbl-core')
_gitroot="git://github.com/magnific0/uzblicious.git"
_gitname="uzblicious"

build() {
  cd "$srcdir"

  msg "Connecting to the git repository..."
  if [ -d "$srcdir/$_gitname" ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  cd "$srcdir"
  rm -rf $_gitname-build
  git clone $_gitname $_gitname-build
  cd $_gitname-build
 
  make
  
}

package() {
  cd $_gitname-build

  install -Dm644 uzblicious.conf.example "$pkgdir/usr/share/uzbl/examples/config/uzblicious.conf.example"
  install -Dm755 uzblicious "$pkgdir/usr/bin/uzblicious"

  echo "Don't forget to configure uzbl to use uzblicious. See README.md on $url for more information."
   
}

# vim:set ts=2 sw=2 et:
