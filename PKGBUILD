# Maintainer: Aditya Shakya <adi1090x@gmail.com>

pkgname=archcraft-blackbox
pkgver=1.0
pkgrel=0
pkgdesc="Blackbox Configurations for Archcraft"
url="https://github.com/archcraft-os/archcraft-blackbox"
arch=('any')
license=('GPL3')
makedepends=('git')
depends=('blackbox' 'sxhkd'
		'alacritty' 'thunar' 'geany'
		'rofi' 'dunst'
		'mpd' 'mpc'
		'maim' 'xclip' 'viewnior'
		'ksuperkey' 
		'betterlockscreen'
		'xfce4-power-manager' 
		'xsettingsd'
		'hsetroot'
		'acpi'
		'networkmanager'
		'wmname'
		'pulsemixer' 'light' 'xcolor'
)
conflicts=()
provides=("${pkgname}")
options=(!strip !emptydirs)
install="${pkgname}.install"

prepare() {
	cp -af ../files/. ${srcdir}
}

package() {
	local _config=${pkgdir}/etc/skel/.blackbox
	mkdir -p "$_config"

	# Copy blackbox config files
	cp -r ${srcdir}/alacritty 		"$_config"
	cp -r ${srcdir}/scripts 		"$_config"
	cp -r ${srcdir}/styles 			"$_config"
	cp -r ${srcdir}/theme 			"$_config"

	chmod +x "$_config"/scripts/*
	chmod +x "$_config"/theme/polybar.sh
	chmod +x "$_config"/theme/polybar/launch.sh
	chmod +x "$_config"/theme/polybar/scripts/bluetooth.sh

	install -Dm 644 dunstrc   				"$_config"/dunstrc
	install -Dm 644 menu   					"$_config"/menu
	install -Dm 644 picom.conf   			"$_config"/picom.conf
	install -Dm 644 picom-ibhagwan.conf   	"$_config"/picom-ibhagwan.conf
	install -Dm 644 picom-jonaburg.conf   	"$_config"/picom-jonaburg.conf
	install -Dm 644 picom-original.conf   	"$_config"/picom-original.conf
	install -Dm 644 sxhkdrc   				"$_config"/sxhkdrc
	install -Dm 644 xsettingsd   			"$_config"/xsettingsd

	install -Dm 644 .blackboxrc   			${pkgdir}/etc/skel/.blackboxrc

	install -Dm 755 run-blackbox   			${pkgdir}/usr/local/bin/run-blackbox
	install -Dm 644 blackbox.desktop   		${pkgdir}/usr/share/xsessions/blackbox.desktop
}
