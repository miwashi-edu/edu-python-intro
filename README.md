# edu-python-intro

> Now we start to add to our hello world module.

## Create indata for piping

```bash
cd ws
cd [repository-name]
cat > ./names.txt << EOF
Mikael
Anna
Eva
Nisse
EOF
```

## Create hello command allowing piping

```bash
cd ws
cd [repository-name]
cat > ./hello_world/main.py << EOF
# hello.py (Revised Version 2)

import argparse
import sys

def main():
    parser = argparse.ArgumentParser(description='Prints a greeting message to the user.')
    parser.add_argument('name', nargs='?', type=str, help='the name of the user')
    parser.add_argument('-v', '--version', action='version', version='%(prog)s 1.0', help="show program's version number and exit")
    
    args = parser.parse_args()

    if args.name:
        print(f"Hello, {args.name}!")
    elif not sys.stdin.isatty():
        for line in sys.stdin:
            name = line.strip()
            if name:
                print(f"Hello, {name}!")
    else:
        parser.print_usage()

if __name__ == "__main__":
    main()
EOF
```


## Usage

```bash
hello Mikael

echo "Alice" | hello

cat names.txt | hello
```

## Update the hello command

```bash
pip install . --user
#If you get: WARNING: The script hello is installed in '/home/devuser/.local/bin' which is not on PATH.
export PATH=$PATH:/home/devuser/.local/bin
```
