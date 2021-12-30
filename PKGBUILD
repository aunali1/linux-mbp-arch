# Maintainer: Aun-Ali Zaidi <admin@kodeit.net>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgbase=linux-mbp
pkgver=5.15.12
_srcname=linux-${pkgver}
pkgrel=4
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

  # Hack for AMD DC eDP link rate bug
  2001-drm-amd-display-Force-link_rate-as-LINK_RATE_RBR2-fo.patch

  # Apple SMC ACPI support
  3001-applesmc-convert-static-structures-to-drvdata.patch
  3002-applesmc-make-io-port-base-addr-dynamic.patch
  3003-applesmc-switch-to-acpi_device-from-platform.patch
  3004-applesmc-key-interface-wrappers.patch
  3005-applesmc-basic-mmio-interface-implementation.patch
  3006-applesmc-fan-support-on-T2-Macs.patch
  3007-applesmc-Add-iMacPro-to-applesmc_whitelist.patch

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

  # MBP Peripheral support
  6001-media-uvcvideo-Add-support-for-Apple-T2-attached-iSi.patch	# UVC Camera support

  # Hack for i915 overscan issues
  7001-drm-i915-fbdev-Discard-BIOS-framebuffers-exceeding-h.patch

  # Broadcom WIFI device support
  8001-brcmfmac-pcie-Declare-missing-firmware-files-in-pcie.patch
  8002-brcmfmac-firmware-Support-having-multiple-alt-paths.patch
  8003-brcmfmac-firmware-Handle-per-board-clm_blob-files.patch
  8004-brcmfmac-pcie-sdio-usb-Get-CLM-blob-via-standard-fir.patch
  8005-brcmfmac-firmware-Support-passing-in-multiple-board_.patch
  8006-brcmfmac-pcie-Read-Apple-OTP-information.patch
  8007-brcmfmac-of-Fetch-Apple-properties.patch
  8008-brcmfmac-pcie-Perform-firmware-selection-for-Apple-p.patch
  8009-brcmfmac-firmware-Allow-platform-to-override-macaddr.patch
  8010-brcmfmac-msgbuf-Increase-RX-ring-sizes-to-1024.patch
  8011-brcmfmac-pcie-Fix-crashes-due-to-early-IRQs.patch
  8012-brcmfmac-pcie-Support-PCIe-core-revisions-64.patch
  8013-brcmfmac-pcie-Add-IDs-properties-for-BCM4378.patch
  8014-ACPI-property-Support-strings-in-Apple-_DSM-props.patch
  8015-brcmfmac-acpi-Add-support-for-fetching-Apple-ACPI-pr.patch
  8016-brcmfmac-pcie-Provide-a-buffer-of-random-bytes-to-th.patch
  8017-brcmfmac-pcie-Add-IDs-properties-for-BCM4355.patch
  8018-brcmfmac-pcie-Add-IDs-properties-for-BCM4377.patch
  8019-brcmfmac-pcie-Perform-correct-BCM4364-firmware-selec.patch
  8020-brcmfmac-chip-Only-disable-D11-cores-handle-an-arbit.patch
  8021-brcmfmac-chip-Handle-1024-unit-sizes-for-TCM-blocks.patch
  8022-brcmfmac-cfg80211-Add-support-for-scan-params-v2.patch
  8023-brcmfmac-feature-Add-support-for-setting-feats-based.patch
  8024-brcmfmac-cfg80211-Add-support-for-PMKID_V3-operation.patch
  8025-brcmfmac-cfg80211-Pass-the-PMK-in-binary-instead-of-.patch
  8026-brcmfmac-pcie-Add-IDs-properties-for-BCM4387.patch
  8027-brcmfmac-pcie-Replace-brcmf_pcie_copy_mem_todev-with.patch
  8028-brcmfmac-pcie-Read-the-console-on-init-and-shutdown.patch
  8029-brcmfmac-pcie-Release-firmwares-in-the-brcmf_pcie_se.patch
  8031-brcmfmac-fwil-Constify-iovar-name-arguments.patch
  8032-brcmfmac-common-Add-support-for-downloading-TxCap-bl.patch
  8033-brcmfmac-pcie-Load-and-provide-TxCap-blobs.patch
  8034-brcmfmac-common-Add-support-for-external-calibration.patch

  # Broadcom P2P VIF fix
  8035-brcmfmac-p2p-Ensure-virtual-interface-is-initialized.patch

  # Broadcom BT device support
  9001-bluetooth-add-disable-read-tx-power-quirk.patch
  9002-mfd-intel-lpss-Add-support-for-MacBookPro16-2-ICL-N-.patch
  9003-mfd-intel-lpss-Fix-too-early-PM-enablement-in-the-AC.patch


)

