# edu-python-intro

## Project 

```bash
# Create and enter the project directory
mkdir python-intro
cd python-intro

# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On Windows: venv\Scripts\activate
# On Unix or MacOS: source venv/bin/activate

# Create essential files and directories
touch requirements.txt  # For listing dependencies
touch main.py           # Main project file
mkdir modules           # For project modules
mkdir tests             # For test scripts
mkdir scripts           # For utility scripts
mkdir data              # For data files
mkdir docs              # For documentation
touch README.md         # Project description and instructions

# Example of installing a dependency and updating requirements.txt
# pip install <package_name>
# pip freeze > requirements.txt

# Start tracking the project with Git
git init
git add .
git commit -m "Initial commit"
```

## Module

```bash
# Create and enter the project directory
mkdir my_python_package
cd my_python_package

# Initialize a Git repository
git init

# Create a virtual environment
python -m venv venv

# Create essential files and directories for a package
mkdir my_package                # This will be your main package directory
touch my_package/__init__.py     # Initialize the package
touch my_package/module1.py      # An example module file
mkdir tests                      # Directory for tests
touch tests/__init__.py          # Initialize the tests package
touch tests/test_module1.py      # An example test file
touch README.md                  # Project description and instructions
touch LICENSE                    # License file
touch setup.py                   # Setup script for package distribution
touch requirements.txt           # For listing dependencies

# setup.py example content
cat <<EOT > setup.py
from setuptools import setup, find_packages

setup(
    name='my_python_package',
    version='0.1.0',
    author='Your Name',
    author_email='your.email@example.com',
    packages=find_packages(),
    install_requires=[],
    python_requires='>=3.6',
)
EOT

# Initialize .gitignore
cat <<EOT > .gitignore
__pycache__/
*.pyc
venv/
.idea/
.vscode/
EOT

# Activate the virtual environment
# On Windows: venv\Scripts\activate
# On Unix or MacOS: source venv/bin/activate

# First commit
git add .
git commit -m "Initial package project setup"
```

