# Make a testing bot at STU

Now your plugin is registered at private repository so you can make use of this plugin. This guide shows how to make a bot using your plugin.

To make a testing bot with the plugin which you created you need to install `STU` and `PAM` and register at `Supervisor`. 


![01-login-STU](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/01-login-STU.png)

If you start `STU` then above `login` page shows up. Please enter **your** `Supervisor` account to sign in.

![02-private-plugin](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/10-make_bot/02-private-plugin.png)

Just after signing in `STU` it starts detecting plugins from [official repository](https://pypi-official.argos-labs.com) and private repositories registered at [supervisor's private plugin menu](https://rpa.argos-labs.com/#/plugin/private-plugin). If it's first time to run the `STU` then it may take more than a few minutes. And afterwards this checking time will be reduced to a few seconds because of cache. 

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

At the first time to run this `bot` it takes a few more seconds to build `Virtual Environment` for this bot. 

You can see the result at the `Notepad` app as above example.
