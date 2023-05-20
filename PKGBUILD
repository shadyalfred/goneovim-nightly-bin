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
         libtiff5
         libx11
         libxcb
         neovim
         nspr
         nss
         qt5-declarative
         qt5-quickcontrols2
         qt5-sensors
         qt5-speech
         qt5-svg
         qt5-tools
         qt5-wayland
         qt5-webengine
         zlib)
provides=("$_pkgname=$pkgver")
conflicts=("$_pkgname")
_archive="goneovim-linux.tar.bz2"
source=("$url/releases/download/nightly/$_archive"
        goneovim-nightly.desktop
        goneovim-nightly.ico)
sha256sums=("7bc2b222e182cfb77c84688e46bc241b525949cfe8da5cdd8c9695ea16cc64c8"
            "7d4b2014d86c5246101c64ac692783c01c95a873392c4a14f0076eb090669b61"
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