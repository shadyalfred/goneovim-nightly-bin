# Maintainer: Shady Alfred <shadyalfred98@gmail.com>

pkgname="goneovim-nightly-bin"
_pkgname="${pkgname%-bin}"
commit="599cae7"
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
DLAGENTS=("https::/usr/bin/curl -L \
                -H 'Accept: application/octet-stream' \
                -H 'X-GitHub-Api-Version: 2022-11-28' \
                https://api.github.com/repos/akiyosi/goneovim/releases/assets/109357358 \
                --output $_archive")
source=($_archive
        goneovim-nightly.desktop
        goneovim-nightly.ico)
sha256sums=("17de5afe2885d91fc09cd6155d0a8e9ffdcb4412a8c7d6389e3e1853701d26fb"
            "7d4b2014d86c5246101c64ac692783c01c95a873392c4a14f0076eb090669b61"
            "0a36211b6ada93d811575b5ca9b33511e405f61cca791858ea2fe1eb5d29279e")

package() {
	install -Dm0644 -t "$pkgdir/usr/share/pixmaps/" goneovim-nightly.ico
	install -Dm0644 -t "$pkgdir/usr/share/applications/" goneovim-nightly.desktop

	cd "$_archive"

         mv ./goneovim "./$_pkgname"

	install -Dm0755 -t "$pkgdir/usr/bin/" "$_pkgname"
	install -Dm0644 -t "$pkgdir/$XDG_DATA_HOME/nvim/site/doc/" "runtime/doc/goneovim.txt"
}
