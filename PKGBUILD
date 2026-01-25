# Maintainer: Amritpal Singh ice@rdseed.in
pkgname=ungoogled-chromium
pkgver=144.0.7559.103
pkgrel=1
pkgdesc="Ungoogled Chromium build by Marmaduke"
arch=('x86_64')
url="https://github.com/macchrome/linchrome"
license=('Unspecified')
depends=(
  'gtk3' 'nss' 'alsa-lib' 'xdg-utils' 'libxss' 'libcups' 'libgcrypt'
  'ttf-liberation' 'systemd' 'dbus' 'libpulse' 'pciutils' 'libva'
  'libffi' 'desktop-file-utils' 'hicolor-icon-theme')
optdepends=(
  'pipewire: WebRTC desktop sharing under Wayland'
  'kdialog: support for native dialogs in Plasma'
  'gtk4: for --gtk-version=4 (GTK4 IME might work better on Wayland)'
  'org.freedesktop.secrets: password storage backend on GNOME / Xfce'
  'kwallet: support for storing passwords in KWallet on Plasma')
provides=("chromium=$pkgver" "chromedriver=$pkgver")
conflicts=('chromium' 'chromedriver')
source=("${url}/releases/download/v144.7559.103-M${pkgver}-r1552494-portable-ungoogled-Lin64/ungoogled-chromium_${pkgver}_${pkgrel}.vaapi_linux.tar.xz"
    "icons.tar.xz"
    "chromium"
    "chromium.desktop"
        )
package() {
  # Note that `-L` option in cp is necessary to dereference symlinks
  mkdir --parents "${pkgdir}/usr/bin"
  chmod +x "${srcdir}/chromium"
  cp -rL "${srcdir}/chromium" "${pkgdir}/usr/bin"

  # we install the .desktop file
  mkdir --parents "${pkgdir}/usr/share/applications"
  cp -rL "${srcdir}/chromium.desktop" "${pkgdir}/usr/share/applications/"

  # copy the icons
  cp -r "${srcdir}/icons" "${pkgdir}/usr/share"

  # then we finally install chromium itself
  mkdir --parents "${pkgdir}/opt"
  cp -r "${srcdir}/${pkgname}_${pkgver}_${pkgrel}.vaapi_linux" "${pkgdir}/opt/${pkgname}"

}

sha256sums=('30aa08f76f4160daed14d766316a7e378d9cfed5ec124a11d968c1f2dc64b166'
            '2370165d823318defa048034eb82ed82744324821c53ccc11566e3b99111d617'
            '7d3b97198fa227f5ba497b1128aef008c41a6d0264fd3548f0e86a4a2d63fc3b'
            '104bbd067c2ff7583d93b1302bc6663c5af3bb2aa4f37e681a14d8ff93ee93fe')
