# Loop

```sh
hosts[0]="domain1.local"
hosts[1]="domain2.local"

echo "${#hosts[*]} elements"

for host in "${hosts[@]}"
do
	ssh-copy-id "{host}"
done
```

# Find files ang grep
```sh
find src/**/*/routing/mobile.js -type f -exec grep 'path' {} \;
```

# Find files ang grep wish extra
grep options:

- -i case insensitive
- -H filename
- -c context
- -n line numbers

```sh
find . -path "**/routing/mobile.js" -type f -exec grep -i -H --colour -C 5 -n 'clients' {} \;
```

# Tar

## Create archive from current dir
```sh
tar -cvzf archive.tar.gz .
```

## Unzip archive
```sh
tar -xf archive.tar.gz -C /target/directory
```

# Function return 
```sh
isdirectory() {
    if [ -d "$1" ] then
        return 0
    else
        return 1
    fi
}
```

check like this:
```sh
if isdirectory $1; then echo "is directory"; else echo "not a directory"; fi
```

or like this:
```sh
isdirectory || echo "not a directory"
```

# Chaining
- `A; B`    Run A and then B, regardless of success of A
- `A && B`  Run B if A succeeded
- `A || B`  Run B if A failed
- `A &`     Run A in background.

# Base dir and dir
```sh
DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
BASE_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )/.." && pwd )"
```

# Increment version

```sh
version=v0.1.101
echo "${version%.*}.$((${version##*.}+1))"
```

# Check who listen port

```sh
lsof -n -i4TCP:$PORT | grep LISTEN
```

# Status code for url and response time
```sh
#!/usr/bin/env bash

URL="http://google.com"

echo $URL

for i in {1..10}
do
   curl -sL -w "code: %{http_code} time: %{time_total}\\n" $URL -o /dev/null
done
```
