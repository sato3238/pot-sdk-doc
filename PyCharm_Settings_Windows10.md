# PyCharm Settings

When you open a folder at PyCharm it create an folder named `.idea`. And all dependent settings and environments and status are saved in this `.idea` folder.

Next settings are usaful just after open a new folder to work with PyCharm.

![03-pycharm-settings](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/02-pycharm-settings/03-pycharm-settings.png)

You can get PyCharm `Settings..` menu iterm from `File` top menu.

![04-proj-interpreter-py37](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/02-pycharm-settings/04-proj-interpreter-py37.png)

For the first time it is needed to set python interpreter for this project. You can select a menu `Project: work` > `Project Interpreter`. And then you can see the default python interpreter located at `C:\work\py37\Scripts\python.exe`. If new created `Virtual Environment` is not exists under the project `C:\work` then you can add the interpreter this window - Click the right side icon of `Project Interpreter:` and select `add`.

![05-add-content-root](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/02-pycharm-settings/05-add-content-root.png)

Our source exists at `plugin-template` folder so it is needed to add `Content Root`.

1. Select `Project Structure` menu under `Project: work` at settings window.
2. Click `+ Add Content Root` of right side.
3. Select `plugin-template` folder.

![06-code-styles-80-columns](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/02-pycharm-settings/06-code-styles-80-columns.png)

[PEP-8](https://peps.python.org/pep-0008/) is very famous `Style Guide for Python Code`. PyCharm automatically guide this style guild at editor. One of style is that `Do not exceed 80 columns if possible`. So python programmers need the 80 columns guide rule at editor. You can do this functionality at the `Hard wrap at 80 columns` item of menu `Editor > Code Style`.

![07-typo-inspection-off](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/02-pycharm-settings/07-typo-inspection-off.png)

Sometimes program code do not follow correct english. To get rid of `Typo` warning at editor uncheck `Typo` check item at menu `Editor > Inspections > Spelling > Typo`.

> You can easily seach the item at left top text input control.

