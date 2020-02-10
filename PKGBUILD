# Based on the file created for Arch Linux by:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

# Maintainer: Philip Müller (x86_64) <philm@manjaro.org>
# Maintainer: Jonathon Fernyhough (i686) <jonathon@manjaro.org>
# Contributor: Helmut Stult <helmut[at]manjaro[dot]org>
# Maintainer (vd): torvic9

pkgbase=linux54-vd
pkgname=('linux54-vd' 'linux54-vd-headers')
_basekernel=5.4
_kernelname=-vd
_sub=18
kernelbase=${_basekernel}${_kernelname}
pkgver=${_basekernel}.${_sub}
pkgrel=2
_archpatch=20200203
arch=('x86_64')
url="http://www.kernel.org/"
license=('GPL2')
makedepends=('xmlto' 'docbook-xsl' 'kmod' 'inetutils' 'bc' 'elfutils' 'git')
options=('!strip')
source=(https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-${pkgver}.tar.{xz,sign}
		# the main kernel config files
		'config.x86_64' 'config.vd' 'config.x200' 'config.x270' 'config.x570' 'x509.genkey' "${pkgbase}.preset"
		# Prepatch from stable-queue
		#
		# ARCH Patches
		0001-arch-patches-${_archpatch}.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/arch-patches-v24/0001-arch-patches.patch
		# MANJARO Patches
		0001-i2c-nuvoton-nc677x-hwmon-driver.patch
		0002-amdgpu-nonupstream-navi10-vfio-reset.patch
		# amdgpu
		0001-amdgpu-sriov-vf-does-not-support-baco.patch
		0002-amdgpu-fix-gfx-vf-flr-fail-on-navi.patch
		0003-amdgpu-update-gfx-golden-settings-20191211.patch
		0004-amdgpu-update-gfx-golden-settings-for-navi14-20191211.patch
		0005-amdgpu-fix-calltrace-during-kmd-unload.patch
		0006-amdgpu-skip-rlc-ucode-loading.patch
		0007-amdgpu-fix-mqd-backup-restore.patch
		0008-amdgpu-should-stop-gfx-ring.patch
		0009-amdgpu-fix-gfx10-missing-csib-set.patch
		0010-amdgpu-unlock-srbm-mutex.patch
		0011-amdgpu-revert-dont-schedule-jobs-while-in-reset.patch
		# BMQ scheduler
		#0001-bmq-linux54-20200117.patch::https://gitlab.com/alfredchen/bmq/raw/master/5.4/bmq_v5.4-r2.patch
		# sirlucjan
		0001-futex-steam-fsync.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/futex-patches-sep/0001-futex-Split-key-setup-from-key-queue-locking-and-rea.patch
		0002-futex-steam-fsync.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/futex-patches-sep/0002-futex-Implement-mechanism-to-wait-on-any-of-several-.patch
		0003-futex-steam-fsync.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/futex-patches-sep/0003-futex-Change-WAIT_MULTIPLE-opcode-to-31.patch
		#0004-futex-steam-fsync.patch::https://raw.githubusercontent.com/sirlucjan/kernel-patches/master/5.4/futex-patches-v2/0001-futex-Add-support-for-multiple-keys-at-the-same-time.patch
		0001-clearlinux-tweak-intel-cpuidle.patch::https://raw.githubusercontent.com/clearlinux-pkgs/linux/master/0106-intel_idle-tweak-cpuidle-cstates.patch
		0002-clearlinux-add-config-opt-for-raid6-bench.patch::https://raw.githubusercontent.com/clearlinux-pkgs/linux/master/0109-raid6-add-Kconfig-option-to-skip-raid6-benchmarking.patch
		0003-clearlinux-init-ata-before-graphics.patch::https://raw.githubusercontent.com/clearlinux-pkgs/linux/master/0110-Initialize-ata-before-graphics.patch
		0004-clearlinux-rcu-nocb-fix-dump.patch::https://raw.githubusercontent.com/clearlinux-pkgs/linux/master/0052-rcu-nocb-Fix-dump_tree-hierarchy-print-always-active.patch
		# vd
		0001-tune-vm-and-vfs-settings.patch
		0002-tune-cfs-scheduler.patch
		0003-optimise-module-compression.patch
		0004-add-nvme-hwmon-temp.patch
		0005-cpu-optimisations-graysky.patch
		0006-tune-cpufreq-ondemand.patch
		# hho
		0001-enable-O3-opt-for-all-arches.patch::https://raw.githubusercontent.com/hhoffstaette/kernel-patches/5.4/5.4/kconfig-20191211-enable-O3-for-all-arches.patch
		0002-mm-split-vmalloc_sync_all.patch::https://raw.githubusercontent.com/hhoffstaette/kernel-patches/5.4/5.4/mm-20191009-split-vmalloc_sync_all.patch
		0003-introduce-list-for-each-continue.patch::https://raw.githubusercontent.com/hhoffstaette/kernel-patches/5.4/5.4/"list-20191129-introduce-list_for_each_continue().patch"
		0004-block-perf-optimisations.patch
		0005-net-disable-tcp-ssthresh-cache.patch::https://raw.githubusercontent.com/hhoffstaette/kernel-patches/5.4/5.4/net-20191209-disable-TCP-ssthresh-metrics-cache-by-default.patch
)

