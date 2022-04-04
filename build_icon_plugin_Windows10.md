# Build icon and plugin

## Build Icon

You can build an icon for this plugin from any image.

![01-search-icons](Captures/03-Make_Plugin_PyCharm/09-build/01-search-icons.png)

Let's search `ascii art icon` or `figlet icon` from google image search.
Any icon candidate is OK.

> Be careful with `Copyright`

![02-build-icon](Captures/03-Make_Plugin_PyCharm/09-build/02-build-icon.png)

You can build `icon.png` in `Terminal` with next command.
```sh
alabs.icon
```

`alabs.icon` tries to read configuration from `icon.yaml` file.

```yaml
---
merge_icons:
  - name: "myicon"
    from: icon-my.png
    size: 30
    localte: center
```
This icon.yaml says reading image from `con-my.png` and tries to shrink to 30 pixels and combine with a frame.

> * Please make any `icon-my.png` image. If extension is not `.png` convert it to `PNG`.
> * Please make background transparent `icon-my.png` image before running `alabs.icon`. This is because it is natural with the result of merging frame image.

You can see the `icon-my.png` image on left pane and result `icon.png` image on right pane.

## Build plugin

Now it is time to build this plugin after codeing, testing and making icon.

![03-build-bat](Captures/03-Make_Plugin_PyCharm/09-build/03-build-bat.png)

You can build this plugin by executing `build.bat` on `terminal`.

> * When you open `PyCharm`'s terminal the terminal is automatically ready to use python interpreter which we made as `VENV`(Virtual Environment), `C:\work\py37\Scripts\python.exe`.
> * You can do the same job at `CMD.EXE` just after activating `VENV` and go to the folder in which `build.bat` exists, `C:\work\plugin-template\argoslabs\myplugin\asciiart`.

The contents of `build.bat` is:
```sh
@echo off
REM !/bin/bash

set VB=-vvv

for /f %%i in ('alabs.ppm get repository') do set REP=%%i
for /f %%i in ('alabs.ppm get trusted-host') do set TH=%%i

pip install -U alabs.ppm -i %REP% --trusted-host %TH%

REM # clear
alabs.ppm --venv clear-all

REM test
alabs.ppm --venv %VB% test
IF NOT %ERRORLEVEL% == 0 (
	echo "test have error"
    goto errorExit
)

REM # build
alabs.ppm --venv %VB% build
IF NOT %ERRORLEVEL% == 0 (
	echo "build have error"
    goto errorExit
)

REM # submit to repository
REM alabs.ppm %VB% submit
REM IF NOT %ERRORLEVEL% == 0 (
REM 	echo "upload have error"
REM     goto errorExit
REM )

REM # upload to private repository
alabs.ppm --venv %VB% upload
IF NOT %ERRORLEVEL% == 0 (
	echo "upload have error"
    goto errorExit
)

REM # clear
alabs.ppm --venv clear-all

echo "Build all success!"

: errorExit
```

Here is the explanation of this `build.bat`:

* `pip install -U alabs.ppm -i %REP% --trusted-host %TH%` : This command update alabs.ppm utility as latest one.
* When `alabs.ppm` utility is trying to build the plugin it uses next `VENV`
  * If exists then delete the folder `%HOMEPROFILE%\py.win32`
  * Making a new `VENV` at `%HOMEPROFILE%\py.win32`
  * Just after `VENV` created this `VENV` is empty third party module
* `alabs.ppm --venv clear-all` : Clear the folder `%HOMEPROFILE%\py.win32`
* `alabs.ppm --venv %VB% test` : Install dependent module[s] and testing the `test_me.py`
* `alabs.ppm --venv %VB% build` : Making one [wheel](https://pypi.org/project/wheel/0.22.0/) Python module file. Similar to `python setup.py bdist_wheel` command
* `alabs.ppm --venv %VB% upload` : You registered your private repository at [supervisor's private plugin menu](https://rpa.argos-labs.com/#/plugin/private-plugin). After successful building `wheel` file you can upload this plugin Python module and use at `STU`.

> "`alabs.ppm %VB% submit` " command is commented out because of under preparation. This is a request to publish to [Official Repository](https://pypi-official.argos-labs.com).

![04-userid-password-sv](Captures/03-Make_Plugin_PyCharm/09-build/04-userid-password-sv.png)

When running `build.bat` two prompts happen:
* `upload command need user id for ARGOS RPA, User ID? ` - Enter ***Supervisor's User ID***
* `upload command need user password for ARGOS RPA, User Password? ` - Enter ***Supervisor's User Password***

> If you already have one or more private repositories then re-order to first position. This is because when plugin is being built it tries to upload to the ***FIRST private repository***.


![05-build-success](Captures/03-Make_Plugin_PyCharm/09-build/05-build-success.png)

At the end of `build.bat` running you can see:
```text
"Build all success!"
```
All process is done by one command `build.bat`. If you cannot see this result you have to solve problem[s].

## Check plugin at private repository

![06-check-upload](Captures/03-Make_Plugin_PyCharm/09-build/06-check-upload.png)

You can see the uploaded plugin Python module at your `private repository`. `
![07-detailed-list](Captures/03-Make_Plugin_PyCharm/09-build/07-detailed-list.png)

pypicloud` can see the module lists and go into to see more detailed versions.

![08-pypi-simple](Captures/03-Make_Plugin_PyCharm/09-build/08-pypi-simple.png)

Normal `Python private pypi server` is accessced by the following scheme:
Optional `username` and `password` and host and `/simple`
Example) `https://username:passw0rd@localhost:6543/simple`

When you open this `URI` then you can see all simple list of modules stored in this private repository.

> You can install python module from this repository using next command.

``` sh
pip install -i https://localhost:6543/simple
```

> `alabs.ppm` utility all manage these jobs at backend.

