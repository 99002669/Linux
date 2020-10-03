Practise4: File system

1. Does the file /bin/cat exist ? What about /bin/dd and /bin/echo. What is the type of these files ?
	genesis69@Trainee:~$ ls /bin/cat
	/bin/cat
	genesis69@Trainee:~$ file /bin/cat
	/bin/cat: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=b357ed53c8c9cb1a312f83b28982304effae0135, for GNU/Linux 3.2.0, stripped
	genesis69@Trainee:~/Desktop$ ls /bin/dd
	/bin/dd
	genesisv69Trainee:~/Desktop$ file /bin/dd
	/bin/dd: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=415fdfff0feef61ab564741f44c4aa57cd1f8c1e, for GNU/Linux 3.2.0, stripped
	genesis69@Trainee:~/Desktop$ ls /bin/echo
	/bin/echo
	genesis69@Trainee:~/Desktop$ file /bin/echo
	/bin/echo: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=714b557112010bbcd04b0e5e6efc1b106166733c, for GNU/Linux 3.2.0, stripped


2. What is the size of the Linux kernel file(s) (vmlinu*) in /boot ?
	genesis69@Trainee:~$ ls -lh /boot/vm*
	lrwxrwxrwx 1 root root  24 Sep 22 12:19 /boot/vmlinuz -> vmlinuz-5.4.0-48-generic
	-rw-r--r-- 1 root root 12M Apr 23 18:48 /boot/vmlinuz-5.4.0-26-generic
	-rw------- 1 root root 12M Sep 10 16:06 /boot/vmlinuz-5.4.0-48-generic
	lrwxrwxrwx 1 root root  24 Sep 22 12:19 /boot/vmlinuz.old -> vmlinuz-5.4.0-26-generic


3. Create a directory ~/test. Then issue the following commands:
cd ~/test
dd if=/dev/zero of=zeroes.txt count=1 bs=100
od zeroes.txt
What is Happening? Can you describe the functionality of dd, od, /dev/zero ?
	genesis69@Trainee:~$ mkdir ~/test
	genesis69@Trainee:~$ ls
	build    Documents  Music        Pictures  snap       test
	Desktop  Downloads  permissions  Public    Templates  Videos
	genesis69@Trainee:~$ cd ~/test
	genesis69@Trainee:~/test$ dd if=/dev/zero of=zeroes.txt count=1 bs=100
	1+0 records in
	1+0 records out
	100 bytes copied, 0.000179526 s, 557 kB/s
	genesis69@Trainee:~/test$ od zeroes.txt
	0000000 000000 000000 000000 000000 000000 000000 000000 000000
	*
	0000140 000000 000000
	0000144
	dd will copy one times (count=1) a block of size 100 bytes (bs=100) from the file /dev/zero to ~/test/zeroes.txt and od - dump files in octal and other formats. /dev/zero is a Linux special device. It can be considered a source of zeroes. You cannot send something to /dev/zero, but you can read zeroes from it.


4. Now issue the following command:
dd if=/dev/random of=random.txt count=1 bs=100 ; od random.txt
Can you describe the functionality of /dev/random?
	genesis69@Trainee:~/test$ dd if=/dev/random of=random.txt count=1 bs=100 ; od random.txt
	1+0 records in
	1+0 records out
	100 bytes copied, 0.000226939 s, 441 kB/s
	0000000 000110 100443 150166 064654 134572 110222 073420 023623
	0000020 140575 146303 015225 114420 004137 062733 041622 150221
	0000040 150024 001704 110556 144032 123575 116250 042014 045055
	0000060 046775 153651 157637 170350 063166 046715 125760 056103
	0000100 013167 127245 020251 016522 113141 000130 053203 133551
	0000120 074701 060043 116453 007024 032571 104641 077222 177704
	0000140 007040 071125
	0000144
	/dev/random acts as a random number generator on your Linux machine.


