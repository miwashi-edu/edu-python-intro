# edu-python-intro

> Now we start to add to our hello world module.

## Create hello command allowing piping

```bash
cd ws
cd [repository-name]
cat > ./hello_world/main.py << EOF
# hello.py (Revised Version 1)

import sys

def main():
    if len(sys.argv) == 2:
        if sys.argv[1] in ['-h', '-?', '-v']:
            print_usage()
        else:
            name = sys.argv[1]
            print(f"Hello, {name}!")
    elif not sys.stdin.isatty():
        for line in sys.stdin:
            name = line.strip()
            if name:
                print(f"Hello, {name}!")
    else:
        print_usage()

def print_usage():
    usage = """
Usage: hello.py [OPTION]... [NAME]
Prints a greeting message to the user. Can also read names from standard input.

Arguments:
  NAME        the name of the user (optional if using pipe)

Options:
  -h, -?      show this help message and exit
  -v          show program's version number and exit
    """
    print(usage)

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
