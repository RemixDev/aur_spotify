# Maintainer: Ashley Whetter <(firstname) @ awhetter.co.uk>
# Contributor: Eothred <yngve.levinsen@gmail.com>

pkgname=spotify
pkgver=1.0.16.104
_anotherpkgver=.g3b776c9e
pkgrel=1
pkgdesc="A proprietary music streaming service"
arch=('x86_64' 'i686')
license=('custom:"Copyright (c) 2006-2010 Spotify Ltd"')
url="http://www.spotify.com"
options=('!strip')

source=('spotify'
'spotify.protocol')
md5sums=('3f843269e92d536cefdd2f68df11f248'
'ef25ddc5b6bf8fe1a0d64cbd79e1f7b4')

source_x86_64=("http://repository.spotify.com/pool/non-free/s/spotify-client/spotify-client_${pkgver}${_anotherpkgver}_amd64.deb")
md5sums_x86_64=('573e4438f3979c102f7fc2bb5e30fb0d')

source_i686=("http://repository.spotify.com/pool/non-free/s/spotify-client/spotify-client_${pkgver}${_anotherpkgver}_i386.deb")
md5sums_i686=('229a7afe41fe3b286a049f4380d3a9c6')

depends=("alsa-lib>=1.0.14" "gconf" "gtk2" "glib2" "nss" "libsystemd" "libxtst" "libx11" "libxss" "libcurl-compat")
optdepends=('desktop-file-utils: Adds URI support to compatible desktop environments'
            'ffmpeg-compat: Adds support for playback of local files'
						)

package() {
  cd "${srcdir}"

	tar -xzf data.tar.gz -C "${pkgdir}"

	install -d "${pkgdir}"/usr/share/applications
	install -d "${pkgdir}"/usr/share/pixmaps
	install "${pkgdir}"/usr/share/spotify/spotify.desktop "${pkgdir}"/usr/share/applications/spotify.desktop
	install "${pkgdir}"/usr/share/spotify/icons/spotify-linux-512.png "${pkgdir}"/usr/share/pixmaps/spotify-client.png

	# Bin Script
	rm "${pkgdir}"/usr/bin/spotify
	install -Dm755 "${srcdir}/spotify" "${pkgdir}/usr/bin/spotify"

  # Copy protocol file if KDE is installed
  if [ -f /usr/bin/startkde ]; then
    echo "Installing with KDE support"
    install -Dm644 "${srcdir}/spotify.protocol" "${pkgdir}/usr/share/kde4/services/spotify.protocol"
  fi
}
