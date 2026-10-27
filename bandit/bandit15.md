# Bandit Level 15 → Level 16
Level Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
Commands you may need to solve this level

ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss
Helpful Reading Material

    [Secure Socket Layer/Transport Layer Security on Wikipedia](https://en.wikipedia.org/wiki/Transport_Layer_Security)
    [OpenSSL Cookbook - Testing with OpenSSL](https://www.feistyduck.com/library/openssl-cookbook/online/testing-with-openssl/index.html)

# Solution

```bash
openssl s_client -connect localhost:30001
```

and after put last password

- change permissions

```bash
chmod 0600 ~/.ssh/bandit16.key
```

- add in config

```bash
vim ~/.ssh/config
```

- add to config file

```vim
Host bandit16
	HostName bandit.labs.overthewire.org
	PreferredAuthentications publickey
	IdentityFile ~/.ssh/bandit16.key
```

```bash
ssh bandit17@bandit16 -p 2220
```

