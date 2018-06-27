# Thanks to Earnestly
pkgbase=system-config
pkgname=(base-config optimus-intel-config optimus-nvidia-config)
pkgver=1.0
pkgrel=1

pkgdesc='System Configurations'
arch=('any')
license=('custom')

source=('etc-locale.conf'
        'pacman-nvidia.hook'
        'sysctl-swappiness.conf'
        'mod-i915.conf'
        'disable-nvidia.conf'
        'bbswitch.conf'
        'bbswitch-early.conf')


package_base-config() {
    pkgdesc='Common System Configuration'
    depends=('nvidia')

    install -Dm0644 "$srcdir"/pacman-nvidia.hook "$pkgdir"/etc/pacman.d/hooks/nvidia.hook
    install -Dm0644 "$srcdir"/etc-locale.conf "$pkgdir"/etc/locale.conf
    install -Dm0644 "$srcdir"/sysctl-swappiness.conf "$pkgdir"/etc/sysctl.d/99-swappiness.conf

    ln -sf /usr/share/zoneinfo/Asia/Kolkata "$pkgdir"/etc/localtime
}

package_optimus-intel-config() {
    pkgdesc='Run Intel-GPU disabling nvidia.'
    depends=('base-config' 'gdm')

    install -Dm0644 "$srcdir"/mod-i915.conf "$pkgdir"/etc/modprobe.d/i915.conf
    install -Dm0644 "$srcdir"/bbswitch.conf "$pkgdir"/etc/modprobe.d/bbswitch.conf
    install -Dm0644 "$srcdir"/bbswitch-early.conf "$pkgdir"/etc/modules-load.d/bbswitch.conf
    install -Dm0644 "$srcdir"/disable-nvidia.conf "$pkgdir"/etc/modprobe.d/disable-nvidia.conf
}

package_optimus-nvidia-config() {
    pkgdesc='Run Nvidia-GPU'
    depends=('base-config')
    conflicts=('optimus-intel-config')
}

sha256sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP')
