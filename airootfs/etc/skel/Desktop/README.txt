RUN ALL COMMANDS IN TERMINAL

###########################
###   Fixing Pacman     ###
###########################
	sudo haveged -w 1024
	sudo pacman-key --init && sudo pacman-key --populate archlinux
	sudo pacman-key --init && sudo pacman-key --populate archlinux && sudo pacman-key --refresh-keys
	sudo pkill haveged
	sudo psync
	sudo pacman -Syyu

###########################
###   Mirror + Clean    ###
###########################
	sudo updatedb
	sudo cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.backup
**	sudo reflector -c 'Germany' -f 6 -l 6 -p http -n 12 --save /etc/pacman.d/mirrorlist
	sudo yaourt -Syyau
	pacu
	post-clean
	sudo pacman -Rs $(pacman -Qq | grep \^xf86-video-)
	sudo reboot


###########################
###   Tor Install Fix   ###
###########################
	gpg --keyserver pool.sks-keyservers.net --recv-keys 2E1AC68ED40814E0

--------------------------------------------------------------------------------------------------------


**	Change Germany to the country mirror closest to you ( keep the ' ' )