validpgpkeys=(
  'ABAF11C65A2970B130ABE3C479BE3E4300411886'  # Linus Torvalds
  '647F28654894E3BD457199BE38DBBDC86092693E'  # Greg Kroah-Hartman
)

sha256sums=('92e9f1fd69543e9ce2a9e6eb918823b1846d2dd99246a74456263cd5ad234d89'
            'SKIP'
            'cb6362ca3ca8053b2ba0a55cf8c9634017357f57ce3ec97e125f60eb973c2581'
            '131cfc84d68d5db26e568590a510bdf8d61e911dee9a31737f8185e1578b7317'
            'a8172dee5d960e1b2fece8d535a3c49f54e0f8e3e2fb52dd5075e54f86ad617b'
            '04f4b1dabf507ebe5e7304a8cdcf490bc2c2620bb7d1e4244cbd4b18e0d6789f'
            '8f0ff11796e2495ddca1a45a38bbac13c87c1bf8d8e89f4bc495ca6993dad8f3'
            'ab010dc5ef6ce85d352956e5996d242246ecd0912b30f0b72025c38eadff8cd5'
            'c14f60f37c5ef16d104aaa05fdc470f8d6d341181f5370b92918c283728e5625'
            '6b305e46feb6741e3e2a07b8a55bb1bcb7b875949f278396dc55219549feb29e'
            '0556859a8168c8f7da9af8e2059d33216d9e5378d2cac70ca54c5ff843fa5add'
            '7a2758f86dd1339f0f1801de2dbea059b55bf3648e240878b11e6d6890d3089c'
            'c449d684f27a44c2368622b6f76abb960c03281218d4512969c567371a74afe0'
            '1801216e75c7fc6569be04bc134d8233b6cbaa02f96d5eb58f18429bef724683'
            'ddbc236dcd79174cbb73552453927062af2bb86a5ae97f2631445993be912845'
            '7fbf6328c7df3a98e409c12e66c9584ed57dd717328281d886739c1855e1a1e4'
            '96e9008ee0e1b305f1831116e76971a52d8c2447a212a9fc145098ce4e6f7773'
            'e96e8242e3d6a2fab780f016d0f00b2553d7067fb8a74ffa39c3ac6af55bfb58'
            '08e0197367e71466325d8b2110ec03c32f4ab086f05e13d4961d784df05e6c47'
            '8e538e60408ebfc98c4458f04362872b1ecaffa3143318f8b75c8c718d24fc1b'
            '0eab1c053ddc6e8d70b906bd66c3ce8c90abbfb0b79eb053dfdb3740be1194ad'
            'e42809933e33e6a12df61ca158af41141216a1bdd4c011a748724206faee69ca'
            '74fe306e22754d8488d5354b21233c087d3f7975fa88a8ff85f8a5e1d1ec6855'
            'fd1f34cf87e72ccd6070590028ad34e12dc42285637a0c61894680cb81d4fb88'
            '9660f0d31bdc5718b7fde41015898f67dce86602886585848d6300dfce2542db'
            'cd228e4b62cab5679c93cd0eda5d96d570f1b3ba84340eddd2d049f2a07eef9d'
            '88b5597753b01f90f77b99580943263969902ffc084972f8843e0659fdd5eb8f'
            '47d26eb8a2ec74b3684ab61837ecfcdad5cdc40722ca01a32684dfdd3775fafc'
            'b4a3d140bc93e4d224570c0f6b87c40c64148571588064858fcdc9f2406feeaa'
            '94b273be24a11dab3c77df0d3a061921d128bb57e78de87f3955049289110f81'
            '725d6693af00daf0a1e2fe8042249dfd16b90bb3f72e5cb841b9e4f7b82e4b7d'
            '58fd33be8d9ab594a01f1da5858567ac7ce8d3e44e0f2f3682e9104c4fb07514'
            '0d6fbf9a5206529d6791d41767ec254f0040d053713092b5fbb21fbe7f3604b7'
            'c6944879f5cdfd335a3adc75b6f6194d127ad93d4dd5bf90d2ad505e83c9b6d2'
            '607097f22f202cd829f12acce7a401fb7f7af5678ffeda90c1fc7da71b895ad7'
            '97f59d09ef55ea8a3634ea426fdc5db0591f77cca14cfe2db49176f71af80037'
            '21eac56173eb18959bbf02c1687dc7fa2c5d1df063ec90e6507f0008ce88bbef'
            '47844884e429ffc395f51610825271c2549d2ab28b52251407d5b4f8a21fe1d9'
            '7f9aa69187e7d197017c6bb15b623330e050a27ba384a3894cbd3e347fdd8a83'
            'b37b2132e97357201e039872c595da18aade6a64743d35ec33ebfd4d4851c3f4'
            '9c006e4845c22808c954ca2374a2a9dd927c192e4bdaf0d00c6abc559831106e')

