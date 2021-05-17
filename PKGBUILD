# Maintainer: Aun-Ali Zaidi <admin@kodeit.net>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgbase=linux-mbp
pkgver=5.11.20
_srcname=linux-${pkgver}
pkgrel=1
pkgdesc='Linux for MBP'
_srctag=v${pkgver%.*}-${pkgver##*.}
url="https://git.archlinux.org/linux.git/log/?h=v$_srctag"
arch=(x86_64)
license=(GPL2)
makedepends=(
  bc kmod libelf pahole cpio perl tar xz
  xmlto python-sphinx python-sphinx_rtd_theme graphviz imagemagick
  git
)
options=('!strip')

source=(
  https://www.kernel.org/pub/linux/kernel/v${pkgver//.*}.x/linux-${pkgver}.tar.xz
  https://www.kernel.org/pub/linux/kernel/v${pkgver//.*}.x/linux-${pkgver}.tar.sign
  config         # the main kernel config file

  # Arch Linux patches
  0001-ZEN-Add-sysctl-and-CONFIG-to-disallow-unprivileged-C.patch
  0002-drm-i915-ilk-glk-Fix-link-training-on-links-with-LTT.patch
  0003-drm-i915-dp-Prevent-setting-the-LTTPR-LT-mode-if-no-.patch
  0004-drm-i915-Disable-LTTPR-support-when-the-DPCD-rev-1.4.patch
  0005-drm-i915-Fix-modesetting-in-case-of-unexpected-AUX-t.patch

  # Hack for AMD DC eDP link rate bug
  2001-drm-amd-display-Force-link_rate-as-LINK_RATE_RBR2-fo.patch

  # Apple SMC ACPI support
  3001-applesmc-convert-static-structures-to-drvdata.patch
  3002-applesmc-make-io-port-base-addr-dynamic.patch
  3003-applesmc-switch-to-acpi_device-from-platform.patch
  3004-applesmc-key-interface-wrappers.patch
  3005-applesmc-basic-mmio-interface-implementation.patch
  3006-applesmc-fan-support-on-T2-Macs.patch

  # T2 USB Keyboard/Touchpad support
  4001-HID-apple-Add-support-for-keyboard-backlight-on-supp.patch
  4002-HID-apple-Add-support-for-MacbookAir8-1-keyboard-tra.patch
  4003-HID-apple-Add-support-for-MacBookPro15-2-keyboard-tr.patch
  4004-HID-apple-Add-support-for-MacBookPro15-1-keyboard-tr.patch
  4005-HID-apple-Add-support-for-MacBookPro15-4-keyboard-tr.patch
  4006-HID-apple-Add-support-for-MacBookPro16-2-keyboard-tr.patch
  4007-HID-apple-Add-support-for-MacBookPro16-3-keyboard-tr.patch
  4008-HID-apple-Add-support-for-MacBookAir9-1-keyboard-tra.patch
  4009-HID-apple-Add-support-for-MacBookPro16-1-keyboard-tr.patch

  # Broadcom Wifi rambase debugging additions
  5001-brcmfmac-move-brcmf_mp_device-into-its-own-header.patch
  5002-brcmfmac-Add-ability-to-manually-specify-FW-rambase-.patch

  # MBP Peripheral support
  6001-media-uvcvideo-Add-support-for-Apple-T2-attached-iSi.patch	# UVC Camera support

  # Hack for i915 overscan issues
  7001-drm-i915-fbdev-Discard-BIOS-framebuffers-exceeding-h.patch

  # Broadcom WIFI/BT device support
  8001-brcmfmac-Add-initial-support-for-the-BRCM4355.patch
  8002-brcmfmac-Add-initial-support-for-the-BRCM4377.patch
)

validpgpkeys=(
  'ABAF11C65A2970B130ABE3C479BE3E4300411886'  # Linus Torvalds
  '647F28654894E3BD457199BE38DBBDC86092693E'  # Greg Kroah-Hartman
)

sha256sums=('73faeea560dc4fe1f9ee17af4b8d72446192e536979460d66ed6d0cd03bf0797'
            'SKIP'
            '849ea169bb72e53a2bfdcafe21b58b12534e998539cbcd15722ffc151c6810f7'
            '38dc7a61065fbed8c1e7866e40c80ff3a318bafe606152de4cde3fe141af152a'
            '78a4c70d84340d1a0f335980eb8ec11914f4be548e4c509f07b957a76c57a593'
            '89104a4f7ecbd82ddd7ccaf847fc78848af327187f22054d4f5066aff8641104'
            '89fd1c26eb26930771bd8edaf1ef83a50f0b69f8bf8705962bfdc2160b173f77'
            'ff65f4e0f8132166d64695dde2979e437d4887b212688b56be07b9a47b3b046e'
            '786dfc22e4c6ece883e7dedd0ba3f6c14018584df95450b2cb78f3da8b01f7cb'
            '4cd7002a6f5c40c5abacbb60221015f73b7b219a9adb133e003877f1d35ec81d'
            '8d8401a99a9dfbc41aa2dc5b6a409a19860b1b918465e19de4a4ff18de075ea3'
            '08d165106fe35b68a7b48f216566951a5db0baac19098c015bcc81c5fcba678d'
            '459906cab172df9f6712a4168e7a5d529f85b2bb58a068f2d44746df14a6d27a'
            '2827dab6eeb2d2a08034938024f902846b5813e967a0ea253dc1ea88315da383'
            '62b7d5831960c5775cdea17d44011cfda790f78d833e9663cf522350ab3643b6'
            '11565cff9c6a7db8846dc7d5930419045e9527863b8df5979a7465006211bd16'
            '83f4be6849ba4d5f9fad647ad2eb78bf6409ee98a40ac62e8a5b80496233d70a'
            '44bd3643b2b22fedc59d79511199f30ce6759fa0acdd9a66262a53c5e046da6b'
            'eb04a492197783643b3e72b1d0cf0e856290381997bd165a14fbc63ac1489c25'
            '69d56d42473526f7dbd4fb18c5e1baafe4e6d32995b2506bd48ff981c53b5385'
            '1deeacae1875cf9075b858a8bfb2463ebc531c9030b7c2ab46bbb8e4c3b974db'
            '40eff5e88bb30c51c6b97e85c2e7b8dec5f97916f768e6c07618d9c5afe68574'
            'cac035fe07663a319185c644c5b39b34bef89ada348881fa4a02d15290260445'
            '45719489a9297d863ea60464e45a7e92f19606e527a7219d3582022e38439c0e'
            '4d22727c1456e268de1c39ac73f2dc0c1630ac25aa66364d99f94e29eba5c6b9'
            '7f41e52285bbdeeaf565e7a1e69860439a4cc302092b473301040f29fc2f5b64'
            '9640178d6251686c980c30fc528b3d70beac6ce8246bf433506a3f843808326c'
            '90a6012cdd8a64ede8e0bbaf7331960bd68f628e0973b65459188eb1ccb5b829'
            '3a7baa28d5f45bdbff23e838133f2e3c6896412ffb5a919b4992a7b2d17469d9'
            'edb804461e3820ef3397e1e236f7caabf906b6a13d03f406c8462ec476ecbbe5')

export KBUILD_BUILD_HOST=archlinux
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

prepare() {
  cd $_srcname

  echo "Setting version..."
  scripts/setlocalversion --save-scmversion
  echo "-$pkgrel" > localversion.10-pkgrel
  echo "${pkgbase#linux}" > localversion.20-pkgname

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    [[ $src = *.patch ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  echo "Setting config..."
  cp ../config .config
  make olddefconfig

  make -s kernelrelease > version
  echo "Prepared $pkgbase version $(<version)"
}

build() {
  cd $_srcname
  make all
  make htmldocs
}

_package() {
  pkgdesc="The $pkgdesc kernel and modules"
  depends=(coreutils kmod initramfs)
  optdepends=('crda: to set the correct wireless channels of your country'
              'linux-firmware: firmware images needed for some devices')
  provides=(VIRTUALBOX-GUEST-MODULES WIREGUARD-MODULE)
  replaces=(virtualbox-guest-modules-arch wireguard-arch)
  provides=("linux=$pkgver")

  cd $_srcname
  local kernver="$(<version)"
  local modulesdir="$pkgdir/usr/lib/modules/$kernver"

  echo "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"

  echo "Installing modules..."
  make INSTALL_MOD_PATH="$pkgdir/usr" INSTALL_MOD_STRIP=1 modules_install

  # remove build and source links
  rm "$modulesdir"/{source,build}
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the $pkgdesc kernel"
  provides=("linux-headers=$pkgver")

  cd $_srcname
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # add xfs and shmem for aufs building
  mkdir -p "$builddir"/{fs/xfs,mm}

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/x86" -a arch/x86/include
  install -Dt "$builddir/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

  install -Dt "$builddir/drivers/md" -m644 drivers/md/*.h
  install -Dt "$builddir/net/mac80211" -m644 net/mac80211/*.h

  # http://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # http://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  echo "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  echo "Removing documentation..."
  rm -r "$builddir/Documentation"

  echo "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local file
  while read -rd '' file; do
    case "$(file -bi "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip -v $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v $STRIP_SHARED "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v $STRIP_STATIC "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"
}

_package-docs() {
  pkgdesc="Documentation for the $pkgdesc kernel"

  cd $_srcname
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing documentation..."
  local src dst
  while read -rd '' src; do
    dst="${src#Documentation/}"
    dst="$builddir/Documentation/${dst#output/}"
    install -Dm644 "$src" "$dst"
  done < <(find Documentation -name '.*' -prune -o ! -type d -print0)

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/share/doc"
  ln -sr "$builddir/Documentation" "$pkgdir/usr/share/doc/$pkgbase"
}

pkgname=("$pkgbase" "$pkgbase-headers" "$pkgbase-docs")
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
