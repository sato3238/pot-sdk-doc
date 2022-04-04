# ARGOS-Labs POT SDK on Windows 10

This guide shows how to develop a plugin using ARGOS POT (`Python-to-Operations Tools`) SDK.

## Prerequisites

You need to install Python Interpreter and IDE

### [Install Python Interpreter](Install_Python_Interpreter_Windows10.md)

You need to install Python 3.7.3 32bit on Windows 10. Once you installed this interpreter it's enough to use this.

### [Install ARGOS POT SDK](Install_ARGOS_POT_SDK_Windows10.md)

ARGOS POT SDK consists of three parts as follows:

| Item | Minimum version | Role | Description |
|---|---|---|---|
| [alabs.common](https://pypi-official.argos-labs.com/#/package/alabs-common) | 3.721.1350 | SDK library | Library for SDK |
| [alabs.icon](https://pypi-official.argos-labs.com/#/package/alabs-icon) | 1.711.2351 | icon utility | This utility make plugin icon |
| [alabs.ppm](https://pypi-official.argos-labs.com/#/package/alabs-ppm) | 4.115.1700 | POT utility | POT main utility |


### [Installation of PyCharm IDE](Install_PyCharm_Windows10.md)

You can install one of Python [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment)
* `PyCharm` Community Edition

## How to build a ARGOS Low-Code Python Plugin

This guild shows how to build ARGOS Low-Code Python Plugin.

#### [Download template](Download_Template.md)

Everytime before starting you need to prepare base folder from `template` and need to set configuration for `PyCharm` IDE.
You can download a `Template` folder in which there are several files including 

#### [PyCharm settings](PyCharm_Settings_Windows10.md)
You need to set settings at the first time of after preparing template.

## Coding for plugin
Next Guide shows how to code from the scafolding template.

### [Set package name](Set_Package_name_Windows10.md)

You need to change python package name from `argoslabs.demo.helloworld` to `argoslabs.myplugin.asciiart` for example.

### [Sample code and dependent module](Install_Dependent_modules_Windows10.md)

When you make your own plugin you need to install third party dependent modules from [pypi.org](https://pypi.org). This guild shows how to do for this topic.

### [Main Coding at `__init__.py`](Main_Coding_Windows10.md)

Plugin's main code is made from the source, `argoslabs/myplugin/asciiart/__init__.py`.

### [Testing and Unique name](Testing_Windows10.md)

Every code need to be tested as much as possible. And package name like `argoslabs.gourp.plugin_name` and `STU`'s Icon display name must be unique.
This guild show you how to test plugin with unittest and check to have unique name. 

### [Tags and Version](Setup_yaml.md)
Before building plugin you have to set tags and version for that plugin.

### [Usage help with README.md](Usage_Help_with_README.md)
Each plugin must have a usage help so that shows this contents at STU link. This guide shows how to make this help contents.

## Build plugin

Now that everything is ready for build. Let's build.

### [Preparing private repository](Preparing_Private_Repository_Windows10.md)

After building a plugin you need to upload this plugin to your own Python private repository. This guide shows how to install private repository and configuration at Supervisor.

### [Build icon and plugin](build_icon_plugin_Windows10.md)
You have to prepare an image and make an icon using `alabs.icon` utility and then you can build this plugin with `build.bat` batch file.

## After making plugin

Once you build your own plugin it's time to make a bot at `STU` for testing. And you may need to upgrade the plugin if needed.

### [Test a bot at STU]()

Now your plugin is registered at private repository so you can make use of this plugin. This guide shows how to make a bot using your plugin.

### [How to upgrade plugin]()
Because plugin is a normal software it need to fix or upgrade if needed. This guide shows how to upgrade your plugin.