validpgpkeys=(
  'ABAF11C65A2970B130ABE3C479BE3E4300411886'  # Linus Torvalds
  '647F28654894E3BD457199BE38DBBDC86092693E'  # Greg Kroah-Hartman
)

sha256sums=('7de919772b62647591527e904e3b3583783381a29d812404f58a222484e751a0'
            'SKIP'
            '6ab7a66895804f832f1b9594b682be0e2e6982455a8fc3f7e87111e1c7dff866'
            'ea16157696cb1807f8960de667a8c56da223bfae02c94d7b2aed6853c541f2ed'
            '786dfc22e4c6ece883e7dedd0ba3f6c14018584df95450b2cb78f3da8b01f7cb'
            '7366a08383900a09f8e742b1e4f0a02e0839a385e68e70a89d1815c197df3300'
            '8d8401a99a9dfbc41aa2dc5b6a409a19860b1b918465e19de4a4ff18de075ea3'
            '08d165106fe35b68a7b48f216566951a5db0baac19098c015bcc81c5fcba678d'
            '459906cab172df9f6712a4168e7a5d529f85b2bb58a068f2d44746df14a6d27a'
            '2827dab6eeb2d2a08034938024f902846b5813e967a0ea253dc1ea88315da383'
            '398dec7d54c6122ae2263cd5a6d52353800a1a60fd85e52427c372ea9974a625'
            '3aaab94e7dc3b73ec51778db07fde1f15a7606b7dce3cc13ee472ae24deddbc9'
            '11565cff9c6a7db8846dc7d5930419045e9527863b8df5979a7465006211bd16'
            '83f4be6849ba4d5f9fad647ad2eb78bf6409ee98a40ac62e8a5b80496233d70a'
            '44bd3643b2b22fedc59d79511199f30ce6759fa0acdd9a66262a53c5e046da6b'
            'eb04a492197783643b3e72b1d0cf0e856290381997bd165a14fbc63ac1489c25'
            '69d56d42473526f7dbd4fb18c5e1baafe4e6d32995b2506bd48ff981c53b5385'
            '1deeacae1875cf9075b858a8bfb2463ebc531c9030b7c2ab46bbb8e4c3b974db'
            '40eff5e88bb30c51c6b97e85c2e7b8dec5f97916f768e6c07618d9c5afe68574'
            'cac035fe07663a319185c644c5b39b34bef89ada348881fa4a02d15290260445'
            '9dfa9f02d17c5cd9620fa2c1d43ca967b81b6a56d33c2bafae14e0c64e498baa'
            '9640178d6251686c980c30fc528b3d70beac6ce8246bf433506a3f843808326c'
            '90a6012cdd8a64ede8e0bbaf7331960bd68f628e0973b65459188eb1ccb5b829'
            '862f631ef9f25453ce38d9ed0197e62d85f9f5a0625ed77237e643297fb42f75'
            '2f7899b70d5c55aea3f6385385fea01ce21b48f9441982a94f36c842cceec083'
            '2b126cda3863f49b8d3a6de8fa8cca979d87bd9e66812531be5c02c9e5840d82'
            '70a277c9ad4fba624b3916e397624e557135b269c34eb704ace29aa1a6b8e430'
            '42ae52b93ea0cbd0d1859512b88e0c290e3500b8e52f8de3be7398cb6039d0b4'
            '300d926bac23b81d267e73433d668581ec1e3b12fa76462ba3d0b1cf2728b82d'
            '01f3185e551dd49007b533d4bae37774131820a51715e1f1a391220e055afc66'
            'db55305b8e3c2a8fa0a85aeaad661717ae745d5dabc7735221adb184e89a2d1b'
            '82f679f3736e09ee9ea8a8b53c052e84bb40df8a05f21a2082224184ad3cf162'
            '9907f67d099a2b6243747350a2c057d82c39e822107ca57cbfdc32baf378d2cb'
            'd25cd32de8c74ba8bcb430c21f9d84deae1174594d00ea94e1fd1e2ab70ea5cb'
            '823d35349844605dadf381ae7c6097379a23c72da59e3cf393fcf3e5d466dafd'
            'ed6e84bc03cd6adfc3f8def843f150b71470df6d6a88fc348d5e1b36f133f424'
            '23d9018c90d02389f2ddeb0821e581d354184b3b38d4488fbc0f3363463a0c9e'
            'd2e2b0f0c80fb5b4da36d3a7a87b10c2419255c0e38e0faa1d7478eaab1b9a35'
            'ecef58f944bf61950b3211e88acd104b0006a177e76f59a47b8253aaf5e6acc6'
            '1eb6e14b5504efbad7911aabc801a265e9ba13cb2fd6ce8e029af55bf97cec86'
            'f2b553e11240bb88e5d0ffd7883d808c069ede544e5c578c22975466a5c9d26a'
            'ac4b200dadbb88179bf37dcea280efe25bf42b420a90ab1399c3bd9c7905f592'
            'e12726162b868435081a215f04d921cd8b9307de71738c41090ec93a267725de'
            'bfa3bb8d16b6c26831f9b5e833d46ea2c60854f016540a051f96c418be1a728f'
            'e9df13adedefd0043ea6678c19a9de608aa69fe83929a13213c528052096ed3c'
            'b51a916bb0048d7cb57ed2afc25394ec72664efe2a8c5705b0dcfe62384e34ed'
            '2ec5dddd41327b5018d41b920955182bc3f220f692a32b061d8797c8fee99dbc'
            'a8596e6180a895515cbc1f361edc8fca460f630dd15bbd161037d84717717ba8'
            '55b6981468b489f5bb7c59d5f9a6b479c0d96bb1018efa209ed8506d54de8399'
            '2339acd32f020db66f2a3190910d925a030798e3fd57006a09dda56e5acbf279'
            'f41ab41dd9445dee28699c1af7909723514f9d41d30a5c148d4f99617ed2d46e'
            '0e6cd10376f13873a9226d233161a0dab6b1d3c6a7d66bc3c4e8d3cc0f0397d0'
            '8f9a6d47eaec7d9df9a822a146ab15ca7bee906866545493cac8621570237060'
            'ecede30aa68ea4646d3efb0a7190466ff1784f4e93756a04bb58756536f28035'
            '0bed877897873ae86e512d711b86fa11adc5b8e7fe35139e290e8d0a0133f6a5'
            '23f4a7002632f95abb1ed75a4df0570b7a81e5cf4067a16da7101b16eb582a01'
            'fa0ad2e2f171eafd727d780588f7ef5d47ddf2d75fab02c67356bbc7b26e25e0'
            '31e414978a947bdb71f27ed364c4da73b81fcf1921250cb69ee1bcf2bbd25636'
            '8aeed7ebb2544aabf2361c7eaeea4ab76f1ce2c5f6257224545b82ef42cf4b44'
            '3bffb2bb84800453ba05676293de9b0b1619d0c19b6295e803f0d9c3a07be23a')

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

  # https://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "$builddir/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

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
