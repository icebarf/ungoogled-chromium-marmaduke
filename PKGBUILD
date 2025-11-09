# Maintainer: Amritpal Singh ice@rdseed.in
pkgname=ungoogled-chromium
pkgver=142.0.7444.142
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
source=("${url}/releases/download/v142.7444.142-M${pkgver}-r1522585-portable-ungoogled-Lin64/ungoogled-chromium_${pkgver}_${pkgrel}.vaapi_linux.tar.xz"
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

sha256sums=('633b2b365c87942b76523dc245880239dbf59fe25caf434dfbd33bb0b609c807'
            '2370165d823318defa048034eb82ed82744324821c53ccc11566e3b99111d617'
            '633fc5126baaff736f0691eb2ad98d11e348d6ca267b5b0f65f1005e44cdea5f'
            '104bbd067c2ff7583d93b1302bc6663c5af3bb2aa4f37e681a14d8ff93ee93fe')
