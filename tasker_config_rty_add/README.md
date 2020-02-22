# tasker_config_rty_add

This project provides a helper script to fix [Tasker App] configs of users who updated from Tasker v5.8.5 to v5.9.beta.3 and had their collision handling messed up because the update removed all `<rty>2</rty>` tags.

The Tasker config stores the collision handling option of each task in the `<rty>` tags of the Task node.

```
<rty>0</rty> or "no tags" == Abort New Task

<rty>1</rty> == Abort Existing Task

<rty>2</rty> == Run Both Together
```

The script finds all tasks with `Run Both Together <rty>2</rty>` tags in an old config file and then adds the same tag to all tasks in the current config file overriding any existing `<rty>` tags of the tasks found.

Note that the `<rty>` tags are added before the `<pri>` tags but you can export another backup from Tasker to fix the order, it shouldn't matter during importing the new config to tasker.

The script can also work to add `<rty>1</rty>` instead by changing the `rty_number` variable to `1` in the script.

Check [Tasker XML Info] for more info on how Tasker App XML files work.
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

You may optionally run the script placed in the current directory without setting the ownership and permission by running the command `bash tasker_config_rty_add`.
If you are not running the script in termux, set the shebang of the script correctly (the first line of the script).

Set `old_config`, `current_config` and `new_config` variables in the script to the names or paths of the tasker configs.

Both the `old_config` and `current_config` tasker configs passed to the script must have been generated using the `Data->Backup` Tasker menu option or the `Data Backup` action. The script will not work with `autobackups` since those contain XML nodes that are collapsed to a single line with no indentations. If you have an `autobackup`, then import that into Tasker and export a backup manually again with one of the ways mentioned earlier.

Run script in your android device or linux distro or cygwin in windows:
```
bash tasker_config_rty_add
```
##


### Current Features

- Transfer rty tags values from one Tasker config to another.
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
