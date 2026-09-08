# Maintainer: Amritpal Singh ice@rdseed.in
pkgname=ungoogled-chromium-marmaduke
pkgver=150.0.7871.252
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
source=("${url}/releases/download/v150.7871.252-M${pkgver}-r1639810-portable-ungoogled-Lin64/ungoogled-chromium_${pkgver}_${pkgrel}.vaapi_linux.tar.xz"
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
  cp -r "${srcdir}/chromium_${pkgver}_${pkgrel}.vaapi_linux" "${pkgdir}/opt/${pkgname}"

}

sha256sums=('486ad7442665b0bebe41067ba3bb8e4a16782bb47a97eabb994229f91663a611'
            '2370165d823318defa048034eb82ed82744324821c53ccc11566e3b99111d617'
            '0934981233cd2a1831343dd8607075a51a5001bdeb2bbd6f4fc7ea453507121c'
            'bc924f38bfd679ec4aba047d5115128d217dba145d4cbfa1d3e78f50f5e3848d')
