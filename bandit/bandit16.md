# Bandit Level 16 → Level 17
Level Goal

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
Commands you may need to solve this level

ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss
Helpful Reading Material

    [Port scanner on Wikipedia](https://en.wikipedia.org/wiki/Port_scanner)

# Solution

```bash
bandit16@bandit:~$ nmap -sV -p 31000-32000 127.0.0.1                                                                                                                
Starting Nmap 7.98 ( https://nmap.org ) at 2026-10-24 20:12 +0000
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00014s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo

bandit16@bandit:~$ openssl s_client -connect localhost:31790 -nocommands
```

- put last password 
