# Bandit Level 29 → Level 30
Level Goal

There is a git repository at ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
Commands you may need to solve this level

git
Helpful Reading Material

    [Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
    [Git from the Bottom Up](https://jwiegley.github.io/git-from-the-bottom-up/)


# Solution

```bash
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo
git branch -a 
git switch dev
cat README
```
