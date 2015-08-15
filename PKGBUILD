# Maintainer: Takuro Onoue <kusanaginoturugi@gmail.com>

pkgname=firefox-aurora-bin-ja
_mypkgn=firefox-aurora
pkgdesc='Standalone web browser from mozilla.org (Japanese version from Aurora channel)'
url='http://www.mozilla.com/firefox/channel/'
pkgver=34.0a2
pkgrel=1
makedepends=('curl')
arch=('i686' 'x86_64')
license=('MPL' 'GPL' 'LGPL')
depends=('gtk2' 'libxt' 'startup-notification' 'mime-types' 'dbus-glib' 
	 'alsa-lib' 'dbus-glib' 'libnotify' 'desktop-file-utils' 'hicolor-icon-theme'
	 'libvpx' 'libevent' 'nss>=3.14.1' 'hunspell')
options=(!emptydirs)
install=firefox.install

_ffsrc="firefox-${pkgver}.ja.linux-${CARCH}.tar.bz2"
_ffsums="firefox-${pkgver}.ja.linux-${CARCH}.checksums"
_ffsrc_url="http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-aurora-l10n/${_ffsrc}"
_ffsums_url="http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-aurora-l10n/${_ffsums}"
_ffsha512=`curl -# $_ffsums_url | head -1 | cut -d " " -f 1`

source=(.AURINFO 'firefox-aurora.desktop' 'firefox-aurora-safe.desktop' $_ffsrc_url)
sha512sums=(SKIP
            '0597c08fec67e1755e8bfee89e82e5f44ce53ccab9529111a1ee7ccabb62cd078b97059874a867c976437b73af7a0afa7fc291146deb8ad41f5e424c91abce03'
            '749bc9bb180909c7319a1576e9df1e4cb06488b33b8dd61b8f1a63e4df9208cb9bb6d0c4ecef3fbe388f78368aef4562ae1dbfda1dbbfa649aa9d247c4903610'       
            $_ffsha512)
package() {

  mkdir -p ${pkgdir}/usr/{lib,bin,share/{applications,pixmaps}}

  cp -r firefox "${pkgdir}/usr/lib/${_mypkgn}"
  
  ln -s /usr/lib/${_mypkgn}/firefox ${pkgdir}/usr/bin/firefox-aurora
  install -m644 {firefox-aurora.desktop,firefox-aurora-safe.desktop} ${pkgdir}/usr/share/applications/
  install -m644 firefox/browser/icons/mozicon128.png ${pkgdir}/usr/share/pixmaps/${_mypkgn}-icon.png
}
