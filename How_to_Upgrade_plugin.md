# How to upgrade plugin (how to delete (end of life) your plugin)

There are many reasons to upgrade plugin:
* `Bug fix`: Mal-functional operation
* `Obsolete dependent module(s)`: Not operation for out of date dependent module
* `Need more function or enhancement`: Add/Modify input parameters and functions
* and many more reasons to upgrade plugin

This section will explain one exampole of the plugin update procedure. Maybe this is not for all of the cases but usually we follow next process.

## Finding (isolating) the problem

When some abnormal situation happens finding the exact problem clearly is the most important thing.

### Reproducing the problem

Most of error reports come from various users who use your plugin who runs it in various environment.
In this case first thing to do is to reproduce that problem at your environment. 
When you try to reproduce the problem, you have to know or gather as much information as possible:
* OS version and release: Windows 10 SP 2 (build xxxxx)
* Main Language: English, Korean, Japnanese, Chinese and so on
* Environmental Variables: %UserProfile%, %Temp%, ...
* ...

## How to solve the problem

Once you find the problem then you can solve the problem.
If you review the code which you made then you can solve easily.
However sometimes you have to maintain the code by others. 
In this case the first thing is that run the `tests\test_me.py` unittest code.
Usually these test cases contains all good and bad functionalities you can see the intention of the original code.

## Coding to fix the bug

You can modity the main `__init__.py` file.

### How to modify original code

Normally you can follow next procedures:
* Debug `test_me.py` test cases
* When you get some case of problem you can debug it
* If you cannot get the problem case then it is important to create the problem case at `test_me.py`
* You can have the breakpoints at source `__init__.py` and find problem at `PyCharm` debug mode
* Loop of Modify code, Debug test case

### How to add a new functionality

If someone request new functionality at this plugin you have to think these things:
* If possible do not change input design so previous running bot have no effects
* Add a new options or parameters for the new functionality 
* Add one or more new test cases at `test_me.py`

## Testing

The test cases at `test_me.py` is really important. Sometime we can say more important than code.
When test all cases regression testing is play the role.
Let's suppose that you have the 100 funcationalities and have 100 test cases. This plugin is working well during one year.
Now you just added a new functionality at your code and one more test case.
You are testing the 101 test cases. If the tests passed then it is lucky.
Usually even the new added case is passed some of the rest cases would not be passed by side effects.
We call this `regression testing`.
So let's create test cases not just success but also failure.

## Rewrite `setup.yaml` for version control

You have to do `version up` at `setup.yaml` file.

## Building the updated plugin

Building process is the same with the command `build.bat`.

## Testing the bot

If you have reproduced failure bot case you have to test that bot is working well after upgrade.

![01-plugin-version-STU](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/11-upgrade-plugin/01-plugin-version-STU.png)

Once you update your plugin you can see the versions at STU like above image. You can upgrade target version and `test run` the bot.

# How to delete (EOL) your plugin

ARGOS Low-code platform has a mechanism to collect usage data of all plugins. When your plugin (or a certain version of your plugin) has no usage record in the last 180 days, you can delete your plugin by following the procedure below.

1. Send a request for removal email to plugin_management@argos-labs.com
2. Receive usage stats and approval/disapproval for deletion
3. If approved, confirm removal by another email.
4. Your plugin (or a certain version(s) of the pluign) will be removed from service.
