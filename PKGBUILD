# Maintainer: George Brooke <george+arch.aur@george-brooke.co.uk>
pkgname=telepathy-kde-contact-applet-git
pkgver=20130113
pkgrel=1
pkgdesc="Shows the avatar and status of a contact, allowing you to start a call or chat."
arch=('i686' 'x86_64')
url="https://projects.kde.org/projects/extragear/network/telepathy/ktp-contact-applet"
license=('GPL' 'LGPL')
depends=('telepathy-kde-common-internals-git' 'kdebase-workspace')
conflicts=('telepathy-kde-presence-applet-git')
makedepends=('cmake' 'automoc4' 'git')

_gitroot="git://anongit.kde.org/ktp-contact-applet"
_gitname="ktp-contact-applet"

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

  rm -rf ${srcdir}/build && mkdir ${srcdir}/build
  cd ${srcdir}/build

  cmake ../$_gitname \
    -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "$srcdir/build"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
