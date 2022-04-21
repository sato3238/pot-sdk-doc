# Build a test bot using your new plugin with STU

Congratulations. Now your plugin is registered (uploaded) at the private repository so you can make use of it in the ARGOS Low-code platform. This section shows how to build a test bot using your plugin.

To make a test bot with the plugin which you created you need to install `STU` and `PAM` and register (sign up) at `Supervisor`. 


![01-login-STU](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/01-login-STU.png)

If your `STU` is already open, please close it and restart. STU sign-in credentials are the same as your Supervisor account credentials.

![02-private-plugin](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/02-private-plugin.png)

**Please be patient when you have a new plugin** - Everytime STU starts he will try to see if there is any change in your toolbox such as addition of a new plugin --- it checks the data from both [official repository](https://pypi-official.argos-labs.com) and private repositories registered at [supervisor's private plugin menu](https://rpa.argos-labs.com/#/plugin/private-plugin). If it's first time to run the `STU` then it may take more than a few minutes. And afterwards this checking time will be reduced to a few seconds because the toolbox data is cached. 

You can find your plugin `ASCII Art` at the last of `Operations`, `Plugins-private` group.

> * Your plugin's display name is `ASCII Art` but above name is `(P)ASCII Art`. `(P)` means private.
> * If you want your plugin is going to publish to [official repository](https://pypi-official.argos-labs.com) then please ask us to publish.
> * Once your plugin is published to `official repository` the `(P)` prefix will be dissapeared.
> * If your plugin is exists both at `official repository` and `private repository`:
>   * Same or grater version exists at `official repository` then no `(P)` prefix exists
>   * Greater version exists at `private repository` then `(P)` prefix exists

![03-asciiart-properties](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/03-asciiart-properties.png)

If you drag and drop your `(P)ASCII Art` plugin at `Operations` to `Timeline then you can see above image at your `STU`. There is a Properties pane at the right side. Let's set next things:
* `Message`: Any message is OK, above example is `Hi ASCII?`
* `Return value` section: Save the result as `{{my.a}}` variable
  * `Result Type`: `String`
  * `VariableName`: `{{my.a}}`


![04-run-notepad](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/04-run-notepad.png)

We will add two more operations to get the result of `(P)ASCII Art` plugin. 
Firstly search `run` at the right to `Operation` and the drag and drotp the `Run Program` operation.
And then at `Properties` pane:
* `File Path`: `notepad`

This means run empty `notepad` application.

![05-text-input](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/05-text-input.png)

Secondly search `input` at the right to `Operation` and the drag and drotp the `Text Input` operation.
And then at `Properties` pane:
* `Input type`: `UserVariable`
* `Paste Icon`: checked
* At drop down box: select `{{my.a}}`

![06-testrun](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/06-testrun.png)

Now that is all to make a testing bot.
To run this bot, `Test run` from `Run` menu or press `F5`.

![07-result](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/07-result.png)

**IMPORTANT** Preparation of `Virtual Environment`can take some time depending on what Python modules your bot will be referencing. But please do not worry. This is just for the very first time. Second time on, the local `Virtual Environment` can be used without re-construction. 

You can see the result at the `Notepad` app as above example.
