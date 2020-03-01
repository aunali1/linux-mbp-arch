# Maintainer: Aun-Ali Zaidi <admin@kodeit.net>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgbase=linux-mbp
pkgver=5.5.7
_srcname=linux-${pkgver}
pkgrel=1
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
  0002-iwlwifi-pcie-restore-support-for-Killer-Qu-C0-NICs.patch
  0003-iwlwifi-mvm-Do-not-require-PHY_SKU-NVM-section-for-3.patch
  0004-drm-Remove-PageReserved-manipulation-from-drm_pci_al.patch
  0005-drm-i915-Serialise-i915_active_acquire-with-__active.patch
  0006-drm-i915-gem-Take-runtime-pm-wakeref-prior-to-unbind.patch
  0007-drm-i915-gem-Avoid-parking-the-vma-as-we-unbind.patch
  0008-drm-i915-gem-Try-to-flush-pending-unbind-events.patch
  0009-drm-i915-gem-Reinitialise-the-local-list-before-repe.patch
  0010-drm-i915-Add-a-simple-is-bound-check-before-unbindin.patch
  0011-drm-i915-Introduce-a-vma.kref.patch

  # Linux 5.5+ Broadcom HCI Bluetooth detection fix
  2001-serdev-Fix-detection-of-UART-devices-on-Apple-machin.patch

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

sha256sums=('b843ef331290559c5cfce99616165154899e3d7906898ec7de5054efd39f7e48'
            'SKIP'
            'a5cc9786b08383d3d0cdc0d146ddeedceb4d20bd5c73092e258da9ad98121034'
            '031da8c40d8e3883d4a3ca6e364dda6f9ff9fb06f09e1b5c6f33bde9e0403d1f'
            'ede75f02724a78d140248bed46905b7a55aa835916101ceb9dd4a79c390a57ac'
            'ec4b1dc9a0d55711ed118b675b33f0a0a9cdb980175fbfd2ada28482aabb371a'
            'f8f7a9fcbd3718c4ddb8506f7e0308a9a5ad93347fbbd8d4f8328c9e5941e8a7'
            'e92d16f56a48c65c15c10a920fdaefe127ed0bfeefe4c41673dab880d4d44792'
            'dedd5714d6eae4fd9ef688ad60792918944b4878bdfb7e92f04ea451099b1574'
            '9bebae617f1f8a5a0b68331a94ed504756bc18cbed899d23bfbb244309a21240'
            '7037a82c30df8eb51997e3325b0a9f295cc6b77fd8bd045725f22fc0b470d754'
            '77077b38c064f79abeb5cd02b77c0502eb859fd6ae23ba4c84143eccdcba543a'
            '2a40785a40e8d1c50ada94d79fc12915ef4ad75fdc97e7132494383fb975136c'
            '4f3b5a9f71a66fa1e6e403113ff7432a099d82c3d79ce26692bc11d30b48c3f5'
            '9bb8de4cba26cf2eaa540bd9fccf1cbce00805c74fc627cab68fd265d2075570'
            '25e1aac0d44d72e377f08e4f4b90351cffcacc0be63e02a4033cb99f10cc9fe7'
            'c70118659c5cf6a5c7f060c941d46fdd3b1e6d28f2b62c24a941745f2b3c4732'
            '3855aa07fab97d202900216951225b6952d7c716258a3c3727df8e6277289ee0'
            '9e5e0b45fe007ed214049b26b44174ee8f61376076e80fd33bba9fdac001e157'
            '3c8a361370ed3ee094e2c8af1ff5360fd78f24e387c250904031fb70e8f2bb6e'
            '8e43d95104301913737e5d73860f0e21bb0e5e25dcfd0f16d48a0715b38c98a1'
            'e1d72fdb0a7a66a6f3fc8afb6fe056f28cfa088c1cc9c799b93405b62a274b96'
            'a6c070d7b7444d711d9cb6b28bccb774228864132ef83dd3a291df3353e85465'
            '0318952f59efdce4dc72703adc764940db6fdff184960c27a23a80c3413d8a60'
            'e632f2959efca848fd28acb5e278cc476f8fb54d70ca95272b0a76add47e474e'
            '717f7fc70a3e3fcfa5ffbac505c8259c1d86718ca1ca6593e8925dac3d29a835'
            '359555c0c391fdac9c57e2d0be9af5570767218ccae9be9d51175970c54cacc8')

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
  make INSTALL_MOD_PATH="$pkgdir/usr" modules_install

  # remove build and source links
  rm "$modulesdir"/{source,build}

  echo "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"
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

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"

  echo "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"
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

  echo "Fixing permissions..."
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
