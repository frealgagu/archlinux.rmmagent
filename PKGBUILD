# Maintainer: Sean Snell <ssnell at cmhsol dot com>
# Maintainer: Fredy García <frealgagu at gmail dot com>

pkgname=rmmagent
pkgver=2.0.3
pkgrel=1
pkgdesc="Advanced Monitoring Agent"
arch=("x86_64")
url="https://www.solarwindsmsp.com/content/advanced-monitoring-agent"
license=("custom")
depends=(
  "dmidecode"
  "ethtool"
  "openssl-1.0"
  "qt5-declarative"
  "smartmontools"
  "unzip"
)
options=("!strip")
source=(
  "manual://${pkgname}_${pkgver}_amd64.deb"
  "${pkgname}.patch"
)
md5sums=(
  "f49564cc1131471e03ddeb409fb1edb5"
  "af2faec92412d7c77a1ca1bd797fb4fd"
)

prepare() {
  cd "${srcdir}"

  bsdtar -xf data.tar.gz -C "${srcdir}/"

  patch -Np1 -i "${srcdir}/${pkgname}.patch"
}

build() {
  cd "${srcdir}"

  mv "${srcdir}/usr/local/" "${srcdir}/usr/share/"
}

package() {
  cp --no-dereference --preserve=links --recursive --no-preserve=ownership "${srcdir}/"{etc,usr} "${pkgdir}/"
}
