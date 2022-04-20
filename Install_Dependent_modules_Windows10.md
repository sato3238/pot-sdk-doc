# Sample code and dependent modules

***The most important part of coding plugin is making a good functional sample code.***

## Starting point - the ascii art example
To begin with, there is an old fashioned [ascii art](https://en.wikipedia.org/wiki/ASCII_art) at `terminal` or `CMD.EXE`. We will show this example as a new plugin.

![figlet.org](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/figlet-org.png)

[Figlet](http://www.figlet.org) is an imprementation to build **BIG** ascii art characters from normal text. 
And you can easily find `python figlet` module at Google or pypi.

![pyfiglet](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/pyfiglet.png)

## Need to install dependent modules

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

This simple three-line-code is sufficient. This shows how simple Python is for developers.

Let's save this script as `pyfiglet_test.py`. Then we can run.

```sh
python pyfiglet_test.py
   __            __     __                               __
  / /____  _  __/ /_   / /_____     ________  ____  ____/ /__  _____
 / __/ _ \| |/_/ __/  / __/ __ \   / ___/ _ \/ __ \/ __  / _ \/ ___/
/ /_/  __/>  </ /_   / /_/ /_/ /  / /  /  __/ / / / /_/ /  __/ /
\__/\___/_/|_|\__/   \__/\____/  /_/   \___/_/ /_/\__,_/\___/_/
```

## Modifying the requirements.txt file with PyCharm for dependent module(s)
Let's go back to our `PyCharm` environment.

![01-requirements](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/01-requirements.png)

You can find a file named `requirements.txt` in the `asciiart` folder. This folder is a sub folder of `argoslabs` and of `myplugin`. This requirements.txt is the standard with Python to specify dependent modules and you get more information form this article, [How to install Python packages with pip and requirements.txt](https://note.nkmk.me/en/python-pip-install-requirements/).

You must add any dependent python modules to this 'requirements.txt' file.

Here is the example:

```sh
# pip dependent packages

# default for alabs
alabs.common

# for ASCII Art using Figlet
pyfiglet
```

> * Starting with `#` is the comment line.
> * **Please note that every plugin must include `alabs.common` as a dependent module**. **DO NOT SET specific version number** for this module as it grabs the latest one automatcially.
> * When you desire to set a specific version for the module, please do so like `pyfiglet==0.7`

Usually Python modules are designed to be cross-platform - meaning it would run Windows, Linux and MacOS. But sometimes, a specific modules needs to be installed and run for specific OS. 

For example, 

``` sh
# For Windows win32 dependent job : Windows ONLY!!!
pywin32; sys_platform == 'win32'
```

## Installing requirements.txt at PyCharm

![02-open-terminal](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/02-open-terminal.png)

After you modified `requirements.txt` let's try to install the dependent module(s) at this Python environment. 
To install this requirements, open the terminal from the context menu, `Open In > Terminal`.

> Please make sure you have set the `Python interpreter` at Project menu at settings in `PyCharm`.

![03-pip-install](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/04-dependent-modules/03-pip-install.png)

At `PyCharm`'s terminal you can run this command:

``` sh
pip install -r requirements.txt -i https://pypi-official.argos-labs.com/simple
```

> * `alabs.common` Python module exists in our [officai repository](https://pypi-official.argos-labs.com).
> * So next index option, `-i https://pypi-official.argos-labs.com/simple` needed for `pip install` command.

