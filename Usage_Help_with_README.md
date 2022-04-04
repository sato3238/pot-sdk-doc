# Help document with README.md

`.md` file extension is for [MarkDown](https://www.markdownguide.org/) document.
Our [Github plugin source](https://github.com/Jerry-Chae/plugins) also has the [README.md](https://github.com/Jerry-Chae/plugins/blob/main/README.md) and shows translated result markdown document automatically. This is true for every sub folders which have the `README.md`.

# Help document template

Next markdown document shows the template.

```md
# Plugin Display Name

***Description of this plugin***

> Note: ...

## Name of the plugin
Item | Value
---|:---:
Icon | ![Plugin Name](icon.png) 
Display Name | **Plugin Name**

## Name of the author (Contact info of the author)

Your Name
* [email](mailto:name@your.com)
* [github](https://github.com/your)

## Notification

### Dependent modules
Module | Source Page | License | Version (If specified otherwise using recent version will be used)
---|---|---|---
[dep-module]() | [dep-module]() | [MIT](https://github.com/ssut/py-googletrans/blob/master/LICENSE) | 4.0

> * Note

## Warning 
No potential damage to customer files and data (overwrite risk)

## Helpful links to 3rd party contents
None

## Version Control 
* [3.705.2300](setup.yaml)
* Release Date: `Jul 5, 2021`

## Input (Required)
Display Name | Input Method | Default Value | Description
---|---|---|---
msg | | | message to translate

> * Note

## Input (Optional)

Display Name | Show Default | Input Method | Default Value | Description
---|---|---|---|---
Text file | True | fileread | | Text file to read message
File Encoding | False | | utf8 | File encoding for text file
Target lang | True | choices | English | Destination language to use

> * Note

## Return Value

### Normal Case
Description of output result

## Return Code
Code | Meaning
---|---
0 | Success
99 | Exceptional case

## Parameter setting examples (diagrams)
If any STU example capture images.
```

Next is the example [README.md](https://github.com/Jerry-Chae/plugins/blob/main/argoslabs/google/translate/README.md) for [argoslabs.google.translate](https://github.com/Jerry-Chae/plugins/tree/main/argoslabs/google/translate).

> * Currently STU have the seperate help contents for the plugin.
> * We have a plan to show this README.md help contents for plugin in the near future.