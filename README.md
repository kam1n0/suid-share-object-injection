# suid-share-object-injection
*Credit to Tib3rius* | https://tryhackme.com/room/linuxprivesc

* Find all the SUID/SGID executables on the linux machine

[![Image of suid](https://github.com/kam1n0/suid-share-object-injection/blob/master/tmp_upload/suid.png)](#)

* If suid-so appears in the results, it is potentially vulnerable to *shared object injection*

1. Execute the file and note that currently it displays a progress bar before exiting:

[![Image of suid-so](https://github.com/kam1n0/suid-share-object-injection/blob/master/tmp_upload/suid-so2.png)](#)

2. Run *strace* on the file and search the output for open/access calls and "no such file" errors:

[![Image of strace](https://github.com/kam1n0/suid-share-object-injection/blob/master/tmp_upload/strace.png)](#)

3. Create the .config directory for the libcacl.c file

[![Image of mkdir](https://github.com/kam1n0/suid-share-object-injection/blob/master/tmp_upload/mkdir.png)](#)

4. Compile the libcalc.c file into a shared object at the location the 'suid-so' executable was looking for (/home/user/.config):

[![Image of gcc](https://github.com/kam1n0/suid-share-object-injection/blob/master/tmp_upload/gcc.png)](#)

5. Execute the suid-so executable again, and note that this time, instead of a progress bar, we get a root shell:

[![Image of execute](https://github.com/kam1n0/suid-share-object-injection/blob/master/tmp_upload/execute.png)](#)
