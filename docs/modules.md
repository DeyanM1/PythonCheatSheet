# Python Modules and Packaging. Complete Reference.

Copy sections directly into a Jupyter notebook.

---

## Imports & `__name__`

```python
import math                                             # imports the entire module
from math import sqrt                                   # imports specific function (math.sqrt not needed)
import numpy as np                                      # imports module with an alias

# --- Absolute vs Relative Imports (Inside Packages) ---
# Assuming structure: package/
#                       ├── __init__.py
#                       ├── module_a.py
#                       └── subpackage/
#                             ├── __init__.py
#                             └── module_b.py

# In module_b.py:
# from package import module_a                          # absolute import (preferred for clarity)
# from .. import module_a                               # relative import (go up one level)

# --- The __name__ Guard ---
if __name__ == "__main__":                              # checks if script is run directly (not imported)
    print("Script executed directly")                   # code here won't run if file is imported as module

```

## Virtual Environments (venv)

```bash
# --- Creating & Activating ---
# It is best practice to create a venv for every project to isolate dependencies.

python -m venv .venv                                    # creates a virtual environment named '.venv'

# Windows Activation:
.venv\Scripts\activate                                  # activates the environment (prompt changes)

# macOS/Linux Activation:
source .venv/bin/activate                               # activates the environment (prompt changes)

# Deactivation:
deactivate                                              # exits the virtual environment

```

## Package Management (pip)

```bash
# --- Installing Packages ---
pip install requests                                    # installs latest version of a package
pip install "requests==2.31.0"                          # installs a specific version
pip install --upgrade requests                          # upgrades package to the latest version

# --- Managing Dependencies ---
pip list                                                # lists all installed packages in current env
pip freeze > requirements.txt                           # saves all current packages to file
pip install -r requirements.txt                         # installs all packages listed in file

# --- Package Info ---
pip show requests                                       # shows details (version, location) of package

```

## Project Layout (Best Practice)

```text
my_project/                                             # root project folder
├── .venv/                                              # virtual environment (excluded from git)
├── .gitignore                                          # files to ignore (e.g., .venv, __pycache__)
├── requirements.txt                                    # list of dependencies
├── README.md                                           # project documentation
├── pyproject.toml                                      # build system requirements (modern standard)
└── src/                                                # source code directory (prevents import errors)
    └── my_package/                                     # actual python package
        ├── __init__.py                                 # marks directory as a package
        ├── main.py                                     # entry point script
        └── utils.py                                    # helper module

```

```python
# --- Entry Point Example (src/my_package/main.py) ---
# To run this project structure usually: python -m my_package.main

import sys                                              # imports system module
from .utils import helper_func                          # relative import from same package

def main():                                             # defines main execution logic
    print("App started")                                # prints status
    helper_func()                                       # calls imported function

if __name__ == "__main__":                              # checks if running as main script
    main()                                              # executes main function

```