5. Issue the following two commands, and look at the first character of each output line.
ls -l /dev/sd* /dev/hd*
ls -l /dev/tty* /dev/input/mou*
Can you tell the difference between block and character devices ?
	genesis69@Trainee:~$ ls -l /dev/sd* /dev/hd*
	ls: cannot access '/dev/hd*': No such file or directory
	brw-rw---- 1 root disk 8, 0 Oct  1 08:19  /dev/sda
	brw-rw---- 1 root disk 8, 1 Oct  1 08:20  /dev/sda1
	brw-rw---- 1 root disk 8, 2 Oct  1 08:20  /dev/sda2
	brw-rw---- 1 root disk 8, 3 Oct  1 08:20  /dev/sda3
	brw-rw---- 1 root disk 8, 4 Oct  1 08:20  /dev/sda4
	brw-rw---- 1 root disk 8, 5 Oct  1 08:20  /dev/sda5
	genesis69@Trainee:~$ ls -l /dev/tty* /dev/input/mou*
	crw-rw---- 1 root      input   13, 32 Oct  1 08:19 /dev/input/mouse0
	crw-rw-rw- 1 root      tty      5,  0 Oct  1 08:19 /dev/tty
	crw--w---- 1 root      tty      4,  0 Oct  1 08:19 /dev/tty0
	crw--w---- 1 root      tty      4,  1 Oct  1 08:20 /dev/tty1
	crw--w---- 1 root      tty      4, 10 Oct  1 08:19 /dev/tty10
	crw--w---- 1 root      tty      4, 11 Oct  1 08:19 /dev/tty11
	crw--w---- 1 root      tty      4, 12 Oct  1 08:19 /dev/tty12
	crw--w---- 1 root      tty      4, 13 Oct  1 08:19 /dev/tty13
	crw--w---- 1 root      tty      4, 14 Oct  1 08:19 /dev/tty14
	crw--w---- 1 root      tty      4, 15 Oct  1 08:19 /dev/tty15
	crw--w---- 1 root      tty      4, 16 Oct  1 08:19 /dev/tty16
	crw--w---- 1 root      tty      4, 17 Oct  1 08:19 /dev/tty17
	crw--w---- 1 root      tty      4, 18 Oct  1 08:19 /dev/tty18
	crw--w---- 1 root      tty      4, 19 Oct  1 08:19 /dev/tty19
	crw--w---- 1 genesis69 tty      4,  2 Oct  1 08:20 /dev/tty2
	crw--w---- 1 root      tty      4, 20 Oct  1 08:19 /dev/tty20
	crw--w---- 1 root      tty      4, 21 Oct  1 08:19 /dev/tty21
	crw--w---- 1 root      tty      4, 22 Oct  1 08:19 /dev/tty22
	crw--w---- 1 root      tty      4, 23 Oct  1 08:19 /dev/tty23
	crw--w---- 1 root      tty      4, 24 Oct  1 08:19 /dev/tty24
	crw--w---- 1 root      tty      4, 25 Oct  1 08:19 /dev/tty25
	crw--w---- 1 root      tty      4, 26 Oct  1 08:19 /dev/tty26
	crw--w---- 1 root      tty      4, 27 Oct  1 08:19 /dev/tty27
	crw--w---- 1 root      tty      4, 28 Oct  1 08:19 /dev/tty28
	crw--w---- 1 root      tty      4, 29 Oct  1 08:19 /dev/tty29
	crw--w---- 1 root      tty      4,  3 Oct  1 08:20 /dev/tty3
	crw--w---- 1 root      tty      4, 30 Oct  1 08:19 /dev/tty30
	crw--w---- 1 root      tty      4, 31 Oct  1 08:19 /dev/tty31
	crw--w---- 1 root      tty      4, 32 Oct  1 08:19 /dev/tty32
	crw--w---- 1 root      tty      4, 33 Oct  1 08:19 /dev/tty33
	crw--w---- 1 root      tty      4, 34 Oct  1 08:19 /dev/tty34
	crw--w---- 1 root      tty      4, 35 Oct  1 08:19 /dev/tty35
	crw--w---- 1 root      tty      4, 36 Oct  1 08:19 /dev/tty36
	crw--w---- 1 root      tty      4, 37 Oct  1 08:19 /dev/tty37
	crw--w---- 1 root      tty      4, 38 Oct  1 08:19 /dev/tty38
	crw--w---- 1 root      tty      4, 39 Oct  1 08:19 /dev/tty39
	crw--w---- 1 root      tty      4,  4 Oct  1 08:20 /dev/tty4
	crw--w---- 1 root      tty      4, 40 Oct  1 08:19 /dev/tty40
	crw--w---- 1 root      tty      4, 41 Oct  1 08:19 /dev/tty41
	crw--w---- 1 root      tty      4, 42 Oct  1 08:19 /dev/tty42
	crw--w---- 1 root      tty      4, 43 Oct  1 08:19 /dev/tty43
	crw--w---- 1 root      tty      4, 44 Oct  1 08:19 /dev/tty44
	crw--w---- 1 root      tty      4, 45 Oct  1 08:19 /dev/tty45
	crw--w---- 1 root      tty      4, 46 Oct  1 08:19 /dev/tty46
	crw--w---- 1 root      tty      4, 47 Oct  1 08:19 /dev/tty47
	crw--w---- 1 root      tty      4, 48 Oct  1 08:19 /dev/tty48
	crw--w---- 1 root      tty      4, 49 Oct  1 08:19 /dev/tty49
	crw--w---- 1 root      tty      4,  5 Oct  1 08:20 /dev/tty5
	crw--w---- 1 root      tty      4, 50 Oct  1 08:19 /dev/tty50
	crw--w---- 1 root      tty      4, 51 Oct  1 08:19 /dev/tty51
	crw--w---- 1 root      tty      4, 52 Oct  1 08:19 /dev/tty52
	crw--w---- 1 root      tty      4, 53 Oct  1 08:19 /dev/tty53
	crw--w---- 1 root      tty      4, 54 Oct  1 08:19 /dev/tty54
	crw--w---- 1 root      tty      4, 55 Oct  1 08:19 /dev/tty55
	crw--w---- 1 root      tty      4, 56 Oct  1 08:19 /dev/tty56
	crw--w---- 1 root      tty      4, 57 Oct  1 08:19 /dev/tty57
	crw--w---- 1 root      tty      4, 58 Oct  1 08:19 /dev/tty58
	crw--w---- 1 root      tty      4, 59 Oct  1 08:19 /dev/tty59
	crw--w---- 1 root      tty      4,  6 Oct  1 08:20 /dev/tty6
	crw--w---- 1 root      tty      4, 60 Oct  1 08:19 /dev/tty60
	crw--w---- 1 root      tty      4, 61 Oct  1 08:19 /dev/tty61
	crw--w---- 1 root      tty      4, 62 Oct  1 08:19 /dev/tty62
	crw--w---- 1 root      tty      4, 63 Oct  1 08:19 /dev/tty63
	crw--w---- 1 root      tty      4,  7 Oct  1 08:19 /dev/tty7
	crw--w---- 1 root      tty      4,  8 Oct  1 08:19 /dev/tty8
	crw--w---- 1 root      tty      4,  9 Oct  1 08:19 /dev/tty9
	crw------- 1 root      root     5,  3 Oct  1 08:19 /dev/ttyprintk
	crw-rw---- 1 root      dialout  4, 64 Oct  1 08:19 /dev/ttyS0
	crw-rw---- 1 root      dialout  4, 65 Oct  1 08:19 /dev/ttyS1
	crw-rw---- 1 root      dialout  4, 74 Oct  1 08:19 /dev/ttyS10
	crw-rw---- 1 root      dialout  4, 75 Oct  1 08:19 /dev/ttyS11
	crw-rw---- 1 root      dialout  4, 76 Oct  1 08:19 /dev/ttyS12
	crw-rw---- 1 root      dialout  4, 77 Oct  1 08:19 /dev/ttyS13
	crw-rw---- 1 root      dialout  4, 78 Oct  1 08:19 /dev/ttyS14
	crw-rw---- 1 root      dialout  4, 79 Oct  1 08:19 /dev/ttyS15
	crw-rw---- 1 root      dialout  4, 80 Oct  1 08:19 /dev/ttyS16
	crw-rw---- 1 root      dialout  4, 81 Oct  1 08:19 /dev/ttyS17
	crw-rw---- 1 root      dialout  4, 82 Oct  1 08:19 /dev/ttyS18
	crw-rw---- 1 root      dialout  4, 83 Oct  1 08:19 /dev/ttyS19
	crw-rw---- 1 root      dialout  4, 66 Oct  1 08:19 /dev/ttyS2
	crw-rw---- 1 root      dialout  4, 84 Oct  1 08:19 /dev/ttyS20
	crw-rw---- 1 root      dialout  4, 85 Oct  1 08:19 /dev/ttyS21
	crw-rw---- 1 root      dialout  4, 86 Oct  1 08:19 /dev/ttyS22
	crw-rw---- 1 root      dialout  4, 87 Oct  1 08:19 /dev/ttyS23
	crw-rw---- 1 root      dialout  4, 88 Oct  1 08:19 /dev/ttyS24
	crw-rw---- 1 root      dialout  4, 89 Oct  1 08:19 /dev/ttyS25
	crw-rw---- 1 root      dialout  4, 90 Oct  1 08:19 /dev/ttyS26
	crw-rw---- 1 root      dialout  4, 91 Oct  1 08:19 /dev/ttyS27
	crw-rw---- 1 root      dialout  4, 92 Oct  1 08:19 /dev/ttyS28
	crw-rw---- 1 root      dialout  4, 93 Oct  1 08:19 /dev/ttyS29
	crw-rw---- 1 root      dialout  4, 67 Oct  1 08:19 /dev/ttyS3
	crw-rw---- 1 root      dialout  4, 94 Oct  1 08:19 /dev/ttyS30
	crw-rw---- 1 root      dialout  4, 95 Oct  1 08:19 /dev/ttyS31
	crw-rw---- 1 root      dialout  4, 68 Oct  1 08:19 /dev/ttyS4
	crw-rw---- 1 root      dialout  4, 69 Oct  1 08:19 /dev/ttyS5
	crw-rw---- 1 root      dialout  4, 70 Oct  1 08:19 /dev/ttyS6
	crw-rw---- 1 root      dialout  4, 71 Oct  1 08:19 /dev/ttyS7
	crw-rw---- 1 root      dialout  4, 72 Oct  1 08:19 /dev/ttyS8
	crw-rw---- 1 root      dialout  4, 73 Oct  1 08:19 /dev/ttyS9

	The first ls will show block(b) devices, the second ls shows character(c) devices. Block devices are always written to (or read from) in blocks. For hard disks, blocks of 512 bytes are common. Character devices act as a stream of characters (or bytes). Mouse and keyboard are typical character devices.


