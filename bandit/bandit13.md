# Bandit Level 13 → Level 14
Level Goal

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.
If you need help with this level: a hint file can be found in the home directory.
Make sure to read the error messages as they are informative.
Commands you may need to solve this level

ssh, scp, umask, chmod, cat, nc, install
Helpful Reading Material

    [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
    [Transferring Files via SCP](https://help.ubuntu.com/community/SSH/TransferFiles)

# Solution

```bash
cat sshkey.private 
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
NhAAAAAwEAAQAAAYEAuCCoxSR6xDCnsm98k.......

bandit13@bandit:~$ exit
touch ~/.ssh/bandit14.key
vim ~/.ssh/bandit14.key
```
- put key in file ~/.ssh/bandit14.key

```vim
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
NhAAAAAwEAAQAAAYEAuCCoxSR6xDCnsm98k.......
```
- change permissions

```bash
chmod 0600 ~/.ssh/bandit14.key
```

- add in config

```bash
vim ~/.ssh/config
```

- add to config file

```vim
Host bandit
	HostName bandit.labs.overthewire.org
	PreferredAuthentications publickey
	IdentityFile ~/.ssh/bandit14.key
```

```bash
ssh bandit14@bandit -p 2220
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
nc localhost 30000
```

- put password from /etc/bandit_pas/bandit14
