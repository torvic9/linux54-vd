# Based on the file created for Arch Linux by:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

# Maintainer: Philip Müller (x86_64) <philm@manjaro.org>
# Maintainer: Jonathon Fernyhough (i686) <jonathon@manjaro.org>
# Contributor: Helmut Stult <helmut[at]manjaro[dot]org>
# torvic9

pkgbase=linux54-vd
pkgname=('linux54-vd' 'linux54-vd-headers')
_kernelname=-vd
_basekernel=5.4
_basever=54
_sub=1
pkgver=${_basekernel}.${_sub}
pkgrel=3
arch=('x86_64')
url="http://www.kernel.org/"
license=('GPL2')
makedepends=('xmlto' 'docbook-xsl' 'kmod' 'inetutils' 'bc' 'elfutils' 'git')
options=('!strip')
source=(https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-${pkgver}.tar.{xz,sign}
        # the main kernel config files
        'config.x86_64' 'config.vd'
        # ARCH Patches
        0001-ZEN-Add-sysctl-and-CONFIG-to-disallow-unprivileged-CLONE_NEWUSER.patch
        # MANJARO Patches
        '0001-nonupstream-navi10-vfio-reset.patch'
        '0001-drm-amdgpu-Add-DC-feature-mask-to-disable-fractional-pwm.patch'
        # vd
	0001-futex.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/futex-patches-sep/0001-futex-Split-key-setup-from-key-queue-locking-and-rea.patch
	0002-futex.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/futex-patches-sep/0002-futex-Implement-mechanism-to-wait-on-any-of-several-.patch
	0003-futex.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/futex-patches-sep/0003-futex-Change-WAIT_MULTIPLE-opcode-to-31.patch
	cpu-optimisations-graysky.patch
	0001-clearlinux-tweak-cpuidle.patch::https://raw.githubusercontent.com/clearlinux-pkgs/linux/master/0106-intel_idle-tweak-cpuidle-cstates.patch
	0002-clearlinux-add-config-raid6.patch::https://raw.githubusercontent.com/clearlinux-pkgs/linux/master/0109-raid6-add-Kconfig-option-to-skip-raid6-benchmarking.patch
	0003-clearlinux-init-ata-before-graphics.patch::https://raw.githubusercontent.com/clearlinux-pkgs/linux/master/0110-Initialize-ata-before-graphics.patch
	add-nvme-hwmon-temp.patch
	0001-tune-vm-and-vfs-settings.patch
	0002-tune-cfs-scheduler.patch
	block-optimisations-hho.patch
)
sha256sums=('a7d48bb324d53e421ffbe4da40087b3c0c5112707e5f3d827c30118542c74fd9'
            'SKIP'
            '1f2a113cf9df4dc1df2e7b5dbe307e52b92f35572ead855492ff33dd0ee09acb'
            'aa14ab02031ef9bec74941eb89097bbfcd294aaadb9461a0ed5a17208dffc474'
            '7685d526bbdbfa795986591a70071c960ff572f56d3501774861728a9df8664c'
            '7a2758f86dd1339f0f1801de2dbea059b55bf3648e240878b11e6d6890d3089c'
            '1fd4518cb0518d68f8db879f16ce16455fdc2200ed232f9e27fb5f1f3b5e4906'
            'fd1f34cf87e72ccd6070590028ad34e12dc42285637a0c61894680cb81d4fb88'
            '9660f0d31bdc5718b7fde41015898f67dce86602886585848d6300dfce2542db'
            'cd228e4b62cab5679c93cd0eda5d96d570f1b3ba84340eddd2d049f2a07eef9d'
            '607097f22f202cd829f12acce7a401fb7f7af5678ffeda90c1fc7da71b895ad7'
            '819e206f4ef8c50fbe5112ea8566c5193fee522c7f28396af28d1dfdc3546ae0'
            '672343639203797b194025f864845dea8097d4650b7af19e1cacdd2bfe9013b0'
            '6cf992514973b94cffe81b5547a8c76c0ccd03f7bafc1a234c5af4ba34cc1a9d'
            'c6944879f5cdfd335a3adc75b6f6194d127ad93d4dd5bf90d2ad505e83c9b6d2'
            'f4041dc77564ee6de09c1c02c59068b8eceb6fbdbe60158acdec0a0cfb5cb3f7'
            'f4f42dd737f2398a27d674cb7cb666f299b15542f05f35dcd4b8e1835a845c10'
            '74eb904dea0162eace78cbf6ab68bb3d151522c84efc3c55ba0c23a21db126c2')