export KBUILD_BUILD_USER=manjaro
export KBUILD_BUILD_HOST=systemd-run
_clang=0

if [[ ${_clang} -eq 1 ]]; then
	export HOSTCC='/opt/clang10/bin/clang --target=x86_64-unknown-linux-gnu'
	export HOSTLD=/opt/clang10/bin/ld.lld
	export HOSTAR=/opt/clang10/bin/llvm-ar
	export CC='/opt/clang10/bin/clang --target=x86_64-unknown-linux-gnu'
	export LD=/opt/clang10/bin/ld.lld
	export AR=/opt/clang10/bin/llvm-ar
	export AS=/opt/clang10/bin/llvm-as
	export OBJCOPY=/opt/clang10/bin/llvm-objcopy
	export OBJDUMP=/opt/clang10/bin/llvm-objdump
	export STRIP=/opt/clang10/bin/llvm-strip
	export NM=/opt/clang10/bin/llvm-nm
	export RANLIB=/opt/clang10/bin/llvm-ranlib
	CLANGOPTS="CC=/opt/clang10/bin/clang HOSTCC=/opt/clang10/bin/clang"
fi

prepare() {
  local TBOLD=$(tput bold)
  local TNORMAL=$(tput sgr0)
  cd "${srcdir}/linux-${pkgver}"

  # add latest fixes from stable queue, if needed
  # http://git.kernel.org/?p=linux/kernel/git/stable/stable-queue.git
  # enable only if you have "gen-stable-queue-patch.sh" executed before
  #patch -Np1 -i "${srcdir}/prepatch-${_basekernel}`date +%Y%m%d`"

  printf '\n'
  msg2 "APPLYING PATCHES"

  # apply patch from the source array (should be a pacman feature)
  local filename filename2
  for filename in "${source[@]}"; do
  	if [[ "$filename" =~ \.patch$ ]]; then
		filename="${filename%%::*}"
		filename2="${filename#*-}"
        	echo -e "\n---- Applying patch ${TBOLD}${filename2%%.*}${TNORMAL}:"
        	patch -Np1 -i "$srcdir/${filename}"
  	fi
  done

  # kernel config
  printf '\n'
  msg2 "KERNEL CONFIGURATION"
  local _config
  echo "---- Select configuration file:"
  echo "${TBOLD}1)${TNORMAL} Manjaro default"
  echo "${TBOLD}2)${TNORMAL} vd default"
  echo "${TBOLD}3)${TNORMAL} x570"
  echo "${TBOLD}4)${TNORMAL} x270"
  echo "${TBOLD}5)${TNORMAL} x200"
  while true ; do
  	read -p "Enter number (1-5): " _config
	  case ${_config} in
		1) cat ../config.x86_64 > ./.config && break ;;
		2) cat ../config.vd > ./.config && break ;;
		3) cat ../config.x570 > ./.config && break ;;
		4) cat ../config.x270 > ./.config && break ;;
		5) cat ../config.x200 > ./.config && break ;;
		*) echo "Please enter a number (1-5)!" && continue ;;
  	  esac
  done

  # add key
  printf '\n'
  msg2 "KERNEL KEY GENERATION"
  read -p "---- Enter the full path to the key if you have one, else enter 'n': " UCHOICE
  if [[ ${UCHOICE} != "n" ]]; then
    if [[ -f ${UCHOICE} ]]; then
      cat ${UCHOICE} > ./certs/vd54-kernel-key.pem || exit 2
    else
      echo "Path does not exist. Aborting..." ; exit 2
    fi
  else
	cat ../x509.genkey > ./certs/x509.genkey
    sed -i 's/vd54\-kernel\-key/signing\_key/' ./.config || exit 2
  fi

  if [ "${_kernelname}" != "" ]; then
    sed -i "s|CONFIG_LOCALVERSION=.*|CONFIG_LOCALVERSION=\"${_kernelname}\"|g" ./.config
    sed -i "s|CONFIG_LOCALVERSION_AUTO=.*|CONFIG_LOCALVERSION_AUTO=n|" ./.config
  fi

  # set patchlevel to 4
  #sed -ri "s|^(PATCHLEVEL =).*|\1 4|" Makefile

  # set extraversion to pkgrel
  sed -ri "s|^(EXTRAVERSION =).*|\1 -${pkgrel}|" Makefile

  # don't run depmod on 'make install'. We'll do this ourselves in packaging
  #sed -i '2iexit 0' scripts/depmod.sh

  # get kernel version
  make $CLANGOPTS prepare
  make $CLANGOPTS -s kernelrelease > version
  printf '\n'
  msg2 "Prepared %s version %s" "$pkgbase" "$(<version)"
  read -p "---- Enter 'y' for nconfig: " NCONFIG
  [[ $NCONFIG = "y" ]] && make $CLANGOPTS nconfig

  # rewrite configuration
  yes "" | make $CLANGOPTS config >/dev/null
}

