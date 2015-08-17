# Maintainer: Julien Pecqueur (JPEC) <jpec[at]julienpecqueur[dot]net>
pkgname=raspyplayer-git
pkgver=20130312
pkgrel=3
pkgdesc="A simple media player originally designed for the Raspberry Pi."
url="http://raspyplayer.org"
arch=('any')
license=('GPL')
depends=('python' 'tk' 'xterm' 'xdg-utils')
optdepends=('mplayer' 'omxplayer')
makedepends=('git')
conflicts=('raspyplayer')
md5sums=('SKIP')
_gitroot="git://github.com/jpec/RasPyPlayer.git"
_gitname="RasPyPlayer"

build() {
  cd ${srcdir}/
  msg "Connecting to the GIT server...."
  if [[ -d ${srcdir}/${_gitname} ]] ; then
    cd ${_gitname}
    git reset --hard
    git pull origin
    msg "The local files are updated..."
  else
    msg "Cloning git repo..."
    git clone ${_gitroot}
    cd ${_gitname}
  fi
  git reset --hard
  msg "GIT checkout done."
}

package() {
  cd "${srcdir}/${_gitname}"
  # install files
  install -Dm755 RasPyPlayer.py "$pkgdir/usr/local/bin/raspyplayer"
  install -Dm666 raspyplayer.conf "$pkgdir/etc/raspyplayer.conf"
  install -Dm644 raspyplayer.desktop "$pkgdir/usr/share/applications/raspyplayer.desktop"
  install -Dm644 raspyplayer.png "$pkgdir/usr/share/pixmaps/raspyplayer.png"
}

# vim:set ts=2 sw=2 et: