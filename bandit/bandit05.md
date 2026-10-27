# Bandit Level 5 → Level 6
Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable

Commands you may need to solve this level

ls , cd , cat , file , du , find

# solution

```bash
find . -type f ! -empty ! -executable -readable -exec ls -l {} \; | grep 1033

cat ./inhere/maybehere07/.file2
```
