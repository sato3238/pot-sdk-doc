# ARGOS RPA+ Python Plugin Developers

This page explains how to build `ARGOS RPA+ Python plugin` and use `POT (Python-to-Operation Tools)`.

## Prerequsites

### Windows 10 or Linux or Mac
> However most example are tested in Windows 10

### Make sure python 3.7 is installed on system

### Make a virtual environment for Plugin

Usually Next commands are running in CMD.EXE in Windows 10.

#### Make a virtualenv

```bash
python -m venv C:\work\py3
```
> Example directory is `C:\work\py3`. You can change it what you want

#### Activate the virtualenv
```bash
C:\work\py3\Scripts\activate
```

> After activating the prompt starts with the name of virtual environment. In above example the prompt looks like `(py3) C:\>`


## Install the SDK

Next commands are run in the virtual environment.

```bash
pip install -U alabs.ppm alabs.icon --index https://pypi-official.argos-labs.com/pypi
```

> You can upgrade as well as install with `-U` option

### Check version

```bash
pip list
```

To check versions for SDK enter above command.

```bash
Package             Version------------------- ----------alabs.common        1.920.1030alabs.icon          1.711.2351alabs.ppm           1.809.1820
```
SDK consists with three parts as follows:

| Item | Minimum version | Role | Description |
|---|---|---|---|
| alabs.common | 1.920.1030 | SDK library | Library for SDK |
| alabs.icon | 1.711.2351 | icon utility | This utility make plugin icon |
| alabs.ppm | 1.809.1820 | POT utility | POT main utility |


## How to build Plugin

### Need Python IDE

Usually python developer using one of these IDE (Integrated Development Environment).

