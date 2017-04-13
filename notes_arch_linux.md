# ArchLinux Cheat Sheet

### Network configuration

* ##### List network devices
		# ip link

* ##### Enabling and disabling network interfaces
    	# ip link set <network interface> up
    	# ip link set <network interface> down

* ##### To check the result:
    	# ip link show dev <network interface>

* ##### Start the DHCP service :
    	# systemctl start dhcpcd@<network interface>.service

* ##### Enable DHCP service to be started on bootup:
    	# systemctl enable dhcpcd@<network interface>.service

* ##### Install and start Network File System (NFS) :


		# pacman -S nfs-utils
		# systemctl start nfs-server.service
		# systemctl enable nfs-server.service


### Manage packages with pacman

* ##### Install a new package
		# pacman -S <package name>

* ##### Update all package
		# pacman -Syu

* ##### Remove all the cached packages that are not currently installed
		# pacman -Sc

* ##### Recursively removing orphans packages and their configuration files
		# pacman -Rns $(pacman -Qtdq)

### System and service manager : systemd

Arch Linux uses systemd as the init process.

* ##### List running units
		# systemctl

* ##### **Start** a unit immediately
		# systemctl start <unit>

* ##### **Stop** a unit immediately
		# systemctl stop <unit>

* ##### **Restart** a unit
		# systemctl restart <unit>

* ##### **Reload** configuration
		# systemctl reload <unit>

* ##### Show the **status** of a unit
		$ systemctl status <unit>

* ##### Check whether a unit is already **enabled** or not
		$ systemctl is-enabled <unit>

* ##### Enable a unit to be **started on bootup**
		# systemctl enable <unit>

* ##### Disable a unit to **not start during bootup**
		# systemctl disable <unit>

* ##### Check if any systemd services have entered in a failed state
		# systemctl --failed

### Miscellaneous

* ##### Kernel warning : "intel_rapl : no valid rapl domains found in package 0"

  Create and edit `/etc/modprobe.d/blacklist.conf` file with :

  		blacklist intel_rapl

* ##### Add an user
    	# useradd -m -G users -s /bin/bash <username>

* ##### Kernel warning : "ACPI : No IRQ available for PCI Interrupt Link [LNKS]. Try pci=noa"

  * Open `/boot/grub/grub.cfg`
  * In the `Arch Linux` entry menu, find the line beginning with `linux`
  * At the end of this line add

    		acpi=noirq
  * Example :

    		linux   /vmlinuz-linux root=UUID=a590453b-f844-4cf5-a74f-66a945eb2434 rw  quiet acpi=noirq

  To test this change before on a temporary grub.cfg modification, type `e` on menu entry in the boot loader to enter in edit mode.

* ##### Show boot log
    	journalctl -b

* ##### Enable SSH service to be started on bootup:
		systemctl enable sshd.service

[General recommendations](https://wiki.archlinux.org/index.php/General_recommendations)

[System maintenance](https://wiki.archlinux.org/index.php/System_maintenance#Avoid_certain_pacman_commands)



pacman -S samba gvfs gvfs-smb sshfs
