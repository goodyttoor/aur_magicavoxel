# Maintainer: Alexis Couronne <alexis@skitoo.net>

# I maintain this on Github, feel free to submit a pull request to
# https://github.com/skitoo/magicavoxel-archlinux

pkgname=magicavoxel
pkgver=0.99.4
pkgrel=2
pkgdesc='A free lightweight 8-bit voxel editor and interactive path tracing renderer, enjoy :)'
arch=('any')
url="http://ephtracy.github.io/"
source=("https://github.com/ephtracy/ephtracy.github.io/releases/download/${pkgver}/MagicaVoxel-${pkgver}.${pkgrel}-alpha-win64.zip"
        "https://github.com/ephtracy/ephtracy.github.io/releases/download/${pkgver}/plugin-win64.zip"
        "http://ephtracy.github.io/favicon.png"
        "magicavoxel"
        "magicavoxel.desktop"
        )
license=("Feel free to use it for any project, no commercial licences required, credits are appreciated")
depends=(wine)
makedepends=(unzip)
noextract=("MagicaVoxel-${pkgver}.${pkgrel}-alpha-win64.zip")
md5sums=('49da7365178fa2ab7c55d9d7c6268395'
         '02e7c206bfd79afa544df799c053ec81'
         '64ba6d1187827aa3ff3577c9ef9419fc'
         'f4c23c8e58253215628e3c0acd14522e'
         'd6c5be935d1588955be51ffbb2c1516b')

build () {
  unzip -o "MagicaVoxel-${pkgver}.${pkgrel}-alpha-win64.zip"
  unzip -o "plugin-win64.zip" -d "${srcdir}/MagicaVoxel-${pkgver}.${pkgrel}-alpha-win64"
}

package () {
  install -dm755 "${pkgdir}/usr/share/magicavoxel"
  cp -ra "${srcdir}/MagicaVoxel-${pkgver}.${pkgrel}-alpha-win64/." "${pkgdir}/usr/share/magicavoxel"
  install -m644 favicon.png "${pkgdir}/usr/share/magicavoxel.png"
  install -dm755 "${pkgdir}/usr/bin"
  install -m755 magicavoxel "${pkgdir}/usr/bin"
  install -dm755 "${pkgdir}/usr/share/applications"
  install -m644 magicavoxel.desktop "${pkgdir}/usr/share/applications/magicavoxel.desktop"
  install -dm755 "${pkgdir}/usr/share/icons/hicolor/256x256/apps"
  install -m644 favicon.png "${pkgdir}/usr/share/icons/hicolor/256x256/apps/magicavoxel.png"
}

post_install() {
  update-desktop-database -q
  xdg-icon-resource forceupdate --theme hicolor &>/dev/null
}
