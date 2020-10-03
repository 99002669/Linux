Practise2: Working with files

1. List the files in the /bin directory
	ls /bin


2. Display the type of file of /bin/cat, /etc/passwd and /usr/bin/passwd.
	file /bin/cat /etc/passwd /usr/bin/passwd


3. Use files LFS.png dummy.pdf 
3a. Display the type of file of wolf.jpg and dummy.pdf
	file wolf.jpg dummy.pdf


3b. Rename LFS.png to wolf.pdf 
	mv LFS.png wolf.pdf


3c. Display the type of file of wolf.pdf and dummy.pdf.
	file wolf.pdf dummy.pdf


4. Create a directory ~/touched and enter it.
	mkdir ~/touched 
	cd ~/touched
				
		
5. Create the files today.txt and yesterday.txt in touched.
	touch today.txt yesterday.txt


6. Change the date on yesterday.txt to match yesterday's date.
	touch -t 202009291830 yesterday.txt


7. Copy yesterday.txt to copy.yesterday.txt 
	cp yesterday.txt copy.yesterday.txt


8. Rename copy.yesterday.txt to kim
	mv copy.yesterday.txt kim


9. Create a directory called ~/testbackup and copy all files from ~/touched into it.
	mkdir ~/testbackup 
	cp -r ~/touched ~/testbackup/ 


10. Use one command to remove the directory ~/testbackup and all files in it.
	rm -rf ~/testbackup 


11. Create a directory ~/etcbackup and copy all *.conf files from /etc into it. Did you include all subdirectories of /etc ?
	mkdir ~/etcbackup
	cp /etc/*.conf ~/etcbackup
	No, the subdirectories are not included.


12. Use rename to rename all *.conf files to *.backup .
	rename 's/conf/backup/' *.conf
		
