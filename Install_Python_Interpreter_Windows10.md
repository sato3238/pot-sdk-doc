# Python Interpreter on Windows 10

There is no python interpreter on Windows so we need to install it.

> We support Python Version 3.7.3. 

## Install Python 3.7.3

![01-google-search](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/01-google-search.png)
First search at google with `python 3.7.3 download for windows`.

![02-Python3.7.3-Page](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/02-Python3.7.3-Page.png)
Python 3.7.3 page shows.

![03-download-executable-x86-installable](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/03-download-executable-x86-installable.png)
You can download `Windows x86 executable installer`
> * There are installer files for `x86-64` and `x86`.  `x86-64` is for 64-bit Windows OS and `x86` is for 32-bit Windows OS. 
> * Windows PAM embed Python 3.7.3 32-bit interpreter and using it so choose `x86` installer.
> * 32-bit python can also run at 64-bit Windows OS.

And the let's run the downloaded installer.

![04-install-python](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/04-install-python.png)

Let's run `Customized installation` at the starting setup window.
> * You can use `Install Now` with default options, but for the convenience of following examples.

![05-optional-features](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/05-optional-features.png)
> * It's necessary to set `pip` option to use pip for installing other Python packages.

![06-cusmise-install-location](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/06-cusmise-install-location.png)

> * We recommand the `Customize install location` with the `C:\Python37-32` location.
> * This is for using absolute `python.exe` path like `C:\Python37-32\python.exe` without setting PATH.

![07-setup-succussful](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/07-setup-succussful.png)

Finally successfully installed of `Python 3.7.3`.

![08-python-version-check](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/08-python-version-check.png)

We can check the Python version at `CMD.EXE`.

```sh
C:\> C:\Python37-32\python.exe -V
Python 3.7.3

C:\> C:\Python37-32\python.exe
Python 3.7.3 (v3.7.3:ef4ec6ed12, Mar 25 2019, 21:26:53) [MSC v.1916 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

## Building Virtual Environment

Python [Virtual Environment](https://docs.python.org/3.7/library/venv.html) is the lightweight “virtual environments” with their own site directories, optionally isolated from system site directories. Each virtual environment has its own Python binary (which matches the version of the binary that was used to create this environment) and can have its own independent set of installed Python packages in its site directories.

![09-building-venv](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/01-Install_Python_3.7/09-building-venv.png)

``` sh
C:\>mkdir work

C:\>cd work

C:\work>C:\Python37-32\python.exe -m venv py37

C:\work>py37\Scripts\activate

(py37) C:\work>pip list
Package    Version
---------- -------
pip        19.0.3
setuptools 40.8.0
You are using pip version 19.0.3, however version 22.0.4 is available.
You should consider upgrading via the 'python -m pip install --upgrade pip' command.

(py37) C:\work>python -m pip install --upgrade pip
Collecting pip
  Using cached https://files.pythonhosted.org/packages/4d/16/0a14ca596f30316efd412a60bdfac02a7259bf8673d4d917dc60b9a21812/pip-22.0.4-py3-none-any.whl
Installing collected packages: pip
  Found existing installation: pip 19.0.3
    Uninstalling pip-19.0.3:
      Successfully uninstalled pip-19.0.3
Successfully installed pip-22.0.4

(py37) C:\work>pip list
Package    Version
---------- -------
pip        22.0.4
setuptools 40.8.0

(py37) C:\work>where python
C:\work\py37\Scripts\python.exe
C:\Users\toor\AppData\Local\Microsoft\WindowsApps\python.exe

(py37) C:\work>deactivate
C:\work>
```

Whenever you want a new Virtual Environment you can create and use it.
If you do not want that Virtual Environment just delete created folder in case above example `C:\work\py37`.
