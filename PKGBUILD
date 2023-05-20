# Maintainer: Shady Alfred <shadyalfred98@gmail.com>

pkgname="goneovim-nightly-bin"
_pkgname="${pkgname%-bin}"
commit="c326565"
pkgver="$commit"
pkgrel=1
pkgdesc="Neovim GUI written in Golang, using a Golang qt backend (Nightly)"
arch=(x86_64)
url="https://github.com/akiyosi/goneovim"
license=(MIT)
depends=(expat
         fontconfig
         freetype2
         gcc-libs
         glibc
         gtk3
         libglvnd
         libspeechd
         libtiff5
         libx11
         libxcb
         neovim
         nspr
         nss
         postgresql-libs
         qt5-declarative
         qt5-quickcontrols2
         qt5-sensors
         qt5-speech
         qt5-svg
         qt5-tools
         qt5-wayland
         qt5-webengine
         qt5-websockets
         zlib)
provides=("$_pkgname=$pkgver")
conflicts=("$_pkgname")
_archive="goneovim-linux.tar.bz2"
source=("$url/releases/download/nightly/$_archive"
        goneovim.desktop
        goneovim.ico)
sha256sums=("7bc2b222e182cfb77c84688e46bc241b525949cfe8da5cdd8c9695ea16cc64c8"
            "bb7dd036f10fe1e9132d2bbbf346e99234425b012fadf177bb212c472ac5fca0"
            "0a36211b6ada93d811575b5ca9b33511e405f61cca791858ea2fe1eb5d29279e")

package() {
	install -Dm0644 -t "$pkgdir/usr/share/pixmaps/" goneovim-nightly.ico
	install -Dm0644 -t "$pkgdir/usr/share/applications/" goneovim-nightly.desktop
	cd "$_archive"

         mv ./goneovim "./$_pkgname"
         mv ./runtime/doc/goneovim.txt "./runtime/doc/$_pkgname.txt"

	install -Dm0755 -t "$pkgdir/usr/bin/" "$_pkgname"
	install -Dm0644 -t "$pkgdir/usr/share/nvim/runtime/doc/" "runtime/doc/$_pkgname.txt"
}
