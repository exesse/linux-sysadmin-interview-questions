Linux System Administrator/DevOps Interview Questions
====================================================

A collection of linux sysadmin/devops interview questions. Feel free to contribute via pull requests, issues or email messages.


## <a name='toc'>Table of Contents</a>

  1. [Contributors](#contributors)
  1. [General Questions](#general)
  1. [Simple Linux Questions](#simple)
  1. [Medium Linux Questions](#medium)
  1. [Hard Linux Questions](#hard)
  1. [Expert Linux Questions](#expert)
  1. [Networking Questions](#network)
  1. [MySQL Questions](#mysql)
  1. [DevOps Questions](#devop)
  1. [Fun Questions](#fun)
  1. [Demo Time](#demo)
  1. [Other Great References](#references)


#### [[⬆]](#toc) <a name='contributors'>Contributors:</a>

* [moregeek](https://github.com/moregeek)
* [typhonius](https://github.com/typhonius)
* [schumar](https://github.com/schumar)
* [negesti](https://github.com/negesti)
* peter
* [andreashappe](https://github.com/andreashappe)
* [quatrix](https://github.com/quatrix)
* [biyanisuraj](https://github.com/biyanisuraj)
* [pedroguima](https://github.com/pedroguima)
* Ben
* [bharatnc](https://github.com/bharatnc)


#### [[⬆]](#toc) <a name='general'>General Questions:</a>

* What did you learn yesterday/this week?
* Talk about your preferred development/administration environment. (OS, Editor, Browsers, Tools etc.)
* Tell me about the last major Linux project you finished.
* Tell me about the biggest mistake you've made in [some recent time period] and how you would do it differently today. What did you learn from this experience?
* Why we must choose you?
* What function does DNS play on a network?
* What is HTTP?
* What is an HTTP proxy and how does it work?
* Describe briefly how HTTPS works.
* What is SMTP? Give the basic scenario of how a mail message is delivered via SMTP.
* What is RAID? What is RAID0, RAID1, RAID5, RAID10?
* What is a level 0 backup? What is an incremental backup?
* Describe the general file system hierarchy of a Linux system.
* Which difference have between public and private SSH key?


#### [[⬆]](#toc) <a name='simple'>Simple Linux Questions:</a>

<details><summary>What is the name and the UID of the administrator user?
</summary><p>

UID 0, name root, wheel or could be even renamed.
</p>
</details>

<details><summary>How to list all files, including hidden ones, in a directory?
</summary><p>

```bash
ls -la
```
</p></details>

<details><summary> What is the Unix/Linux command to remove a directory and its contents?
</summary><p>

```bash
rm -rf
```
</p></details>

<details><summary> Which command will show you free/used memory? Does free memory exist on Linux?
</summary><p>

```bash
cat /proc/meminfo
vmstat -s | grep 'used memory'
vmstat -s | grep 'free memory'
```
Of course - do you think /proc/meminfo is lying to you?
</p></details>

<details><summary> How to search for the string "my konfu is the best" in files of a directory recursively?
</summary><p>

```bash
grep -r "my konfu is the best" .
```
</p></details>

<details><summary> How to connect to a remote server or what is SSH?
</summary><p>

```ssh username@remote_host -p <custom port>```

Secure Shell (SSH) is a cryptographic network protocol for operating network services securely over an unsecured network.
Typical applications include remote command-line, login, and remote command execution, but any network service can be secured with SSH.
Read more on [Wikipedia](https://en.wikipedia.org/wiki/Ssh_(Secure_Shell)).
</p></details>

<details><summary> How to get all environment variables and how can you use them?
</summary><p>

```bash
set
```
Enviroment variables could be called from scripts, apps or from shell directly as `$VARIABLE_NAME`.
</p></details>

<details><summary> I get "command not found" when I run ```ifconfig -a```. What can be wrong?
</summary><p>

Package `net-tools` is not installed. 
</p></details>

<details><summary> What happens if I type TAB-TAB?
</summary><p>

`command not found` will be returned. 
</p></details>

<details><summary> What command will show the available disk space on the Unix/Linux system?
</summary><p>

Space usage on partitions in human-readable format:
```bash
df -h
```

Inode usage on partitions:
```bash
df -h
```

Disks space usage:
```bash
lsblk
```
</p></details>

<details><summary> What commands do you know that can be used to check DNS records?
</summary><p>

```bash
dig google.com AAAA

# Or for A record simply:
nslookup google.com
```
</p></details>

<details><summary> What Unix/Linux commands will alter a files ownership, files permissions?
</summary><p>

`chown USER:GROUP` - alters ownership

`chmod xxx` - alters permissions, where xxx is:

| # | permission              | rwx | binary |
|---|-------------------------|-----|--------|
| 7 | read, write and execute | rwx | 111    |
| 6 | read and write          | rw- | 110    |
| 5 | read and execute        | r-x | 101    |
| 4 | read only               | r-- | 100    |
| 3 | write and execute       | -wx | 011    |
| 2 | write only              | -w- | 010    |
| 1 | execute only            | --x | 001    |
| 0 | none                    | --- | 000    |

</p></details>

<details><summary> What does ```chmod +x FILENAME``` do?
</summary><p>

Will make `FILENAME` executable.
</p></details>

<details><summary> What does the permission 0750 on a file mean?
</summary><p>

Sets `-rwxr-x---` permission which means that user has `read, write and execute`, group only `read and execute` 
and others has access at all. Chmod online calculator could be found [here](https://chmodcommand.com/).
</p></details>

<details><summary> What does the permission 0750 on a directory mean?
</summary><p>
Generally speaking exactly the same as previous question, but on the directory scope. When used with flag `-r` same 
permission would be re-applied on all files inside the folder. By default files will have separate permissions. 
</p></details>

<details><summary> How to add a new system user without login permissions?
</summary><p>

```bash
useradd -r USERNAME
```
Other way is to set default shell to `/usr/sbin/nologin` for the user in `/etc/passwd` file after regular process.
</p></details>

<details><summary> How to add/remove a group from a user?
</summary><p>

```bash
gpasswd -a USER GROUP
gpasswd -d USER GROUP
```
First command for 'add' and later for 'remove'.
</p></details>

<details><summary> What is a bash alias?
</summary><p>

An bash alias is nothing but the shortcut to commands. Read more [here](https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html).
</p></details>

<details><summary> How do you set the mail address of the root/a user?
</summary><p>

One will need to edit or create file `/etc/aliases` to add the email next to the user.

Example of '/etc/aliases':
```vi
# See man 5 aliases for format
postmaster:    root

root: user@youremaildomain.com
```
</p></details>

<details><summary> What does CTRL-c do?
</summary><p>

Cancels running task in shell.
</p></details>

<details><summary> What does CTRL-d do?
</summary><p>

Exits from terminal. Closes TTY/SSH session.
</p></details>

<details><summary> What does CTRL-z do?
</summary><p>

Pauses running task. To proceed in foreground type `fg` and `bg` for background. However even in background the task 
will be bind to current terminal.  
</p></details>

<details><summary> What is in /etc/services?
</summary><p>

Well-known ports used by services and\or registered by IANA. Read more [here](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).
</p></details>

<details><summary> How to redirect STDOUT and STDERR in bash? (> /dev/null 2>&1)
</summary><p>

`>` - write to a file

`>>` - append to an existing file

`1>filename` - STDOUT

`2>filename` - STDERR

`&>filename` - both STDOUT and STDERR

`&>/dev/null` - make all OUTPUT silent
</p></details>

<details><summary> What is the difference between UNIX and Linux.
</summary><p>

Unix is proprietary, multitasking, multiuser computer operating systems that derive from the original AT&T Unix, 
developed in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie. 

Linux is nothing but a UNIX clone which is written Linus Torvalds from scratch with the help of some hackers across the globe.

More info in the article - 
[Unix Vs Linux: Learn what is the Core Difference between UNIX and Linux Architecture, Kernel And Commands](https://www.softwaretestinghelp.com/unix-vs-linux/).
</p></details>

<details><summary> What is the difference between Telnet and SSH?
</summary><p>

Telnet is an application protocol used on the Internet or local area network to provide a bidirectional interactive 
text-oriented communication facility using a virtual terminal connection. Sends messages as plain text. Operates on 23/tcp.
Read more on [Wikipedia](https://en.wikipedia.org/wiki/Telnet).

Secure Shell (SSH) is a cryptographic network protocol for operating network services securely over an unsecured network.
Typical applications include remote command-line, login, and remote command execution, but any network service can be secured with SSH.
Read more on [Wikipedia](https://en.wikipedia.org/wiki/Ssh_(Secure_Shell)).
</p></details>

<details><summary> Explain the three load averages and what do they indicate. What command can be used to view the load averages?
</summary><p>

`uptime` is the best way to view load average. It is also useful to get number of CPU's with `nproc` for better understanding 
of results. 

Example: `load average: 1,81, 0,77, 0,57`. 

* **1,81** - is the usage over **last minute**. If we assume that the result is for one core system - this means that last
minute our CPU was busy, and approximately twice as much load is waiting to be processed. I run 8 CPU's computer, so it basically
means that over last minute each CPU on my system was busy only 22,6 percent of the given time.
* **0,77** - usage over **last 5 minutes**. For one CPU system means that, 23 percent of time computer was idle or 1 minute and 9 seconds
was doing nothing. 
* **0,57** - average usage over **last 15 minutes**. One-CPU computer was idle 6 minutes and 27 seconds or 43% of time.   
</p></details>

<details><summary> Can you name a lower-case letter that is not a valid option for GNU ```ls```?
</summary><p>

```bash
ls -y
___
ls: invalid option -- 'y'
Try 'ls --help' for more information.
```
</p></details>

<details><summary> What is a Linux kernel module?
</summary><p>

Modules are pieces of code written in C that can be loaded and unloaded into the kernel upon demand. 
They extend the functionality of the kernel without the need to reboot the system. 
For example, one type of module is the device driver, which allows the kernel to access hardware connected to the system. 
Without modules, we would have to build monolithic kernels and add new functionality directly into the kernel image. 
Besides having larger kernels, this has the disadvantage of requiring us to rebuild and reboot the kernel every time we want new functionality.
Read more [here](https://linux.die.net/lkmpg/x40.html).
</p></details>

<details><summary> Walk me through the steps in booting into single user mode to troubleshoot a problem.
</summary><p>

[Runlevel](https://en.wikipedia.org/wiki/Runlevel) - is a mode of operation in the computer operating systems that 
implement Unix System V-style initialization.

| level | name | description |
|-------|-----------------------|-------------|
| 0 | halt | Shuts down the system |
| 1 | single-user mode | Mode for administrative tasks |
| 2 | multi-user mode | Does not configure network interfaces and does not export networks services |
| 3 | multi-user mode with networking | Starts the system normally |
| 4 | not-used | Reserved for special purposes |
| 5 | display-mode | Same as level 3, but with display manager |
| 6 | reboot | Reboots the system | 

Troubleshooting guide: 
* reboot and hold 'Shift' to bring up GRUB menu
* select GRUB menu entry and press 'e' to edit
* locate the line containing `ro  quiet splash` and add `single` to that line
* press 'Ctrl-x' or 'F10' to proceed. 
</p></details>

<details><summary> Walk me through the steps you'd take to troubleshoot a 404 error on a web application you administer.
</summary><p>

The HTTP error 404, or more commonly called "404 error", means that the page you are trying to open could not be found on the server.
I would go bottom from the top using OSI model:
* application (where error happens)
* presentation (other browser, other page)
* session (DNS queries)
* transport
* network
* data link
* physical
</p></details>

<details><summary> What is ICMP protocol? Why do you need to use?
</summary>
<p>

Internet Control Message Protocol is located at the Network layer of the OSI model and is an integral part of the 
Internet Protocol suite (TCP/IP). ICMP is assigned Protocol Number 1 in the IP suite according to 
[IANA.org](https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xml). Designed to act as an error reporting
and query service, it plays a crucial role in the host-to-host datagram service in network communication.
</p></details>

#### [[⬆]](#toc) <a name='medium'>Medium Linux Questions:</a>

<details><summary>What do the following commands do and how would you use them?</summary>
<p>
* ```tee```
* ```awk```
* ```tr```
* ```cut```
* ```tac```
* ```curl```
* ```wget```
* ```watch```
* ```head```
* ```tail```
* ```less```
* ```cat```
* ```touch```
* ```sar```
* ```netstat```
* ```tcpdump```
* ```lsof```
</p></details>
* What does an ```&``` after a command do?
* What does ```& disown``` after a command do?
* What is a packet filter and how does it work?
* What is Virtual Memory?
* What is swap and what is it used for?
* What is an A record, an NS record, a PTR record, a CNAME record, an MX record?
* Are there any other RRs and what are they used for?
* What is a Split-Horizon DNS?
* What is the sticky bit?
* What does the immutable bit do to a file?
* What is the difference between hardlinks and symlinks? What happens when you remove the source to a symlink/hardlink?
* What is an inode and what fields are stored in an inode?
* How to force/trigger a file system check on next reboot?
* What is SNMP and what is it used for?
* What is a runlevel and how to get the current runlevel?
* What is SSH port forwarding?
* What is the difference between local and remote port forwarding?
* What are the steps to add a user to a system without using useradd/adduser?
* What is MAJOR and MINOR numbers of special files?
* Describe the mknod command and when you'd use it.
* Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.
* Describe a scenario when deleting a file, but 'df' not showing the space being freed.
* Describe how 'ps' works.
* What happens to a child process that dies and has no parent process to wait for it and what’s bad about this?
* Explain briefly each one of the process states.
* How to know which process listens on a specific port?
* What is a zombie process and what could be the cause of it?
* You run a bash script and you want to see its output on your terminal and save it to a file at the same time. How could you do it?
* Explain what echo "1" > /proc/sys/net/ipv4/ip_forward does.
* Describe briefly the steps you need to take in order to create and install a valid certificate for the site https://foo.example.com.
* Can you have several HTTPS virtual hosts sharing the same IP?
* What is a wildcard certificate?
* Which Linux file types do you know?
* What is the difference between a process and a thread? And parent and child processes after a fork system call?
* What is the difference between exec and fork?
* What is "nohup" used for?
* What is the difference between these two commands?
 * ```myvar=hello```
 * ```export myvar=hello```
* How many NTP servers would you configure in your local ntp.conf?
* What does the column 'reach' mean in ```ntpq -p``` output?
* You need to upgrade kernel at 100-1000 servers, how you would do this?
* How can you get Host, Channel, ID, LUN of SCSI disk?
* How can you limit process memory usage?
* What is bash quick substitution/caret replace(^x^y)?
* Do you know of any alternative shells? If so, have you used any?
* What is a tarpipe (or, how would you go about copying everything, including hardlinks and special files, from one server to another)?
* How can you tell if the httpd package was already installed?
* How can you list the contents of a package?
* How can you determine which package is better: openssh-server-5.3p1-118.1.el6_8.x86_64 or openssh-server-6.6p1-1.el6.x86_64 ?
* Can you explain to me the difference between block based, and object based storage?

#### [[⬆]](#toc) <a name='hard'>Hard Linux Questions:</a>

* What is a tunnel and how you can bypass a http proxy?
* What is the difference between IDS and IPS?
* What shortcuts do you use on a regular basis?
* What is the Linux Standard Base?
* What is an atomic operation?
* Your freshly configured http server is not running after a restart, what can you do?
* What kind of keys are in ~/.ssh/authorized_keys and what it is this file used for?
* I've added my public ssh key into authorized_keys but I'm still getting a password prompt, what can be wrong?
* Did you ever create RPM's, DEB's or solaris pkg's?
* What does ```:(){ :|:& };:``` do on your system?
* How do you catch a Linux signal on a script?
* Can you catch a SIGKILL?
* What's happening when the Linux kernel is starting the OOM killer and how does it choose which process to kill first?
* Describe the linux boot process with as much detail as possible, starting from when the system is powered on and ending when you get a prompt.
* What's a chroot jail?
* When trying to umount a directory it says it's busy, how to find out which PID holds the directory?
* What's LD_PRELOAD and when it's used?
* You ran a binary and nothing happened. How would you debug this?
* What are cgroups? Can you specify a scenario where you could use them?
* How can you remove/delete a file with file-name consisting of only non-printable/non-type-able characters?
* How can you increase or decrease the priority of a process in Linux?


#### [[⬆]](#toc) <a name='expert'>Expert Linux Questions:</a>

* A running process gets ```EAGAIN: Resource temporarily unavailable``` on reading a socket. How can you close this bad socket/file descriptor without killing the process?
* What do you control with swapiness?
* How do you change TCP stack buffers? How do you calculate it?
* What is Huge Tables? Why isn't it enabled by default? Why and when use it?
* What is LUKS? How to use it?


#### [[⬆]](#toc) <a name='network'>Networking Questions:</a>

* What is localhost and why would ```ping localhost``` fail?
* What is the similarity between "ping" & "traceroute" ? How is traceroute able to find the hops.
* What is the command used to show all open ports and/or socket connections on a machine?
* Is 300.168.0.123 a valid IPv4 address?
* Which IP ranges/subnets are "private" or "non-routable" (RFC 1918)?
* What is a VLAN?
* What is ARP and what is it used for?
* What is the difference between TCP and UDP?
* What is the purpose of a default gateway?
* What is command used to show the routing table on a Linux box?
* A TCP connection on a network can be uniquely defined by 4 things. What are those things?
* When a client running a web browser connects to a web server, what is the source port and what is the destination port of the connection?
* How do you add an IPv6 address to a specific interface?
* You have added an IPv4 and IPv6 address to interface eth0. A ping to the v4 address is working but a ping to the v6 address gives you the response ```sendmsg: operation not permitted```. What could be wrong?
* What is SNAT and when should it be used?
* Explain how could you ssh login into a Linux system that DROPs all new incoming packets using a SSH tunnel.
* How do you stop a DDoS attack?
* How can you see content of an ip packet?
* What is IPoAC (RFC 1149)?
* What will happen when you bind port 0?



#### [[⬆]](#toc) <a name='mysql'>MySQL questions:</a>

* How do you create a user?
* How do you provide privileges to a user?
* What is the difference between a "left" and a "right" join?
* Explain briefly the differences between InnoDB and MyISAM.
* Describe briefly the steps you need to follow in order to create a simple master/slave cluster.
* Why should you run "mysql_secure_installation" after installing MySQL?
* How do you check which jobs are running?
* How would you take a backup of a MySQL database?

#### [[⬆]](#toc) <a name='devop'>DevOps Questions:</a>

* Can you describe your workflow when you create a script?
* What is GIT?
* What is a dynamically/statically linked file?
* What does "./configure && make && make install" do?
* What is puppet/chef/ansible used for?
* What is Nagios/Zenoss/NewRelic used for?
* What is Jenkins/TeamCity/GoCI used for?
* What is the difference between Containers and VMs?
* How do you create a new postgres user?
* What is a virtual IP address? What is a cluster?
* How do you print all strings of printable characters present in a file?
* How do you find shared library dependencies?
* What is Automake and Autoconf?
* ./configure shows an error that libfoobar is missing on your system, how could you fix this, what could be wrong?
* What are the advantages/disadvantages of script vs compiled program?
* What's the relationship between continuous delivery and DevOps?
* What are the important aspects of a system of continuous integration and deployment?
* How would you enable network file sharing within AWS that would allow EC2 instances in multiple availability zones to share data?

#### [[⬆]](#toc) <a name='fun'>Fun Questions:</a>

* A careless sysadmin executes the following command: ```chmod 444 /bin/chmod ``` - what do you do to fix this?
* I've lost my root password, what can I do?
* I've rebooted a remote server but after 10 minutes I'm still not able to ssh into it, what can be wrong?
* If you were stuck on a desert island with only 5 command-line utilities, which would you choose?
* You come across a random computer and it appears to be a command console for the universe. What is the first thing you type?
* Tell me about a creative way that you've used SSH?
* You have deleted by error a running script, what could you do to restore it?
* What will happen on 19 January 2038?
* How to reboot server when reboot command is not responding?


#### [[⬆]](#toc) <a name='demo'>Demo Time:</a>

* Unpack test.tar.gz without man pages or google.
* Remove all "*.pyc" files from testdir recursively?
* Search for "my konfu is the best" in all *.py files.
* Replace the occurrence of "my konfu is the best" with "I'm a linux jedi master" in all *.txt files.
* Test if port 443 on a machine with IP address X.X.X.X is reachable.
* Get http://myinternal.webserver.local/test.html via telnet.
* How to send an email without a mail client, just on the command line?
* Write a ```get_prim``` method in python/perl/bash/pseudo.
* Find all files which have been accessed within the last 30 days.
* Explain the following command ```(date ; ps -ef | awk '{print $1}' | sort | uniq | wc -l ) >> Activity.log```
* Write a script to list all the differences between two directories.
* In a log file with contents as ```<TIME> : [MESSAGE] : [ERROR_NO] - Human readable text``` display summary/count of specific error numbers that occurred every hour or a specific hour.


#### [[⬆]](#toc) <a name='references'>Other Great References:</a>

Some questions are 'borrowed' from other great references like:

* https://github.com/darcyclarke/Front-end-Developer-Interview-Questions
* https://github.com/kylejohnson/linux-sysadmin-interview-questions/blob/master/test.md
* http://slideshare.net/kavyasri790693/linux-admin-interview-questions
* https://srvfail.com/linux-interview-questions/