6. Use cat to display /etc/hosts and /etc/resolv.conf. What is your idea about the purpose of these files ?
	genesis69@Trainee:~$ cat /etc/hosts
	127.0.0.1	localhost
	127.0.1.1	Trainee	
	# The following lines are desirable for IPv6 capable hosts
	::1     ip6-localhost ip6-loopback
	fe00::0 ip6-localnet
	ff00::0 ip6-mcastprefix
	ff02::1 ip6-allnodes
	ff02::2 ip6-allrouters
	genesis69@Trainee:~$ cat /etc/resolv.conf
	# This file is managed by man:systemd-resolved(8). Do not edit.
	#
	# This is a dynamic resolv.conf file for connecting local clients to the
	# internal DNS stub resolver of systemd-resolved. This file lists all
	# configured search domains.
	#
	# Run "resolvectl status" to see details about the uplink DNS servers
	# currently in use.
	#
	# Third party programs must not access this file directly, but only through the
	# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
	# replace this symlink by a static file or a different symlink.
	#
	# See man:systemd-resolved.service(8) for details about the supported modes of
	# operation for /etc/resolv.conf.
	
	nameserver 127.0.0.53
	options edns0
	search GUEST.local
	
	/etc/hosts contains hostnames with their ip address. And /etc/resolv.conf should contain the ip address of a DNS name server.

	
