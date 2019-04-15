# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Stijn Segers <francesco dot borromini at gmail dot com>

pkgname=freerdp-with-shadow-server
epoch=1
pkgver=2.0.0_rc4
_pkgver=${pkgver/_/-}
_pkgver=${_pkgver/+/-}
pkgrel=1
pkgdesc="Free RDP client"
arch=('x86_64')
url="http://freerdp.sourceforge.net"
license=('GPL')
depends=('openssl' 'libxcursor' 'libcups' 'alsa-lib' 'libxext' 'libxdamage'
	 'ffmpeg' 'libxkbfile' 'libxinerama' 'libxv' 'libpulse' 'libxkbfile'
	 'libxrender' 'libxfixes' 'gst-plugins-base-libs' 'dbus-glib'
         'libxkbcommon')
makedepends=('krb5' 'cmake' 'damageproto' 'fixesproto' 'renderproto'
	     'xmlto' 'docbook-xsl' 'git')
provides=('libwinpr-tools2.so' 'libfreerdp-client2.so' 'libfreerdp2.so'
          'libwinpr2.so' 'libfreerdp-server2.so' 'libfreerdp-shadow2.so'
          'libfreerdp-shadow-subsystem2.so')
source=($pkgname-$pkgver.tar.gz::https://github.com/FreeRDP/FreeRDP/archive/${pkgver/_/-}.tar.gz)
sha256sums=('3406f3bfab63f81c1533029a5bf73949ff60f22f6e155c5a08005b8b8afe6d49')
provides=(freerdp)
conflicts=(freerdp)

build() {
  cd "$srcdir"/FreeRDP-${_pkgver}
  cmake \
	-DCMAKE_INSTALL_PREFIX=/usr \
	-DCMAKE_INSTALL_LIBDIR=lib \
	-DWITH_PULSE=ON \
	-DWITH_CUPS=ON \
	-DWITH_CHANNELS=ON \
	-DWITH_CLIENT_CHANNELS=ON \
	-DWITH_SERVER_CHANNELS=ON \
	-DWITH_WAYLAND=ON \
	-DCHANNEL_URBDRC_CLIENT=ON \
	-DWITH_SERVER=ON \
	.
  make
}

package() {
  cd "$srcdir"/FreeRDP-${_pkgver}
  make DESTDIR="${pkgdir}" install
}
