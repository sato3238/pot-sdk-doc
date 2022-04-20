# Setting the package name

Python package consists with a folder with `__init__.py` file in it.

**IMPORTANT** ARGOS Low-Code plugin has the following naming rule:
* Package name has three sections separated by a period like `argoslabs.group.name`
* The first section must be `argoslabs` and this cannot be changed as it is the identifier in the ARGOS Low-code platform.
* You can set the group name, `group`. This can be any name as you like. However, making it meaningful to everyone is recommended.
* The `name` is the name of your plugin. ***However, this is NOT the display name on STU.*** Again, the more specific name is, the better.

> * `group` and `name` are only allowed with **lowercase alphabets and underbar character** which can be expressed by Regular Expression,  `[a-z_]`
> The POT SDK template has the package name of `argoslabs.demo.helloworld`
> Under `plugin-template` folder next folder structure may be seen as below:

```sh
plugin-template
+-- argoslabs
   +-- __init__.py
   +-- demo
      +-- __init__.py
      +-- helloworld
         +-- __init__.py
         +-- ...
```

![01-rename-second-level](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/03-naming/01-rename-second-level.png)

Firstly you can rename the `demo` group name with your own.
You can do it as follows:
> * Click the `demo` folder
> * Click the right button
> * Select `Refactor > Rename` or press `Shift + F6`

![02-rename-demo](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/03-naming/02-rename-demo.png)

You enter `myplugin` as example. 
> You can set proper group name as you wish like company name.

![03-rename-third](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/03-naming/03-rename-third.png)

Now it's time to rename `helloworld` - the plugin name.

![04-rename-hello.png](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/03-naming/04-rename-hello.png)

In this example we will change it to `asciiart`.

![05-check-changed](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/03-naming/05-check-changed.png)

You can see `argoslabs/myplugin/asciiart` folder structure at Project pane.

> Instead of changing the folder name manually, you CAN use `refactor > rename` functionality to change all referenced including comments automatically.

Whenever you build a new plugin you can start with this template.