build() {
  cd "${srcdir}/linux-${pkgver}"

  # build!
  make $CLANGOPTS ${MAKEFLAGS} LOCALVERSION= bzImage modules
}

package_linux54-vd() {
  pkgdesc="The ${pkgbase/linux/Linux} vd kernel and modules"
  depends=('coreutils' 'linux-firmware' 'kmod' 'mkinitcpio>=27')
  optdepends=('crda: to set the correct wireless channels of your country')
  provides=("linux=${pkgver}")

  cd "${srcdir}/linux-${pkgver}"

  local kernver="$(<version)"
  local modulesdir="$pkgdir/usr/lib/modules/$kernver"

  mkdir -p "${pkgdir}"/{boot,usr/lib/modules}

  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make $CLANGOPTS -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "${pkgbase}" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"
  echo "${kernelbase}-${CARCH}" | install -Dm644 /dev/stdin "$modulesdir/kernelbase"

  # add kernel version
  echo "${pkgver}-${pkgrel}${_kernelname} x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  # make room for external modules
  local _extramodules="extramodules-${kernelbase}"
  ln -s "../${_extramodules}" "$modulesdir/extramodules"

  # add real version for building modules and running depmod from hook
  echo "${kernver}" |
    install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_extramodules}/version"

  # now we call depmod...
  #printf '\n'
  #msg2 "Running depmod..."
  #depmod -v -b "${pkgdir}/usr" -F System.map "$kernver"

  printf '\n'
  msg2 "Installing modules..."
  make $CLANGOPTS ${MAKEFLAGS} LOCALVERSION= INSTALL_MOD_PATH="${pkgdir}/usr" modules_install

  # remove build and source links
  rm $modulesdir/source
  rm $modulesdir/build
  [[ -f ./certs/vd54-kernel-key.pem ]] && rm ./certs/vd54-kernel-key.pem

  # Fixing permissions
  printf '\n'
  msg2 "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "$pkgdir"

  # add mkinitcpio preset (not strictly needed)
  install -Dm644 "$srcdir/${pkgbase}.preset" "$pkgdir/etc/mkinitcpio.d/${pkgbase}.preset"
}

