# Maintainer: Aun-Ali Zaidi <admin@kodeit.net>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgbase=linux-mbp
pkgver=5.4.8
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

  # MBP Peripheral support
  camera.patch   # UVC Camera support
  wifi.patch     # Broadcom Wifi support  
)

validpgpkeys=(
  'ABAF11C65A2970B130ABE3C479BE3E4300411886'  # Linus Torvalds
  '647F28654894E3BD457199BE38DBBDC86092693E'  # Greg Kroah-Hartman
)

sha256sums=('42c414c902193f9e8a1b70c728ca440de02d85dc29102f52ef98cfbf20d29a52'
            'SKIP'
            'a11412b57ebfff89b50edd327c75c1dbfac953621a7f0ad623d8ebc123e8e094'
            'ef048f988d97f3c75b8b02d47a28f97859f84413eb990636c6a6c33db2efe857'
            'bbdcf98efddcaa40012c1220aec9134943f2afd00668ed4a7a96e64c7bd75629'
            '86cb7d220b18ba7de003057ed019e39852ffe96850c3fcdb38d831cd4f510e95'
            '92854e03766672916ab377d6e0dee68aa68de544c1fc810972daab7f76cc6a98'
            '64f376f775e3aaf87169a9545dfb574c81f2e72c3f5add8081c533b822e5068c'
            '5a1e6ab195f970a63d8ad1f0377c910b029313957953186f8b211ae6a27c38cf'
            '0f1ad8d85c7095ef74f28b6f23a2e24c56674cd4e1fd68a22436c975172a0755'
            '7771b153a2e36488e1105d917d6948cba8beeca9cdc24de2c28f9aaa0c924931'
            'd0d20bfb41d866e6e69b84a04751319e4fe98578b949da553678d31ddf9afb23'
            '5180cc08a4bdc9e90ccddf99c4ecbda0e4d31728b9c41d595d6ac4e85434b177'
            'b7e204d2761b5ec19da04d1419df2867dcc18bfedeb3fdc87c2ecfe058b55563'
            '4aaa08158cc31a9c5178a9b864197d6f2d6828505421de5c1b342e3781e5b183'
            '43242e46c83cb988e0a48b22de456a7aec354258a06c4b373ea8806e79ee4a03'
            '7255b4ce6aaa4fdea3623d6be01258580ff6ea04f80e6860db7b2187aff48e22'
            'dc7cf7462f8615df2a6555e2451ee186fb1eb500c6307765af5fce3a321a861c'
            '12d7b4dfb93442ed1288dea15a0a48c5db47b2985947f41f3020568586575713'
            'd24d4ecafca6a9719502d99ce9932b01713737570211408cde05eda57a7c178d'
            '29470448c0443c81a7b4510a6d52cc56958111daa3d7f5198d68ad7516a867a0'
            '9cacf0a7f5a43ef3ed807f050dec7e247b6fbf33cfcdf74ee091f00956165b20'
            '594ee36c0bc7eee93df824017bc32c3f5afb13b14f1a396f28b665c97dc1d7c0'
            '41afb414a69dc9e2b022605e0e63a9e14738c8e8c87984b95969aa8ab3584d77'
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
