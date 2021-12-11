# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Your Name <youremail@domain.com>
pkgname=tiny-media-manager-bin
pkgver=4.2.4
pkgrel=1
epoch=
pkgdesc="A multi-OS media management tool"
arch=("any")
url="https://www.tinymediamanager.org/"
license=('Apache')
depends=("libmediainfo" "java-runtime>=11")
makedepends=()
checkdepends=()
optdepends=()
provides=()
conflicts=("tiny-media-manager")
replaces=("tiny-media-manager")
backup=()
options=()
install=
changelog=
source=(
  "${pkgname}-${pkgver}.tar.gz::https://release.tinymediamanager.org/v4/dist/tmm_${pkgver}_linux-amd64.tar.gz"
  "generic.desktop"
)
noextract=("${pkgname}-${pkgver}.tar.gz")
sha256sums=(
  "132f5528acc00beb2c5979dd37cb92c8a523e628deea23e6f69e711efae482dc"
  "443e215a98ded0e4be592ae87e7a89dd07f2ce3aca9dba3cf0a85964617a2b45"
)

package() {
	dstdir="${pkgdir}/usr/share/${pkgname}"
  mkdir -p "$dstdir"
  tar -xvf "${pkgname}-${pkgver}.tar.gz" --directory "$dstdir" --strip-components 1
  
  mv "generic.desktop" "${pkgname}.desktop"
  sed -i "s/VERSION/${pkgver}/" "${pkgname}.desktop"
  sed -i "s/DESCRIPTION/${pkgdesc}/" "${pkgname}.desktop"
  sed -i "s/PKGNAME/${pkgname}/" "${pkgname}.desktop"

  install -D "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  mkdir -p "${pkgdir}/usr/bin"
  ln -s "${dstdir}/tinyMediaManager" "${pkgdir}/usr/bin/${pkgname}"
}