prepare() {
  cd "${srcdir}/linux-${pkgver}"

  # add latest fixes from stable queue, if needed
  # http://git.kernel.org/?p=linux/kernel/git/stable/stable-queue.git
  # enable only if you have "gen-stable-queue-patch.sh" executed before
  #patch -Np1 -i "${srcdir}/prepatch-${_basekernel}`date +%Y%m%d`"

  # disable USER_NS for non-root users by default
  patch -Np1 -i ../0001-ZEN-Add-sysctl-and-CONFIG-to-disallow-unprivileged-CLONE_NEWUSER.patch

  # https://bugzilla.kernel.org/show_bug.cgi?id=204957
  patch -Np1 -i "${srcdir}/0001-drm-amdgpu-Add-DC-feature-mask-to-disable-fractional-pwm.patch"

  # TODO: remove when AMD properly fixes it!
  # INFO: this is a hack and won't be upstreamed
  # https://forum.level1techs.com/t/145666/86
  # https://forum.manjaro.org/t/107820/11
  patch -Np1 -i "${srcdir}/0001-nonupstream-navi10-vfio-reset.patch"

  # vd
  patch -Np1 -i ../0001-futex.patch
  patch -Np1 -i ../0002-futex.patch
  patch -Np1 -i ../0003-futex.patch
  patch -Np1 -i ../0001-clearlinux-tweak-cpuidle.patch
  patch -Np1 -i ../0002-clearlinux-add-config-raid6.patch
  patch -Np1 -i ../0003-clearlinux-init-ata-before-graphics.patch
  patch -Np1 -i ../cpu-optimisations-graysky.patch
  patch -Np1 -i ../add-nvme-hwmon-temp.patch
  patch -Np1 -i ../block-optimisations-hho.patch
  patch -Np1 -i ../0001-tune-vm-and-vfs-settings.patch
  patch -Np1 -i ../0002-tune-cfs-scheduler.patch

  cat "${srcdir}/config.vd" > ./.config

  if [ "${_kernelname}" != "" ]; then
    sed -i "s|CONFIG_LOCALVERSION=.*|CONFIG_LOCALVERSION=\"${_kernelname}\"|g" ./.config
    sed -i "s|CONFIG_LOCALVERSION_AUTO=.*|CONFIG_LOCALVERSION_AUTO=n|" ./.config
  fi

  # set patchlevel to 4
  sed -ri "s|^(PATCHLEVEL =).*|\1 4|" Makefile

  # set extraversion to pkgrel
  sed -ri "s|^(EXTRAVERSION =).*|\1 -${pkgrel}|" Makefile

  # don't run depmod on 'make install'. We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh

  # get kernel version
  make prepare

  # load configuration
  # Configure the kernel. Replace the line below with one of your choice.
  #make menuconfig # CLI menu for configuration
  make nconfig # new CLI menu for configuration
  #make xconfig # X-based configuration
  #make oldconfig # using old config from previous kernel version
  # ... or manually edit .config

  # rewrite configuration
  yes "" | make config >/dev/null
}

build() {
  cd "${srcdir}/linux-${pkgver}"

  # build!
  make ${MAKEFLAGS} LOCALVERSION= bzImage modules
}

