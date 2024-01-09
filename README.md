# edu-python-intro
## Prerequisites

> 1. Go to github.com.
> 2. Register if you aren't already.
> 3. Create an EMPTY repository (call it pentest-toolbox or similar).
> 4. Copy the repository URL


## Clone

```bash
cd ~
git clone https://github.com/miwashi-edu/pentest-toolbox.git # Change to the repository URL you copied in step 4
cd pentest-toolbox # Adjust to the name you chose in step 3.

#python -m venv venv
#source ./venv/bin/activate # Activate venv

# Install the project and its dependencies
#python3 setup.py install

# Additional setup steps (if any, based on the project's README)

# Your commands to run the project (based on the project's documentation)

#deactivate # Quit venv when you are ready
```

## Create project scaffold

```bash
cd ws
cd pentest-toolbox
touch requirements.txt
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

## Create setup.py

```bash
cd ws
cd pentest-toolbox
cat > setup.py << EOF
from setuptools import setup, find_packages

setup(
    name='pentest-toolbox',
    version='0.1.0',
    packages=find_packages(),
    entry_points={
        'console_scripts': [
            'hello=hello_world.main:main',
        ],
    },
)
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
├── requirements.txt
└── setup.py
```

## Create pip configuration

> It tells pip (acronym for "Pip Installs Packages" or "Pip Installs Python") where our commands will be installed in the system.

```bash
mkdir -p ~/.pip
touch ~/.pip/pip.conf
cat > ~/.pip/pip.conf << 'EOF'
[install]
install-option=--prefix=/usr/local
EOF
```

## Install the hello command

```bash
pip install . --prefix=/usr/local
```
