# Python Fundamentals

## Installing Python

[How to install pip/conda on Mac/Windows.](pip-and-conda-install.md)

## Setting Up Virtual Enironments
* Heavily recommended for local computer usage, 100% required for remote
  deployment.
* Python has a standard library of functionality; additional functionality is
  imported into projects through additional packages.
  + PyPI is the most popular repository of Python packages.  Conda is an
    alternative repository.
  + `pip` is the tool to install packages from PyPI; `conda` for the Conda
    repositories.
  + Different projects will require different packages.  Installing just the
    packages that you need for each Python project:
    - Prevents package version conflicts between different projects.
    - Establishes a minimized storage footprint of packages for each project
      (though commonly-used packages in many projects will be replicated).
  + `virtualenv` will be used to create virtual environments for each Python project.
  + :eyes: Make sure that you have `pip` and `virtualenv` installed on your laptop. :eyes:
* Steps towards creating and configuring a virtual environment:
  1. `virtualenv env` (creates a local python virtual environment in `env/`)
  1. `source env/bin/activate` (activate the working environment)
  1. `pip install $PACKAGENAME`
  1. Collect all of the packages that you need in a `requirements.txt` file
     [optionally include versions], and install all at once: `pip install -r
     requirements.txt`.  This is very useful for replicating virtual
     environments on new systems (e.g., CI testing setups).
  1. Work
  1. `deactivate`

## Python Starter Notes
* Python uses indentation--not semicolons and curly braces--to delineate
  different logical aspects of code.
```
if BOOLEAN_IS_TRUE:
    do_this()
else:
    do_that()
    and_this()

test_tuple = (1, 2, 3)
test_list = ['a', 'b', 'c']

for n, val in enumerate(test_tuple):
    print(val)
    print(n)
    print(test_tuple[n])

```

## Modular Coding
* Modularity will allow for discrete *units *of function to be explicitly *tested*.  This is essential in medical software design.
* Modularity will allow the functional logic of software to be more readable.
* Modularity promotes the reuse of tested and validated code to compose new
  code.
* A non-object-oriented example of Python code:
```
def main():
    """main function
    This main function captures what actions this script will execute when called
    by the last line of the script (note functions that are called are named as
    verbs (actions)).
    """
    collect_all_csv_filenames()
    read_csv()
    write_data()


def collect_all_csv_filenames():
    """Define a function that, as written, does nothing
    """
    from glob import glob
    pass


def read_csv():
    """Define another function
    """
    check_no_spaces()
    check_camel_case()
    pass


def write_data(type='json'):
    """Define another function
    """
    pass


def check_no_spaces():
    """Define another function
    """
    pass


def check_camel_case():
    """Define another function
    """
    pass
    
# The __name__ variable is something automatically set by the Python
# interpreter based on the file that is being executed.  When this script is
# being directly executed from the command line, __name__ is set equal to 
# __main__; when that happens, this conditional statement then executes the
# main() function defined above.  You need these two lines to get your program 
# to run as a script from the command line.
if __name__ == "__main__":
    main()
```
* All of the functions above, except for main, should be testable.

## Learning Python
* [Playground and Cheatsheet for Learning Python](https://github.com/mlp6/learn-python)  Please note that this is a fork of a repository created by GitHub user [trekhleb](https://github.com/trekhleb).
* [LearnXinYMinutes for Python3](https://learnxinyminutes.com/docs/python3/).
