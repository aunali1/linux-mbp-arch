# Maintainer: Aun-Ali Zaidi <admin@kodeit.net>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgbase=linux-mbp
pkgver=5.4.10
_srcname=linux-${pkgver}
pkgrel=2
pkgdesc='Linux for MBP'
_srctag=v${pkgver%.*}-${pkgver##*.}
url="https://git.archlinux.org/linux.git/log/?h=v$_srctag"
arch=(x86_64)
license=(GPL2)
makedepends=(
  bc kmod libelf
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
  0002-lib-devres-add-a-helper-function-for-ioremap_uc.patch
  0003-mfd-intel-lpss-Use-devm_ioremap_uc-for-MMIO.patch
  0004-PCI-pciehp-Do-not-disable-interrupt-twice-on-suspend.patch
  0005-PCI-pciehp-Prevent-deadlock-on-disconnect.patch
  0006-ACPI-PM-s2idle-Rework-ACPI-events-synchronization.patch
  0007-iwlwifi-pcie-restore-support-for-Killer-Qu-C0-NICs.patch
  0008-x86-intel-Disable-HPET-on-Intel-Ice-Lake-platforms.patch
  0009-drm-i915-save-AUD_FREQ_CNTRL-state-at-audio-domain-s.patch
  0010-drm-i915-Fix-audio-power-up-sequence-for-gen10-displ.patch
  0011-drm-i915-extend-audio-CDCLK-2-BCLK-constraint-to-mor.patch
  0012-drm-i915-gt-Detect-if-we-miss-WaIdleLiteRestore.patch
  0013-pinctrl-sunrisepoint-Add-missing-Interrupt-Status-re.patch
  0014-Revert-iwlwifi-mvm-fix-scan-config-command-size.patch
  0015-e1000e-Revert-e1000e-Make-watchdog-use-delayed-work.patch

  # Apple SMC ACPI support
  3001-applesmc-convert-static-structures-to-drvdata.patch
  3002-applesmc-make-io-port-base-addr-dynamic.patch
  3003-applesmc-switch-to-acpi_device-from-platform.patch
  3004-applesmc-key-interface-wrappers.patch
  3005-applesmc-basic-mmio-interface-implementation.patch
  3006-applesmc-fan-support-on-T2-Macs.patch

  # T2 USB Keyboard/Touchpad support
  4001-touchpad.patch
  4002-keyboard-backlight.patch

  # Broadcom Wifi rambase debugging additions
  5001-brcmfmac-move-brcmf_mp_device-into-its-own-header.patch
  5002-brcmfmac-Add-ability-to-manually-specify-FW-rambase-.patch

  # MBP Peripheral support
  camera.patch   # UVC Camera support
  wifi.patch     # Broadcom Wifi support  
)

validpgpkeys=(
  'ABAF11C65A2970B130ABE3C479BE3E4300411886'  # Linus Torvalds
  '647F28654894E3BD457199BE38DBBDC86092693E'  # Greg Kroah-Hartman
)

sha256sums=('f23c0218a5e3b363bb5a880972f507bb4dc4a290a787a7da08be07ea12042edd'
            'SKIP'
            'a11412b57ebfff89b50edd327c75c1dbfac953621a7f0ad623d8ebc123e8e094'
            '4352e7f6fec8972bf728312bd5923ab5fa5815f4d29a797b5eb70c7ef88c8fc4'
            '261b3d6b13603d8df7f058b2ba19f8334905ac0c4d2b8970a698b1fec9a39deb'
            'cda71e3d276a72773b4040bd549b229d998071ec7fd2ce2bd0ace15aabeab008'
            '8d101e12018996051c470ab1639e0b230b93486aa601e674af4deefc17b65268'
            '3613b97e2363ee874f0bc240de535832b5afbac3f8d6be91f0a78f258f799b35'
            '82447b66a70b6db74ed465b039f2a4eeb0be2999a6208c4537bace4adea587b9'
            '3c44ce05d1948fba71dc33f96bc736f896156ad7275eb97cf1ff63d5efbbc583'
            '1d59d620e3c9d94f07f230630ffba01ed247bc6ed7172779b4c9da2135f582f0'
            '518cbe8a099791acce532231fbf3c6746ac13884b2421413af22709c5d474922'
            '08ce5f6a4f582ff2074ac49cad1a5526dcebc422a5c3891f6b958d060a7fbdf6'
            'd43a8993791a039f6faf39c60f310ffee6c635476d6ab4ae6e5ecabed061e93a'
            'de0d054f66c3ba29ce2a4f6b3b6ce3ec67192fff3750d8bf04cf88b594b9760c'
            'e35ceb6c1da2b4755ea4e339fb909c12485c1881d28bf98374aa0a00b363ca6b'
            '8336dcf392a5653c7cc9f4b181723c9b53026216011853b22519b7dd7ca27edb'
            '8056c23f76cda6ff676d338b2d9184c885f6685f5338f33f063d5efd69f2b442'
            '7255b4ce6aaa4fdea3623d6be01258580ff6ea04f80e6860db7b2187aff48e22'
            'dc7cf7462f8615df2a6555e2451ee186fb1eb500c6307765af5fce3a321a861c'
            '12d7b4dfb93442ed1288dea15a0a48c5db47b2985947f41f3020568586575713'
            'd24d4ecafca6a9719502d99ce9932b01713737570211408cde05eda57a7c178d'
            '29470448c0443c81a7b4510a6d52cc56958111daa3d7f5198d68ad7516a867a0'
            '9cacf0a7f5a43ef3ed807f050dec7e247b6fbf33cfcdf74ee091f00956165b20'
            '594ee36c0bc7eee93df824017bc32c3f5afb13b14f1a396f28b665c97dc1d7c0'
            '41afb414a69dc9e2b022605e0e63a9e14738c8e8c87984b95969aa8ab3584d77'
            '0318952f59efdce4dc72703adc764940db6fdff184960c27a23a80c3413d8a60'
            '89e1cc266131398309840696ec70cec1315f3ad46d65b3ea393ea14f0673f3b5'
            '717f7fc70a3e3fcfa5ffbac505c8259c1d86718ca1ca6593e8925dac3d29a835'
            'c33b7bb818b3b81fc4db3ed7f15545ee1e38107788daed07d7d2a19700968f9d')

export KBUILD_BUILD_HOST=archlinux
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

prepare() {
  cd $_srcname

  msg2 "Setting version..."
  scripts/setlocalversion --save-scmversion
  echo "-$pkgrel" > localversion.10-pkgrel
  echo "${pkgbase#linux}" > localversion.20-pkgname

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    [[ $src = *.patch ]] || continue
    msg2 "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  msg2 "Setting config..."
  cp ../config .config
  make olddefconfig

  make -s kernelrelease > version
  msg2 "Prepared %s version %s" "$pkgbase" "$(<version)"
}

build() {
  cd $_srcname
  make bzImage modules htmldocs
}

_package() {
  pkgdesc="The $pkgdesc kernel and modules"
  depends=(coreutils kmod initramfs)
  optdepends=('crda: to set the correct wireless channels of your country'
              'linux-firmware: firmware images needed for some devices')
  provides=("linux=$pkgver")

  cd $_srcname
  local kernver="$(<version)"
  local modulesdir="$pkgdir/usr/lib/modules/$kernver"

  msg2 "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"

  msg2 "Installing modules..."
  make INSTALL_MOD_PATH="$pkgdir/usr" modules_install

  # remove build and source links
  rm "$modulesdir"/{source,build}

  msg2 "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the $pkgdesc kernel"
  provides=("linux-headers=$pkgver")

  cd $_srcname
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  msg2 "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # add xfs and shmem for aufs building
  mkdir -p "$builddir"/{fs/xfs,mm}

  msg2 "Installing headers..."
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

  msg2 "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  msg2 "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  msg2 "Removing documentation..."
  rm -r "$builddir/Documentation"

  msg2 "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  msg2 "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  msg2 "Stripping build tools..."
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

  msg2 "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"

  msg2 "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"
}

_package-docs() {
  pkgdesc="Documentation for the $pkgdesc kernel"

  cd $_srcname
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  msg2 "Installing documentation..."
  local src dst
  while read -rd '' src; do
    dst="${src#Documentation/}"
    dst="$builddir/Documentation/${dst#output/}"
    install -Dm644 "$src" "$dst"
  done < <(find Documentation -name '.*' -prune -o ! -type d -print0)

  msg2 "Adding symlink..."
  mkdir -p "$pkgdir/usr/share/doc"
  ln -sr "$builddir/Documentation" "$pkgdir/usr/share/doc/$pkgbase"

  msg2 "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"
}

pkgname=("$pkgbase" "$pkgbase-headers" "$pkgbase-docs")
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
