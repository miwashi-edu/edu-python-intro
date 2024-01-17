# edu-python-intro

> Now we start to add to our hello world module.


## Create pyproject.toml

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
