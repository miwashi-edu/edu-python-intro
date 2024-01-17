# edu-python-intro

> Pevious level we used setup.py to tell PIP how to package/install our command.
> This time we will modernise the project and replace setup.py and requirements.txt with pyproject.toml
> setup.py is as of 2023 entirely deprecated, and pyproject.toml should be used.

## Prerequisites

> 1. Go to github.com.
> 2. Register if you aren't already.
> 3. Create a repository (call it mytoolbox or pentest-toolbox or similar).
> 4. Copy the repository URL


## Clone

```bash
cd ~
git clone https://github.com/[user]/[repository-name].git
cd [repository-name]
```

## Create project scaffold

```bash
cd ws
cd [repository-name]
touch pyproject.toml
mkdir tests
touch tests/__init__.py
mkdir docs
mkdir scripts
mkdir hello_world
touch hello_world/__init__.py

cat > hello_world/main.py << EOF
def main():
    print("Hello World")

if __name__ == "__main__":
    main()
EOF
git add .
git commit -m "Initial commit"
```

## Create pyproject.toml

```bash
cd ws
cd [repository-name]
cat > pyproject.toml << EOF

EOF
```



### Result

```
~/ws/pentest-toolbox/
│
├── hello_world/
│   ├── __init__.py
│   ├── main.py
│
├── tests/
│   ├── __init__.py
│
├── docs/
│   └── documentation files
│
├── scripts/
│   └── useful_scripts
│
├── .gitignore
├── README.md
├── LICENSE
└── pyproject.toml
```

## Install the hello command

```bash
pip install . --user
#If you get: WARNING: The script hello is installed in '/home/devuser/.local/bin' which is not on PATH.
export PATH=$PATH:/home/devuser/.local/bin
```
