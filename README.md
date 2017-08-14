Using Sphinx and Read The Docs
===============================

Basic repo demonstrating usage of Sphinx documentation and
ReadTheDocs integration.

#### Requires:
Sphinx 1.5.6

```bash
python -c """import sphinx; print(sphinx.__version__)"""
```

#### Usage
In this example we have three scripts.
  + pkg/hello.py
  + pkg/hi.py
  + pkg.py       (with class Pkg and function foo)

And one initializer file:
  + pkg/__init__.py.

The contents of `__init__.py` goes like this
```py
from .hello import hello
from .hi import hi
from .pkg import Pkg
from .pkg import foo
```
**Note**

  Use `from .pkg import foo` instead of `from pkg import foo`.

To make documentation using sphinx and to integrate github docs to
read the docs we should do following things

  + First Copy this `rtd_example` to pwd.
    - Note: github repo name is `rtd_example` and
            ReadTheDocs name is `rtd_example_bhishan` since
            the name `rtd_example` was already taken.
  + Replace scripts and edit index.rst files.
  + To create automatic rst
      - `sphinx-apidoc -o docs pkg`
      - copy contents of `modules.rst` to `index.rst` and
        delete `modules.rst`.
      - note that the rst files `hello.rst` and `hi.rst` are NOT
        created by `sphinx-apidoc` they are not needed separately
        and are embedded inside `pkg.rst`
      - We can change `index.rst` file to our taste now.
  + cd docs
  + make clean; make html
  + Upload the repo to the github and wait some time for
    read the docs building or build yourself.