* [PyCharm](https://www.jetbrains.com/pycharm/)
* [Visual Studio Code for Python](https://code.visualstudio.com/docs/languages/python)

### Download Template code

[Download plugin demo]()

### Unzip and open in IDE
* unzip above zip file
* open top `plugin-demo` at your IDE

### Change python Package name
* Above template has the python package `your.demo.helloworld`
* Change this package as you want like `my.api.crm`
* Two parts changed with the new package name.
	* \_\_main__.py : change `from your.demo.helloworld import main` into `from my.api.crm import main`
	* setup.yaml : change `your.demo.helloworld: ['icon.*']` into `my.api.crm: ['icon.*']`
	* test_me.py : change `from your.demo.helloworld import _main as main` into `from my.api.crm import _main as main`
	
### Design user arguments and result

ARGOS RPA+ Python plugin is regarded as a CLI (Command line interface) program. User run CLI program with arguments as user input and the output is the result. 

So plugin developer must design user arguments and result.

#### How to design user arguments

You can specify user arguments at function `_main()` in `__init__.py` file.

Before you change,

```python
################################################################################def _main(*args):    """    Build user argument and options and call plugin job function    :param args: user arguments    :return: return value from plugin job function    """    with ModuleContext(        owner='YOUR-LABS',        group='demo',        version='1.0',        platform=['windows', 'darwin', 'linux'],        output_type='text',        display_name='My World',        icon_path=get_icon_path(__file__),        description='Hello World friends',    ) as mcxt:        # ##################################### for app dependent parameters        mcxt.add_argument('name', nargs='+', help='name to say hello')        argspec = mcxt.parse_args(args)        return helloworld(mcxt, argspec)
```

Change into,

```python
################################################################################def _main(*args):    """    Build user argument and options and call plugin job function    :param args: user arguments    :return: return value from plugin job function    """    with ModuleContext(        owner='MyCompany',        group='api',        version='1.0',        platform=['windows', 'darwin', 'linux'],        output_type='text',        display_name='CRM Op',        icon_path=get_icon_path(__file__),        description='Our Company CRM API',    ) as mcxt:        # ######################################## for app dependent options        mcxt.add_argument('--type', '-t',                          display_name='Value Type', show_default=True,                          choices=["auto", "string", "int", "float", "date", "datetime"],                          default='auto',                          help='Set Value type, one of {"auto", "int", "float", "date", "datetime"}.'                               ' Default is auto which means try to guess the best type of value')        mcxt.add_argument('--date-format',                          display_name='Date Format',                          choices=list(BinOp.DATE_FORMAT.keys()),                          default='YYYYMMDD',                          help='Set the format of Date')        mcxt.add_argument('--datetime-format',                          display_name='DateTime Format',                          choices=list(BinOp.DATETIME_FORMAT.keys()),                          default='YYYYMMDD-HHMMSS',                          help='Set the format of DateTime')        # ##################################### for app dependent parameters        mcxt.add_argument('left',                          display_name='Left Val',                          help='Left operand for binary operation')        mcxt.add_argument('operation',                          display_name='Operator',                          choices=['+', '-', '*', '/', '%'],                          help='Binary operation, one of "+(add),-(subtract),*(multiply),/(divide),%%(modular)"')        mcxt.add_argument('right',                          display_name='Right Val',                          help='Right operand for binary operation')        argspec = mcxt.parse_args(args)        return do_binop(mcxt, argspec)
```

Where as,

* `ModuleContext` instance defines plugin and attributes. User arguments are defined using `mcxt.add_argument` method (mcxt is the `ModuleContext` instance variable).
* [`mcxt.add_argument`](https://docs.python.org/3.7/library/argparse.html#argparse.ArgumentParser.add_argument) is the superset of Python [argparse standard library](https://docs.python.org/3.7/library/argparse.html)
* In addition to `add_argument` of standard argparse library next arguments are can be added.
	* `display_name` is the label in STU
	* Options are usually not show in default in STU but in advanced group. If `show_default` is true then this option is shows default in STU
	* `input_method` specify how to input from user in STU
		* `password` shows '*' characters for password
		* `fileread` shows file dialog to read a file
		* `fileread;xlsx` shows file dialog to read a file which have the extension of `xlsx`
		* `filewrite` shows file dialog to wirte a file
		* `filewrite;txt,pdf` shows file dialog to wirte a file which have the extension one of `txt` or `pdf`
		* `folderread` shows folder dialog to read
		* `folderwrite` shows folder dialog to write
		* `dateselect` shows date picker dialog
		* `textarea` shows multiple text input control
		* `radio` shows radio button according to group (refer to `input_group`)
		* `combobox` shows combobox for choice
		* `imagebox` shows image
	* `input_group` is used for grouping in STU
		* "groupname" is the grouping name which is used for the group of arguments
		* "groupname;`groupbox`" shows group box named "groupname"
		* "`radio=`a" shows group of radio buttons named "a"
		* "`radio=`a`;default`" shows group of radio button as a default
	* `min_value` or `greater_eq` check the user input value is greater than or equal to given value
	* `max_value` or `less_eq` check the user input value is less than or equal th given value
	* `greater` or `min_value_ni` check the user input value is greater than given value
	* `less` or `max_value_ni` check the user input value is less than given value
	* `equal` check the user input value is equal to given value
	* `not_equal` check the user input value is not equal to given value
	* `re_match` check the user input value is RE matched for given value

#### How to design result

You can change user function body `helloworld()` into `do_binop()` in `__init__.py` file.

Before you change,

``` python
################################################################################@func_logdef helloworld(mcxt, argspec):    """    plugin job function    :param mcxt: module context    :param argspec: argument spec    :return: True    """    mcxt.logger.info('>>>starting...')    print('Hello world %s' % argspec.name)    mcxt.logger.info('>>>end...')    return 0```

Change into,

```python
################################################################################@func_logdef do_binop(mcxt, argspec):    mcxt.logger.info('>>>starting...')    try:        bo = BinOp(argspec, logger=mcxt.logger)        r = 0  # 0 means success        return r    except Exception as e:        msg = 'argoslabs.filesystem.op Error: %s' % str(e)        mcxt.logger.error(msg)        sys.stderr.write('%s%s' % (msg, os.linesep))        raise    finally:        mcxt.logger.info('>>>end...')```

Where as,

* Plugin result is the Python's standard output (like `sys.stdout` or `print`)
* mcxt is the `ModuleContext` instance
	* mcxt.logger is the [logger object](https://docs.python.org/3/library/logging.html)
* This function return 0 on success otherwise failure

### How to test

You can add each unittest methods in TU class in `test_me.py`.
POT can test this testing at building this plugin.

### Set version

Set `version: 1.22.333` at `setup.yaml` file.

### How to build icon

* Change `my-icon.png` image file with your own
* Open `CMD.EXE` (or terminal in Linux or Mac)
* Activate virtual env (like `C:\work\py3\Script\activate`)
* Run command `alabs.icon`
* Make sure `icon.png` image created. This image file will be used at STU plugin icon.

### Before build plugin (for private plugin repository)

* Make your own python private repository, choose one of deployment
	* [How to Create a Private Python Package Repository](https://www.linode.com/docs/applications/project-management/how-to-create-a-private-python-package-repository/)
	* [How To Install A Private Pypi Server On AWS](https://medium.com/swlh/how-to-install-a-private-pypi-server-on-aws-76993e45c610)
	* [Pypiserver - minimal PyPI server for use in docker container](https://github.com/pypiserver/pypiserver)

* Sign-up or Sign-in at [rpa.argos-labs.com](https://rpa.argos-labs.com/)
* Go to the `Plugins` page and `Private` tab in left menu list
* Add your private repository
	* `name`: plugin name
	* `url`: set as pypi url (like `http://my.pypi.com/simple` or `https://my.pypi.com/pypi`)
	* `user`: user for private plugin
	* `password`: password for the user

### How to build plugin and upload to private plugin repository

* Open `CMD.EXE` (or terminal in Linux or Mac)
* Activate virtual env (like `C:\work\py3\Script\activate`)
* Run command `build.bat` (or `build.sh` in Linux or Mac). This batch file running next commands using POT utility, `alabs.ppm`
	* `alabs.ppm --venv test`: Try to test plugin if error happen exit
	* `alabs.ppm --venv build`: Try to build plugin if error happen exit
	* `alabs.ppm --venv upload`: Try to upload to the first private plugin repository list in Chief page (refer above site, [rpa.argos-labs.com](https://rpa.argos-labs.com/))

## STU plugin use

* Login to STU (if already logged in STU then logout and login again)
* Make sure new plugin appear in STU operation list
* Use the plugin
