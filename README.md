# edu-python-intro
## Prerequisites

> 1. Go to github.com.
> 2. Register if you aren't already.
> 3. Create an EMPTY repository (call it pentest-toolbox or similar).
> 4. Copy the repository URL


## Clone

```console
user@linux:~$ cd ~
user@linux:~$ git clone https://github.com/miwashi-edu/pentest-toolbox.git # Change to the repository URL you copied in step 4
user@linux:~$ cd pentest-toolbox # Adjust to the name you chose in step 3.

user@linux:pentest-toolbox$ python -m venv venv
user@linux:pentest-toolbox$ source ./venv/bin/activate # Activate venv

# Install the project and its dependencies
(venv) user@linux:pentest-toolbox$ python -m build .
(venv) user@linux:pentest-toolbox$ sudo python -m installer dist/*.whl

# Additional setup steps (if any, based on the project's README)

# Your commands to run the project (based on the project's documentation)

(venv) user@linux:pentest-toolbox$ deactivate # Quit venv when you are ready
```

## Create project scaffold

```bash
cd ~/pentest-toolbox
echo "# pentest-toolbox" > README.md
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
cd ~/pentest-toolbox
cat > pyproject.toml << EOF
[build-system]
requires = ["setuptools"]
build-backend = "setuptools.build_meta"

[project]
name = "pentest_toolbox"
version = "0.1.0"
description = "A test project"
authors = [
    {name = "Anton Hvornum", email = "anton@hvornum.se"},
]
license = {text = "AGPL-1.0-or-later"}
readme = "README.md"
requires-python = ">=3.11"
dependencies = [
]

[project.scripts]
hello = "hello_world.main:main"

[options]
package_dir="hello_world"
include_package_data = true

[tool.setuptools.packages.find]
where = ["."]
include = ["hello_world*"]
EOF
```

## Create .gitignore

```bash
cd ws
cd pentest-toolbox
cat > .gitignore << 'EOF'

# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
*.egg-info/
.installed.cfg
*.egg

# PyInstaller
*.manifest
*.spec

# PyBuilder
.pybuilder/
target/

# Jupyter Notebook
.ipynb_checkpoints

# Python tracebacks
python-*.log

# pytest
.pytest_cache/

# mypy
.mypy_cache/

# Virtual environments
.venv/
venv/
ENV/
env/
bin/
Scripts/
pyvenv.cfg
*.pyc
EOF
```

### Result

```
~/pentest-toolbox/
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
└── pyproject.toml
```

## Install the hello command

```console
user@linux:~$ cd pentest-toolbox
user@linux:pentest-toolbox$ python -m build .
user@linux:pentest-toolbox$ sudo python -m installer --prefix /usr/local dist/*.whl
```