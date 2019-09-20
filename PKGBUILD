# Maintainer: Aun-Ali Zaidi <admin@kodeit.net>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Thomas Baechler <thomas@archlinux.org>

pkgbase=linux-mbp
pkgver=5.2.15
_srcname=linux-${pkgver}
pkgrel=1
arch=(x86_64)
url="https://git.archlinux.org/linux.git/log/?h=v$_srcver"
license=(GPL2)
makedepends=(
  xmlto kmod inetutils bc libelf git python-sphinx python-sphinx_rtd_theme
  graphviz imagemagick
)
options=('!strip')

source=(
  https://www.kernel.org/pub/linux/kernel/v${pkgver//.*}.x/linux-${pkgver}.tar.xz
  https://www.kernel.org/pub/linux/kernel/v${pkgver//.*}.x/linux-${pkgver}.tar.sign
  config         # the main kernel config file
  60-linux.hook  # pacman hook for depmod
  90-linux.hook  # pacman hook for initramfs regeneration
  linux.preset   # standard config files for mkinitcpio ramdisk

  # Arch Linux patches
  0001-add-sysctl-to-disallow-unprivileged-CLONE_NEWUSER-by.patch
  0002-ZEN-Add-CONFIG-for-unprivileged_userns_clone.patch

  # MBP ANS2 NVME Controller support
  2001-nvme-pci-Pass-the-queue-to-SQ_SIZE-CQ_SIZE-macros.patch
  2002-nvme-pci-Add-support-for-variable-IO-SQ-element-size.patch
  2003-nvme-pci-Add-support-for-Apple-2018-models.patch
  2004-nvme-pci-Support-shared-tags-across-queues-for-Apple.patch

  # Backported Apple SPI keyboard/touchpad support
  3001-Input-add-Apple-SPI-keyboard-and-trackpad-driver.patch
  3002-Input-applespi-remove-set-but-not-used-variables-sts.patch
  3003-Input-applespi-fix-warnings-detected-by-sparse.patch
  3004-Input-applespi-select-CRC16-module.patch
  3005-Input-applespi-fix-trivial-typo-in-struct-descriptio.patch
  3006-Input-applespi-add-dependency-on-LEDS_CLASS.patch
  3007-Input-applespi-use-struct_size-helper.patch

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

sha256sums=('eb561009da8106b463b1e1a16ab0f75cdef564784f49177148f5f92c32380c4a'
            'SKIP'
            'ca03f3e65af0c4bfde88a864deac18a1b3afdb3fcc88339114272f693bbfadda'
            'ae2e95db94ef7176207c690224169594d49445e04249d2499e9d2fbc117a0b21'
            'c043f3033bb781e2688794a59f6d1f7ed49ef9b13eb77ff9a425df33a244a636'
            'ad6344badc91ad0630caacde83f7f9b97276f80d26a20619a87952be65492c65'
            '2219e0cc40e12f8db3c0df774276156be058bba5913972ca1507c13a4791a50c'
            'd8a77f1feaa5e2c8c9e9b91604060aeee0bf3cf8fd4296088a105bac40743ac3'
            'db8ca5a3cf93522c5a93853acc44ef24cf1c41d0a6682c9f87cd918dcee96eb8'
            '15824843737696c0914c6a5720e7d869bc3375f646f62c699e736da79619d655'
            'cfda9f963272aa81dcf0632f6367ef5149fdfb75444f72bc37a8bad554d63d92'
            '8cd292bf560d89858a29e34fe6dc477df461350aa50b3a89d01db1ee5c576b78'
            '1c793d05446d361f3c1a160e86b01dceea922218fc17d5834ecd816118fb3495'
            '9bd2c7822f51a809fe3b40cf9022d324cc27e2bee8858138af3240b52cf0af55'
            'adf8deb4de1021afc23dd95398142ca18068d7af9f912685d5c7fbe6179c8be4'
            '7111e6d8331f48213d53f276d734ea0d6daa0f788c3fad429264291b30457b1e'
            'c37b22ae17e26ac40c7a217503041dd3e95054df3d0ab61257610ba0e5c511a3'
            '325d2d904d1613b5678131fc4fd3e81d9e38b8fc4ea0ede90f1577e418baa596'
            '5ec9cabde47610a7f2f6ef8cbf4ea8944f835a62542fb344b059ceb333637e00'
            '594ee36c0bc7eee93df824017bc32c3f5afb13b14f1a396f28b665c97dc1d7c0'
            'c2ce62bae7063636c4352b1d6a48656df938822b2c77b3560782b628c864546b'
            '717f7fc70a3e3fcfa5ffbac505c8259c1d86718ca1ca6593e8925dac3d29a835'
            '0990a04ffd9e276d377f4057e5ae3c6b849a500fd9cfb57ede05ddd3be3f4dfa')

_kernelname=${pkgbase#linux}
: ${_kernelname:=-mbp}

prepare() {
  cd $_srcname

  msg2 "Setting version..."
  scripts/setlocalversion --save-scmversion
  echo "-$pkgrel" > localversion.10-pkgrel
  echo "$_kernelname" > localversion.20-pkgname

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

  make -s kernelrelease > ../version
  msg2 "Prepared %s version %s" "$pkgbase" "$(<../version)"
}

build() {
  cd $_srcname
  make bzImage modules htmldocs
}

_package() {
  pkgdesc="The ${pkgbase/linux/Linux} kernel and modules"
  [[ $pkgbase = linux ]] && groups=(base)
  depends=(coreutils linux-firmware kmod mkinitcpio)
  optdepends=('crda: to set the correct wireless channels of your country')
  backup=("etc/mkinitcpio.d/$pkgbase.preset")
  install=linux.install

  local kernver="$(<version)"
  local modulesdir="$pkgdir/usr/lib/modules/$kernver"

  cd $_srcname

  msg2 "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"
  install -Dm644 "$modulesdir/vmlinuz" "$pkgdir/boot/vmlinuz-$pkgbase"

  msg2 "Installing modules..."
  make INSTALL_MOD_PATH="$pkgdir/usr" modules_install

  # a place for external modules,
  # with version file for building modules and running depmod from hook
  local extramodules="extramodules$_kernelname"
  local extradir="$pkgdir/usr/lib/modules/$extramodules"
  install -Dt "$extradir" -m644 ../version
  ln -sr "$extradir" "$modulesdir/extramodules"

  # remove build and source links
  rm "$modulesdir"/{source,build}

  msg2 "Installing hooks..."
  # sed expression for following substitutions
  local subst="
    s|%PKGBASE%|$pkgbase|g
    s|%KERNVER%|$kernver|g
    s|%EXTRAMODULES%|$extramodules|g
  "

  # hack to allow specifying an initially nonexisting install file
  sed "$subst" "$startdir/$install" > "$startdir/$install.pkg"
  true && install=$install.pkg

  # fill in mkinitcpio preset and pacman hooks
  sed "$subst" ../linux.preset | install -Dm644 /dev/stdin \
    "$pkgdir/etc/mkinitcpio.d/$pkgbase.preset"
  sed "$subst" ../60-linux.hook | install -Dm644 /dev/stdin \
    "$pkgdir/usr/share/libalpm/hooks/60-$pkgbase.hook"
  sed "$subst" ../90-linux.hook | install -Dm644 /dev/stdin \
    "$pkgdir/usr/share/libalpm/hooks/90-$pkgbase.hook"

  msg2 "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"
}

_package-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} kernel"

  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  cd $_srcname

  msg2 "Installing build files..."
  install -Dt "$builddir" -m644 Makefile .config Module.symvers System.map vmlinux
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # add xfs and shmem for aufs building
  mkdir -p "$builddir"/{fs/xfs,mm}

  # ???
  mkdir "$builddir/.tmp_versions"

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
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase-$pkgver"

  msg2 "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"
}

_package-docs() {
  pkgdesc="Kernel hackers manual - HTML documentation that comes with the ${pkgbase/linux/Linux} kernel"

  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  cd $_srcname

  msg2 "Installing documentation..."
  mkdir -p "$builddir"
  cp -t "$builddir" -a Documentation

  msg2 "Removing doctrees..."
  rm -r "$builddir/Documentation/output/.doctrees"

  msg2 "Moving HTML docs..."
  local src dst
  while read -rd '' src; do
    dst="$builddir/Documentation/${src#$builddir/Documentation/output/}"
    mkdir -p "${dst%/*}"
    mv "$src" "$dst"
    rmdir -p --ignore-fail-on-non-empty "${src%/*}"
  done < <(find "$builddir/Documentation/output" -type f -print0)

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
