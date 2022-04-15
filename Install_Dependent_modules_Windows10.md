# Sample code and dependent module

***The most important part of coding plugin is making a good functional sample code.***

## Starting point ascii art example
To begin with there is an old fashioned [ascii art](https://en.wikipedia.org/wiki/ASCII_art) at `terminal` or `CMD.EXE`. We will show this example as a new plugin.

![figlet.org](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/figlet-org.png)

[Figlet](http://www.figlet.org) is an imprementation to build **BIG** ascii art characters from normal text. 
And you can find esaily `python figlet` module at google or pypi.

![pyfiglet](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/pyfiglet.png)

## Need to install dependent module

You can install `pyfiglet` using pip:
``` sh
pip install pyfiglet
```

## Making a fully functional sample code

The first and most important thing to build plugin is making a good python running code.

Now that you installed `pyfiglet` let's make a python script.

``` python
from pyfiglet import Figlet
f = Figlet(font='slant')
print(f.renderText('text to render'))
```

This three lines code is enough. This shows how the python is simple for developers.

Let's save this script as `pyfiglet_test.py`. Then we can run.

```sh
python pyfiglet_test.py
   __            __     __                               __
  / /____  _  __/ /_   / /_____     ________  ____  ____/ /__  _____
 / __/ _ \| |/_/ __/  / __/ __ \   / ___/ _ \/ __ \/ __  / _ \/ ___/
/ /_/  __/>  </ /_   / /_/ /_/ /  / /  /  __/ / / / /_/ /  __/ /
\__/\___/_/|_|\__/   \__/\____/  /_/   \___/_/ /_/\__,_/\___/_/
```

## requirements.txt at PyCharm
Let's go back to our `PyCharm` environment.

![01-requirements](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/01-requirements.png)

You can find a file named `requirements.txt` at the `asciiart` folder. This folder is a sub folder from `argoslabs` and `myplugin`. This requirements.txt is the normal python and get some hints form this artical, [How to install Python packages with pip and requirements.txt](https://note.nkmk.me/en/python-pip-install-requirements/).

You need to add any dependent python modules.

Here is the example requirements.txt for this example:

```sh
# pip dependent packages

# default for alabs
alabs.common

# for ASCII Art using Figlet
pyfiglet
```

> * Starting with `#` is the comment line.
> * Every plugin must include `alabs.common` dependent module. **DO NOT SET specific version number** for this module.
> * For some reason you need to set specific version for the module like `pyfiglet==0.7`

Usually python modules are supported cross platform - Windows, Linux and MacOS. But sometimes some modules is need to installed and runned on specific OS. 

For example, 

``` sh
# For Windows win32 dependent job : Windows ONLY!!!
pywin32; sys_platform == 'win32'
```

## Install requirements.txt at PyCharm

![02-open-terminal](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/02-open-terminal.png)

After you modified `requirements.txt` you need to install that module for this python environment. 
To install this requirements open the terminal from the context menu, `Open In > Terminal`.

> Please make sure you have set the `Python Interpreter` at Project menu at settings in `PyCharm`.

![03-pip-install](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/03-pip-install.png)

At `PyCharm`'s terminal you can run this command:

``` sh
pip install -r requirements.txt -i https://pypi-official.argos-labs.com/simple
```

> * `alabs.common` python modues exists at our [officai repository](https://pypi-official.argos-labs.com).
> * So next index option, `-i https://pypi-official.argos-labs.com/simple` needed for `pip install` command.

