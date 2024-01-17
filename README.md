# edu-python-intro

> Now we start to add to our hello world module.

## Create hello command using vanilla python

```bash
cd ws
cd [repository-name]
cat > ./hello_world/main.py << EOF
# hello.py (Version 1)

import sys

def main():
    if len(sys.argv) == 2:
        if sys.argv[1] in ['-h', '-?', '-v']:
            print_usage()
        else:
            name = sys.argv[1]
            print(f"Hello, {name}!")
    else:
        print_usage()

def print_usage():
    usage = """
Usage: hello.py [OPTION]... [NAME]
Prints a greeting message to the user.

Arguments:
  NAME        the name of the user

Options:
  -h, -?      show this help message and exit
  -v          show program's version number and exit
    """
    print(usage)

if __name__ == "__main__":
    main()
EOF
```


## Create hello command using argparser

```bash
cd ws
cd [repository-name]
cat > ./hello_world/main.py << EOF
# hello.py (Version 2)

import argparse

def main():
    parser = argparse.ArgumentParser(description='Prints a greeting message to the user.')
    parser.add_argument('name', nargs='?', help='the name of the user')
    parser.add_argument('-v', '--version', action='version', version='%(prog)s 1.0', help="show program's version number and exit")
    
    args = parser.parse_args()

    if args.name:
        print(f"Hello, {args.name}!")
    else:
        parser.print_usage()

if __name__ == "__main__":
    main()
EOF
```

## Update the hello command

```bash
pip install . --user
#If you get: WARNING: The script hello is installed in '/home/devuser/.local/bin' which is not on PATH.
export PATH=$PATH:/home/devuser/.local/bin
```