7. Are there any files in /etc/skel/ ? Check also for hidden files.
	genesis69@Trainee:~$ ls -al /etc/skel/
	total 28
	drwxr-xr-x   2 root root  4096 Sep 22 12:28 .
	drwxr-xr-x 136 root root 12288 Oct  1 08:34 ..
	-rw-r--r--   1 root root   220 Feb 25  2020 .bash_logout
	-rw-r--r--   1 root root  3771 Feb 25  2020 .bashrc
	-rw-r--r--   1 root root   807 Feb 25  2020 .profile

	Yes, there should be hidden files there.


8. Display /proc/cpuinfo. On what architecture is your Linux running ?
	The file should contain at least one line with Intel or other cpu.


9. Display /proc/interrupts. What is the size of this file ? Where is this file stored ?
	The size is zero, yet the file contains data. It is not stored anywhere because /proc is a virtual file system that allows you to talk with the kernel.

	
10. Can you enter the /root directory ? Are there (hidden) files ?
	genesis69@Trainee:~$ cd /root
	bash: cd: /root: Permission denied
	The /root directory is not accessible for normal users on most modern Linux systems.


11. Are ifconfig, fdisk, parted, shutdown and grub-install present in /sbin ? Why are these binaries in /sbin and not in /bin ?
	Yes. Because those files are only meant for system administrators.


12. Is /var/log a file or a directory ? What about /var/spool ?
	Both are directories.


13. Open two command prompts (Ctrl-Shift-T in gnome-terminal) or terminals (Ctrl-Alt-F1,Ctrl-Alt-F2, ...) and issue the who am i in both. Then try to echo a word from one terminal to the other.
	genesis69@Trainee:~$ whoami
	genesis69
	genesis69@Trainee:~/Desktop$ whoami
	genesis69
	genesis69@Trainee:~$ tty
	/dev/pts/0
	genesis69@Trainee:~/Desktop$ tty
	/dev/pts/1
	genesis69@Trainee:~$ echo "Hello" > /dev/pts/1
	genesis69@Trainee:~/Desktop$ Hello


14. Read the man page of random and explain the difference between /dev/random and /dev/urandom.
	man 4 random
	The file /dev/random has major device number 1 and minor device number 8.  The file /dev/urandom has major device  number 1 and minor device number 9. The /dev/random interface is  considered  a  legacy  interface, and /dev/urandom  is preferred and sufficient in all use cases, with the exception of applications which require randomness during early boot time.


