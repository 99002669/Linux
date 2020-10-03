Practise1: working with directories

1. Display your current directory.
	pwd
	Current directory: /bin
     
     
2. Change to the /etc directory.
	cd /etc


3. Now change to your home directory using only three key presses.
	cd


4. Change to the /boot/grub directory using only eleven key presses.
	cd /boot/grub (use tab to complete the path)


5. Go to the parent directory of the current directory.
	cd ..


6. Go to the root directory.
	cd /


7. List the contents of the root directory.
	ls


8. List a long listing of the root directory.
	ls -l


9. Stay where you are, and list the contents of /etc.
	ls -l /etc


10. Stay where you are, and list the contents of /bin and /sbin.
	ls /bin /sbin


11. Stay where you are, and list the contents of ~.
	ls ~


12. List all the files (including hidden files) in your home directory.
	ls -a  (-a list all the files)


13. List the files in /boot in a human readable format.
	ls -h /boot  (-h lists in human readable format)


14. Create a directory testdir in your home directory.
	mkdir ~/testdir


15. Change to the /etc directory, stay here and create a directory newdir in your home directory.
	cd /etc 
	mkdir ~/newdir
	
		
16. Create in one command the directories ~/dir1/dir2/dir3 (dir3 is a subdirectory from dir2,and dir2 is a subdirectory from dir1 ).
	mkdir -p ~/dir1/dir2/dir3 (-p to create parent directory in this case dir1/dir2q)


17. Remove the directory testdir.
	rmdir testdir


18. Open manual page for bash and read about pushd and popd by searching in manpage.
	man bash
	To find in man pages: /<wordtobesearched>
	TO navigate through the search results: n


