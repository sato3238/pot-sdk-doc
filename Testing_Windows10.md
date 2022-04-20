# Testing your code and validating your file and plugin names for uniqueness

Plugin's test code exists at the source code file named `argoslabs/myplugin/asciiart/tests/test_me.py`.
There are good ways to test with several testing frameworks.
We are using [unittest](https://docs.python.org/3.7/library/unittest.html).

Below shows the full version of `test_me.py`.

```python
"""
====================================
 :mod:`argoslabs.myplugin.asciiart`
====================================
.. moduleauthor:: Your Name <name@yours>
.. note:: ARGOS-LABS License

Description
===========
ARGOS LABS plugin module to use Selenium
"""
# Authors
# ===========
#
# * Your Name
#
# Change Log
# --------
#
#  * [2022/02/02]
#     - starting

################################################################################
import os
import sys
from unittest import TestCase
from argoslabs.myplugin.asciiart import _main as main


################################################################################
class TU(TestCase):
    # ==========================================================================
    def setUp(self) -> None:
        os.chdir(os.path.dirname(__file__))

    # ==========================================================================
    def test0000_init(self):
        ...

    # ==========================================================================
    def test0010_fail_empty(self):
        # sg = sys.gettrace()
        # if sg is None:  # Not in debug mode
        #     print('Skip testing at test/build time')
        #     return
        try:
            _ = main('')
            self.assertTrue(False)
        except Exception as e:
            sys.stderr.write('\n%s\n' % str(e))
            self.assertTrue(True)

    # ==========================================================================
    def test0110_success(self):
        of = 'stdout.txt'
        try:
            r = main('standard',
                     'Hello world?',
                     '--outfile', of)
            self.assertTrue(r == 0)
            with open(of) as ifp:
                rs = ifp.read()
                print(rs)
            self.assertTrue(rs.strip() == r''' _   _      _ _                            _     _ ___ 
| | | | ___| | | ___   __      _____  _ __| | __| |__ \
| |_| |/ _ \ | |/ _ \  \ \ /\ / / _ \| '__| |/ _` | / /
|  _  |  __/ | | (_) |  \ V  V / (_) | |  | | (_| ||_| 
|_| |_|\___|_|_|\___/    \_/\_/ \___/|_|  |_|\__,_|(_) 
                                                       
'''.strip())
        except Exception as e:
            sys.stderr.write('\n%s\n' % str(e))
            self.assertTrue(False)
        finally:
            if os.path.exists(of):
                os.remove(of)

    # ==========================================================================
    def test0120_success_font(self):
        of = 'stdout.txt'
        try:
            r = main('slant',
                     'Hello world?',
                     '--outfile', of)
            self.assertTrue(r == 0)
            with open(of) as ifp:
                rs = ifp.read()
                print(rs)
            self.assertTrue(rs.strip() == r'''    __  __     ____                             __    _____ 
   / / / /__  / / /___     _      ______  _____/ /___/ /__ \
  / /_/ / _ \/ / / __ \   | | /| / / __ \/ ___/ / __  / / _/
 / __  /  __/ / / /_/ /   | |/ |/ / /_/ / /  / / /_/ / /_/  
/_/ /_/\___/_/_/\____/    |__/|__/\____/_/  /_/\__,_/ (_)   
                                                            
'''.strip())
        except Exception as e:
            sys.stderr.write('\n%s\n' % str(e))
            self.assertTrue(False)
        finally:
            if os.path.exists(of):
                os.remove(of)

    # ==========================================================================
    def test0130_success_direction(self):
        of = 'stdout.txt'
        try:
            r = main('slant',
                     'Hello world?',
                     '--direction', 'right-to-left',
                     '--outfile', of)
            self.assertTrue(r == 0)
            with open(of) as ifp:
                rs = ifp.read()
                print(rs)
            self.assertTrue(rs.strip() == r'''                       ___      ____                            ____     __  __
                      /__ \____/ / /________ _      __   ____  / / /__  / / / /
                       / _/ __  / / ___/ __ \ | /| / /  / __ \/ / / _ \/ /_/ / 
                      /_// /_/ / / /  / /_/ / |/ |/ /  / /_/ / / /  __/ __  /  
                     (_) \__,_/_/_/   \____/|__/|__/   \____/_/_/\___/_/ /_/   
                                                                               
'''.strip())
        except Exception as e:
            sys.stderr.write('\n%s\n' % str(e))
            self.assertTrue(False)
        finally:
            if os.path.exists(of):
                os.remove(of)

    # ==========================================================================
    def test0140_success_justify(self):
        of = 'stdout.txt'
        try:
            r = main('slant',
                     'Hello world?',
                     '--width', '44',
                     '--outfile', of)
            self.assertTrue(r == 0)
            with open(of) as ifp:
                rs = ifp.read()
                print(rs)
            self.assertTrue(rs.strip() == r'''    __  __     ____    
   / / / /__  / / /___ 
  / /_/ / _ \/ / / __ \
 / __  /  __/ / / /_/ /
/_/ /_/\___/_/_/\____/ 
                       
                      __    _____ 
 _      ______  _____/ /___/ /__ \
| | /| / / __ \/ ___/ / __  / / _/
| |/ |/ / /_/ / /  / / /_/ / /_/  
|__/|__/\____/_/  /_/\__,_/ (_)   
                                  
'''.strip())
        except Exception as e:
            sys.stderr.write('\n%s\n' % str(e))
            self.assertTrue(False)
        finally:
            if os.path.exists(of):
                os.remove(of)

    # ==========================================================================
    def test9999_quit(self):
        self.assertTrue(True)

```

We are using [uniitest](https://docs.python.org/3.7/library/unittest.html), [TestCase](https://docs.python.org/3.7/library/unittest.html#unittest.TestCase).

## Structure of test case

### import _main for the plugin

```python
from argoslabs.myplugin.asciiart import _main as main
```

You must refer to _main function of proper Python package like `argoslabs.myplugin.asciiart`.

### Test case method

* Every methods starting with `test...()` methods are tested in the ascending order of alphabet. 
* [setUp()](https://docs.python.org/3.7/library/unittest.html#unittest.TestCase.setUp) method is a special method which called befoce every test case methods. 

```python
    def setUp(self) -> None:
        os.chdir(os.path.dirname(__file__))
```
Usually this setup is changing the working folder of `tests` so reading or writing files using relative path.

Every test case have to check the _main(...) result code.

```python
            r = main(...)
            self.assertTrue(r == 0)
```
This return code is the same as plugin's return code.
* `0` - On success
* `None 0` - Otherwise Error

```python
            r = main('slant',
                     'Hello world?',
                     '--width', '44',
                     '--outfile', of)
            self.assertTrue(r == 0)
            with open(of) as ifp:
                rs = ifp.read()
            self.assertTrue(rs == r'...')
```    
* `--outfile` is the saved file from plugin `STDOUT` output. This result is the passed to `PAM` so in this test you can test in this function working well or not
* The most common advantage in this testcase is that we can use `IDE`'s debugging method.

> When you update (fix bugs, add new function, or modify original code) plugin's code this test case is extremely important.
> Naturally, you add a new test case for the new functionality. However, testing for all of the previous test cases must be performed for every update. We call this [Regression testing](https://en.wikipedia.org/wiki/Regression_testing).

## Debugging of testing
![02-debug-unittest](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/06-testing/02-debug-unittest.png)

Two kinds of testing is possible:
* Outside of `TestCase` we can debug whole test cases like above example image.
* When the cursor is in one of the test function and right click and select `Debug` then you can debug only that function.

![03-check-all-passed](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/06-testing/03-check-all-passed.png)

When you test all cases you can see the process of passed or not at the left bottom side on `PyCharm` like above capture image.

> You have to make sure every test case is passed. If not, the plugin build-up will fail.

## How to validate the uniqueness of your package name and the display name
![04-check-unique-name](https://raw.githubusercontent.com/Jerry-Chae/pot-sdk-doc/main/Captures/03-Make_Plugin_PyCharm/06-testing/04-check-unique-name.png)

You can open `Terminal` from the context menu, `Open with > Terminal` on right click of folder `asciiart`.
And run this command,

```sh
(py37) C:\work\plugin-template\argoslabs\myplugin\asciiart>alabs.ppm plugin unique
Package "argoslabs.myplugin.asciiart" and Display name "ASCII Art" seems OK to use.
```

* `(py37)` prompt means that you are in `py37` virtual environment.
* If there is an error message for this package name or display name please change it. Repeat until no error has been found.

> * This `alabs.ppm plugin unique` command may takes long time - often more than 5 minutes because getting all modules from [official repository](https://pypi-official.argos-labs.com)
> * Note that this uniqueness is checking only with `official repository` not `private repositories`. **Your responsibility to check the uniqueness**.
> * New version of `PyCharm` changed from `CMD.EXE` into `PowerShell`. So there may be no `(py37)` virtual environment prompt.

