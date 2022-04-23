# For the very first time  
This repository shall provide additional information about the RoboCon 2022 Talk "For the very first time".  
The talk will describe how to release a new Robot Framework Library to the community.  
The goal is to have a package which can be installed with
``pip install robotframework-myfirstlibrary``.  

## Releasing is more than just Coding..

Releasing a Robot Framework Library to the public is more then just a bit of coding in Python.  
Maintaining and releasing an open source library requires:

- a proper repository structure
- handling of your library and development dependencies
- versioning and publishing (to PyPi)
- documentation of your library and the keywords it provides
- Unit tests and Acceptance tests
- Using Continuous Integration (CI) to build, test and release your library
- Automating the recurring tasks

### Repository Structure
``` 
robotframework-myfirstlibrary
├── MyFirstLibrary
│   ├── __init__.py
│   └── myfirstlibrary.py
├── atest
│   └── atest.robot
├── docs
│   ├── README.md
│   └── myfirstlibrary.html
├── pyproject.toml
├── tasks.py
└── utest
    └── test_myfirstlibrary.py
```

``robotframework-myfirstlibrary`` is the `distribution name` of the library.  
It can later be used to install the library with `pip install robotframework-myfirstlibrary`.  
It's also the name of the `GitHub Repository`.


`MyFirstLibrary` is the name of the `Python Package`.  
It can later be used to import the library into Robot Framework.

``` Robot Framework
*** Settings ***
Library    MyFirstLibrary

*** Test Cases ***
Use a keyword from MyFirstLibrary
   My First Library Keyword     # Use the keyword from MyFirstLibrary
```

The `__init__.py` file is the `Python Package Init File`.  
It will be executed when the package is imported.  
It needs to import the Class `MyFirstLibrary` from the module `myfirstlibrary.py`.
Only afterwards the `keywords` from the `MyFirstLibrary` class can be used.

`__init__.py`
``` Python
from .myfirstlibrary import MyFirstLibrary
```


### Dependencies

### Versioning

### Documentation

### Unit Tests

### Acceptance Tests

### Continuous Integration

### Automating the recurring tasks