package_linux54-vd-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} vd kernel"
  provides=("linux-headers=$pkgver")

  cd "${srcdir}/linux-${pkgver}"
  local kernver="$(<version)"
  local _builddir="${pkgdir}/usr/lib/modules/${kernver}/build"

  printf '\n'
  msg2 "Installing headers..."
  install -Dt "${_builddir}" -m644 Makefile .config Module.symvers System.map version vmlinux || exit 32
  install -Dt "${_builddir}/kernel" -m644 kernel/Makefile
  install -Dt "${_builddir}/arch/x86" -m644 "arch/x86/Makefile"
  mkdir "${_builddir}/.tmp_versions"

  cp -t "${_builddir}" -a include scripts

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "${_builddir}/tools/objtool" tools/objtool/objtool

  # add xfs and shmem for aufs building
  mkdir -p "${_builddir}"/{fs/xfs,mm}

  cp -t "${_builddir}/arch/x86" -a "arch/x86/include"
  install -Dt "${_builddir}/arch/x86/kernel" -m644 "arch/x86/kernel/asm-offsets.s"
  #install -Dt "${_builddir}/arch/${KARCH}/kernel" -m644 "arch/${KARCH}/kernel/macros.s"

  install -Dt "${_builddir}/drivers/md" -m644 drivers/md/*.h
  install -Dt "${_builddir}/net/mac80211" -m644 net/mac80211/*.h

  # http://bugs.archlinux.org/task/13146
  install -Dt "${_builddir}/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # http://bugs.archlinux.org/task/20402
  install -Dt "${_builddir}/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "${_builddir}/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "${_builddir}/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # copy in Kconfig files
  find . -name 'Kconfig*' -exec install -Dm644 {} "${_builddir}/{}" \;

  # remove unneeded stuff
  printf '\n'
  msg2 "Removing unneeded files..."
  # remove unneeded architectures
  local _arch
  for _arch in "${_builddir}"/arch/*/; do
    [[ ${_arch} == */x86/ ]] && continue
    rm -r "${_arch}"
  done

  # remove files already in linux-docs package
  rm -r "${_builddir}/Documentation"

  # remove broken symlinks
  find -L "${_builddir}" -type l -printf 'Removing %P\n' -delete

  # remove loose objects"
  find "${_builddir}" -type f -name '*.o' -printf 'Removing %P\n' -delete

  # strip scripts directory
  printf '\n'
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
  done < <(find "${_builddir}" -type f -perm -u+x ! -name vmlinux -print0)

  # Fix permissions
  printf '\n'
  msg2 "Fixing permissions..."
  chmod -Rc u=rwX,go=rX "${pkgdir}"
}

