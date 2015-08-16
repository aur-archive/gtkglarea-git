# Contributor: Iwan Gabovitch (qubodup) <qubodup@gmail.com>

pkgname=gtkglarea-git
pkgver=20120125
pkgrel=2
pkgdesc="GTK/GL Area libraries, includes gtkgl"
arch=('i686' 'x86_64')
url="http://www.mono-project.com/GtkGLArea"
license=('GPL')
depends=('glut' 'gtk')
makedepends=()
optdepends=()
conflicts=()
provides=(gtkglarea)

_gitroot="git://git.gnome.org/gtkglarea"
_gitname="gtkglarea"

build() {
  cd $srcdir

  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  cd "$srcdir/$_gitname"

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

pwd
  ./autogen.sh
  CFLAGS=-lm ./configure --prefix=/usr
  make || return 1
  make DESTDIR=$pkgdir install
}