package_linux54-vd() {
  pkgdesc="The ${pkgbase/linux/Linux} vd kernel and modules"
  depends=('coreutils' 'linux-firmware' 'kmod' 'mkinitcpio>=27')
  optdepends=('crda: to set the correct wireless channels of your country')
  provides=("linux=${pkgver}")

  cd "${srcdir}/linux-${pkgver}"

  KARCH=x86

  # get kernel version
  _kernver="$(make LOCALVERSION= kernelrelease)"

  mkdir -p "${pkgdir}"/{boot,usr/lib/modules}
  make LOCALVERSION= INSTALL_MOD_PATH="${pkgdir}/usr" modules_install

  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  cp arch/$KARCH/boot/bzImage "${pkgdir}/usr/lib/modules/${_kernver}/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "${pkgbase}" | install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_kernver}/pkgbase"
  echo "${_basekernel}${_kernelname}-${CARCH}" | install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_kernver}/kernelbase"

  # add kernel version
  echo "${pkgver}-${pkgrel}${_kernelname} x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  # make room for external modules
  local _extramodules="extramodules-${_basekernel}${_kernelname:--vd}"
  ln -s "../${_extramodules}" "${pkgdir}/usr/lib/modules/${_kernver}/extramodules"

  # add real version for building modules and running depmod from hook
  echo "${_kernver}" |
    install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_extramodules}/version"

  # remove build and source links
  rm "${pkgdir}"/usr/lib/modules/${_kernver}/{source,build}

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "${_kernver}"

  # add vmlinux
  install -Dt "${pkgdir}/usr/lib/modules/${_kernver}/build" -m644 vmlinux
}

package_linux54-vd-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} vd kernel"
  provides=("linux-headers=$pkgver")

  cd "${srcdir}/linux-${pkgver}"
  local _builddir="${pkgdir}/usr/lib/modules/${_kernver}/build"

  install -Dt "${_builddir}" -m644 Makefile .config Module.symvers
  install -Dt "${_builddir}/kernel" -m644 kernel/Makefile

  mkdir "${_builddir}/.tmp_versions"

  cp -t "${_builddir}" -a include scripts

  install -Dt "${_builddir}/arch/${KARCH}" -m644 "arch/${KARCH}/Makefile"
  install -Dt "${_builddir}/arch/${KARCH}/kernel" -m644 "arch/${KARCH}/kernel/asm-offsets.s"
  #install -Dt "${_builddir}/arch/${KARCH}/kernel" -m644 "arch/${KARCH}/kernel/macros.s"

  if [ "${CARCH}" = "i686" ]; then
    install -Dt "${_builddir}/arch/${KARCH}" -m644 "arch/${KARCH}/Makefile_32.cpu"
  fi

  cp -t "${_builddir}/arch/${KARCH}" -a "arch/${KARCH}/include"

  install -Dt "${_builddir}/drivers/md" -m644 drivers/md/*.h
  install -Dt "${_builddir}/net/mac80211" -m644 net/mac80211/*.h

  # http://bugs.archlinux.org/task/13146
  install -Dt "${_builddir}/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # http://bugs.archlinux.org/task/20402
  install -Dt "${_builddir}/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "${_builddir}/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "${_builddir}/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # add xfs and shmem for aufs building
  mkdir -p "${_builddir}"/{fs/xfs,mm}

  # copy in Kconfig files
  find . -name Kconfig\* -exec install -Dm644 {} "${_builddir}/{}" \;

  if [ "${CARCH}" = "x86_64" ]; then
    # add objtool for external module building and enabled VALIDATION_STACK option
    install -Dt "${_builddir}/tools/objtool" tools/objtool/objtool
  fi

  # remove unneeded architectures
  local _arch
  for _arch in "${_builddir}"/arch/*/; do
    [[ ${_arch} == */x86/ ]] && continue
    rm -r "${_arch}"
  done

  # remove files already in linux-docs package
  rm -r "${_builddir}/Documentation"

  # Fix permissions
  chmod -R u=rwX,go=rX "${_builddir}"

  # strip scripts directory
  local _binary _strip
  while read -rd '' _binary; do
    case "$(file -bi "${_binary}")" in
      *application/x-sharedlib*)  _strip="${STRIP_SHARED}"   ;; # Libraries (.so)
      *application/x-archive*)    _strip="${STRIP_STATIC}"   ;; # Libraries (.a)
      *application/x-executable*) _strip="${STRIP_BINARIES}" ;; # Binaries
      *) continue ;;
    esac
    /usr/bin/strip ${_strip} "${_binary}"
  done < <(find "${_builddir}/scripts" -type f -perm -u+w -print0 2>/dev/null)
}