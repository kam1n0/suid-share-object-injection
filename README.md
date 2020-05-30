# suid-share-object-injection
*Credit to Tib3rius* | https://tryhackme.com/room/linuxprivesc

* Find all the SUID/SGID executables on the linux machine

link suid

* If suid-so appears in the results, it is potentially vulnerable to *shared object injection*

1. Execute the file and note that currently it displays a progress bar before exiting:

link suid-so

2. Run *strace* on the file and search the output for open/access calls and "no such file" errors:

link strace

3. Create the .config directory for the libcacl.c file

link libcacl

4. Compile the libcalc.c file into a shared object at the location the 'suid-so' executable was looking for (/home/user/.config):

link gcc

5. Execute the suid-so executable again, and note that this time, instead of a progress bar, we get a root shell:

link execute
