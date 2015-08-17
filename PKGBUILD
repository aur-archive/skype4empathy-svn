# Maintainer: mirandir <mirandir@orange.fr>

pkgname=skype4empathy-svn
pkgver=664
pkgrel=1
pkgdesc="Skype plugin for Empathy (svn version). The official Skype client must be running. This plugin uses the skype4pidgin plugin with libpurple and telepathy-haze."
arch=("i686" "x86_64")
url=("http://skype4pidgin.googlecode.com/svn/trunk")
license=('GPL')
depends=('skype' 'libpurple' 'telepathy-haze')
makedepends=('subversion')
optdepends=(
	'empathy: IM client for Gnome'
	'kde-telepathy: IM client for KDE'
	)
conflicts=('skype4pidgin' 'skype4pidgin-svn' 'skype4empathy')
replaces=('skype4pidgin' 'skype4pidgin-svn' 'skype4empathy')
source=('http://mirandir.pagesperso-orange.fr/files/skype_icons.tar.xz'
        skype4empathy::svn+http://skype4pidgin.googlecode.com/svn/trunk)
md5sums=('5728aa01ac674fca2c01348719fe8672'
         'SKIP')

pkgver() {
  cd "${srcdir}"/skype4empathy
  svnversion | tr -d [A-z]
}

build() {

cd "${srcdir}"/skype4empathy

  make all || return 1

}

package() {
  cd ${srcdir}
  
  install -d $pkgdir/usr/share/empathy/icons
  
  cd $pkgdir/usr/share/empathy/
  cp -r ${srcdir}/hicolor/ icons/
  
  cd "${srcdir}"/skype4empathy

  install -D -m 0755 libskype_dbus.so "${pkgdir}$(pkg-config --variable=plugindir purple)/libskype_dbus.so"

}
