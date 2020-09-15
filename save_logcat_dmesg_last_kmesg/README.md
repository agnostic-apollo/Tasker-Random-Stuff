# Save logcat, dmesg and last_kmesg

This project provides a Tasker task that allows a user to save the logcat, dmesg and last_kmesg to a file in android storage.

Check [Save_logcat_dmesg_last_kmesg Task Info](Save_logcat_dmesg_last_kmesg.tsk.md) file for more info on the task.
##


### Contents
- [Compatibility](#Compatibility)
- [Dependencies](#Dependencies)
- [Downloads](#Downloads)
- [Install Instructions For Tasker In Android](#Install-Instructions-For-Tasker-In-Android)
- [Usage](#Usage)
- [Current Features](#Current-Features)
- [Planned Features](#Planned-Features)
- [Issues](#Issues)
- [Worthy Of Note](#Worthy-Of-Note)
- [Changelog](#Changelog)
- [Contributions](#Contributions)
##


### Compatibility

- Android using [Tasker App].
##


### Dependencies

- Reading logcat requires Tasker to be granted root or ADB access or `android.permission.READ_LOGS` permission.
- Reading dmesg or last_kmesg requires Tasker to be granted root or ADB access.

The `android.permission.READ_LOGS` permission can be granted to tasker over adb manually using `pm grant net.dinglisch.android.taskerm android.permission.READ_LOGS` command or use the script in [tasker_package_utils](https://github.com/Taskomater/tasker_package_utils) project which has a few more features.
##


### Downloads

Latest version is `v0.1.0`.

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
- [TaskerNet](https://taskernet.com/shares/?user=AS35m8mXdvaT1Vj8TwkSaCaoMUv220IIGtHe3pG4MymrCUhpgzrat6njEOnDVVulhAIHLi6BPUt1&id=Task%3ASave+logcat%3Bdmesg%3Blast_kmesg).
##


### Install Instructions For Tasker In Android

1. Import `save_logcat_dmesg_last_kmesg/Save_logcat_dmesg_last_kmesg.tsk.xml` Task file into Tasker.
##

### Usage

Set/Update variables in the `Set User Modifiable Variables*` section of the task and then run it either with a desktop shortcut or through Tasker task play button.

Check [Save_logcat_dmesg_last_kmesg Task Info](Save_logcat_dmesg_last_kmesg.tsk.md) file for more info on how to use the task.
##


### Current Features

- Save the logcat, dmesg and last_kmesg to a file in android storage.
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

Check [CHANGELOG.md](CHANGELOG.md) file for the **Changelog**.
##


### Contributions

`-`
##


[Tasker App]: https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm
