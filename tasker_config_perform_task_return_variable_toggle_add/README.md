# tasker_config_perform_task_return_variable_toggle_add

This project provides a helper script to add `Reset Return Variable` toggle enable tag to all `Perform Task` actions inside tasks in the [Tasker App] `Data Backup` XML config file.

[Tasker 5.9.3.beta.6] introduced a feature or more accurately a way to solve a critical bug that has existed for a long time. 

A `Reset Return Variable` toggle has been added to the `Perform Task` action which when enabled will automatically unset any variable defined in the `Return Value Variable` field whenever the action is used to run a child task and the variable will only be set if the child task returns something with a `Return` action. If the toggle is disabled and as per the default for previous versions, the variable defined in the `Return Value Variable` field of the `Perform Task` action will not be automatically unset whether the child task uses a `Return` action or not.

`Reset Return Variable` Toggle Info:
The toggle exists in the following states in `Perform Task` action nodes which have the code `130`.

- `Reset Return Variable` toggle disabled: `<Int sr="arg8" val="0"/>`

- `Reset Return Variable` toggle enabled: `<Int sr="arg8" val="1"/>`

Check [Tasker Perform Task Docs]() for more details on the `Reset Return Variable` toggle.
##


### Contents
- [Compatibility](#Compatibility)
- [Dependencies](#Dependencies)
- [Downloads](#Downloads)
- [Usage](#Usage)
- [Current Features](#Current-Features)
- [Planned Features](#Planned-Features)
- [Issues](#Issues)
- [Worthy Of Note](#Worthy-Of-Note)
- [Changelog](#Changelog)
- [Contributions](#Contributions)
##


### Compatibility

- Android using [Termux App].
- Linux distros.
- Windows using [cygwin].
##


### Dependencies

- Android users should install [Termux App].
- Windows users should install [cygwin] and use cygwin shell to run scripts.
- `GNU` variant of `sed` should be installed in your system.
  - Termux (non-root shell): `apt install sed`
  - Linux distros: `sudo apt install sed`
  - Windows: It should ideally be installed by default with cygwin. If not, then run cygwin installer and search package and install.
##


### Downloads

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
##


### Usage

You may optionally run the script placed in the current directory without setting the ownership and permission by running the command `bash tasker_config_perform_task_return_variable_toggle_add`.
If you are not running the script in termux, set the shebang of the script correctly (the first line of the script).

The `current_config` file passed to the script must have been generated using the `Data->Backup` Tasker menu option or the `Data Backup` action. The script will not work with `autobackups` since those contain XML nodes that are collapsed to a single line with no indentations. If you have an `autobackup`, then import that into Tasker and export a backup manually again with one of the ways mentioned earlier. This does not apply for exported project, task, profile or scene files.

##### Help:

```
tasker_config_perform_task_return_variable_toggle_add command is used to add 'Reset Return Variable' \
toggle enable tag to all 'Perform Task' actions inside tasks in the Tasker \"Data Backup\" XML config \
file.

Usage:
  bash tasker_config_perform_task_return_variable_toggle_add current_config new_config

current_config should be the path to a Tasker \"Data Backup\" XML config file that you want to modify. \
It must be an exported \"Data Backup\" and not an auto backup.

new_config is the path to the output Tasker \"Data Backup\" XML config file.

Example Usage:
bash tasker_config_perform_task_return_variable_toggle_add backup.xml backup-new.xml


Any existing 'Reset Return Variable' toggle tags are removed before the enable tags are added. You \
will have to manually disable the toggle in any tasks that require it to be disabled after importing \
the new_config into tasker, depending on your task designs. 

Tags by default are not added to 'Perform Task' actions nested inside other actions like 'Notify' \
action or Scene Menu Elements since the result of tasks started by them is ignored and so the toggle \
doesn't apply to them.

When the command is run, by default a '$diff_output_file' file is generated that will contain the \
difference between the current_config and the new_config to show where the tags are added and removed. \
A '$perform_tasks_not_updated_file' file is also generated that will show which 'Perform Task' actions \
were not updated, ideally only the ones that were mentioned earlier. Make sure the new_config looks \
correct and report any bugs to the dev.


'Reset Return Variable' Toggle Info:
The toggle exists in the following states in 'Perform Task' action nodes which have the code 130.

'Reset Return Variable' toggle disabled:
<Int sr=\"arg8\" val=\"0\"/>

'Reset Return Variable' toggle enabled:
<Int sr=\"arg8\" val=\"1\"/>

The '<Int sr=\"arg8\" val=\"1\"/>' tag is added right after the '<code>130</code>' tag instead of \
at the end of the action node, since conditional statements may exist there and adding it at the start \
seems to be a universally reliable position to add it even for future Tasker versions. The order does \
not matter during import into Tasker and the config will be imported correctly. When you export a new \
backup from Tasker again, the order will be correct.
```
##


### Current Features

- Add `Reset Return Variable` toggle enable tag to all `Perform Task` actions inside tasks in a Tasker `Data Backup` XML config file
##


### Planned Features

`-`
##


### Issues

`-`
##


### Worthy Of Note

`-`
##


### Changelog

Check [CHANGELOG.md](../CHANGELOG.md) file for the **Changelog**.
##


### Contributions

`-`
##


[Tasker App]: https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm
[Tasker XML Info]: https://github.com/Taskomater/Tasker-XML-Info
[Termux App]: https://github.com/termux/termux-app
[cygwin]: https://cygwin.com/index.html
[Tasker 5.9.3.beta.6]: https://www.reddit.com/r/tasker/comments/gm3dl6/dev_tasker_593beta6_tasker_veterans_rejoice/
[Tasker Perform Task Docs]: 
