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
  + pkg/foo1.py
  + pkg/bar1.py
  + pkg.py (with class Pkg and function foo)

And one initializer file:
  + pkg/__init__.py.

The contents of `__init__.py` goes like this
```py
from .bar1 import bar1
from .foo1 import foo1
from .pkg import Pkg
from .pkg import foo
```
**Note**

  Use `from .pkg import foo` instead of `from pkg import foo`.

To make documentation using sphinx and to integrate github docs to
read the docs we should do following things

  + First Copy this `rtd_example` to pwd.
  + Replace scripts and edit index.rst files.
  + To create automatic rst
      - `sphinx-apidoc -o docs pkg`
      - copy contents of `modules.rst` to `index.rst` and
        change `modules.rst` according to your taste.
  + cd docs
  + make clean; make html
  + Upload the repo to the github and wait some time for
    read the docs building.
