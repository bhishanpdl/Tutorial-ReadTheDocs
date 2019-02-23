# Step 1: Prerequisites
- Go to your conda environment.
- Install sphinx. `python -c """import sphinx; print(sphinx.__version__)""" # 1.7.9`
- Install read the docs theme `pip install sphinx_rtd_theme`. `python -c """import sphinx_rtd_theme as rtd; print(rtd.__version__)""" # 0.4.3`
- We need these versions in `requirements.txt` file.

# Step 2: Download this repos as an template
- We will need Makefile, and need to change requirements.txt.
- We will change the source python scripts.


# Using read the docs
- Sign in to your [read the docs](https://readthedocs.org/dashboard/).
- Click `Import a Project`.
- `Import Manually`.
- Name: `Bhishans ReadTheDocs`. It must be unique to read the docs website.
- Repo: `https://github.com/bhishanpdl/Tutorial-ReadTheDocs`
- Edit advanced project options: `yes`.
- Choose language `Python`.
- Click Build button and after build up, click view the docs.
- From now on, it is always hosted in read the docs website.



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
