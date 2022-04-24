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

Install poetry

```shell
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
```

After setting up the folder structure in your project, you can initialize the project with poetry.

```shell
poetry init
```

Poetry will run an interactive setup wizard to help you configure your project.  
It will ask for information like:

- The name of the project
- The name of the author
- The name of the license
- The version of the project
- The dependencies of the project
- The development dependencies of the project

After the setup wizard is finishes, poetry will create a `pyproject.toml` file.

You can now install the dependencies into a virtual environment with:

```shell
poetry install
```

You can always use the command `poetry run`,  to run any commands in the virtual environment.
You can activate the virtual environment with:

```shell
poetry shell
```
If you need to add a new dependency, you can use the command `poetry add`.

### Versioning

Versions are defined by the `major.minor.patch` format and can be incremented by poetry.  
If the current version is `1.2.3`:
- `poetry version patch` will increment the patch number to `1.2.4`
- `poetry version minor` will increment the minor number to `1.3.0`
- `poetry version major` will increment the major number to `2.0.0`

### Documentation
#### Documentation of the Library

#### Documentation of the Keywords

#### Hosting the Documentation via GitHub Pages

### Tests

#### Unit Tests

Use a Unit Testing Framework like `unittest` or `pytest` to write unit tests.

#### Acceptance Tests

Use Robot Framework to write acceptance tests.

#### Coverage

Use the `coverage` tool to analyze the test coverage of your library.  
You can run tests with `coverage run` and analyze the coverage with `coverage report`.  
If you run the tests with `coverage run`, you can also generate a HTML report with `coverage html`.
Multiple test runs (e.g. for Unit Tests and Acceptance Tests) can be analyzed with `coverage combine`.

Example:
    
```shell
coverage run --source=MyFirstLibrary -p -m pytest utest/
coverage run --source=MyFirstLibrary -p -m robot atest/
coverage combine
coverage report
coverage html
```    

### Continuous Integration

Use GitHub Actions to automate the release process.

### Automating the recurring tasks

Use the included `tasks.py` file to automate the recurring tasks via the `invoke` command.

```shell
invoke tests
invoke libdoc
invoke readme
```




