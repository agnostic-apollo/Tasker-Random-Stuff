# Grab Timed And Filtered Logcat

This project provides a Tasker task that allows a user to capture logcats starting from the current time for the next x seconds using the [Tasker App]. It also allows capturing logcat entries of specific tags and also the usage of regexes to filter specific entries. Check [Grab_Timed_And_Filtered_Logcat Task Info](Grab_Timed_And_Filtered_Logcat.tsk.md) file for more info on the task.
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

The `android.permission.READ_LOGS` permission can be granted to tasker over adb manually using `pm grant net.dinglisch.android.taskerm android.permission.READ_LOGS` command or use the script in [tasker_package_utils](https://github.com/Taskomater/tasker_package_utils) project which has a few more features.
##


### Downloads

Latest version is `v0.3.0`.

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
- [TaskerNet](https://taskernet.com/shares/?user=AS35m8mXdvaT1Vj8TwkSaCaoMUv220IIGtHe3pG4MymrCUhpgzrat6njEOnDVVulhAIHLi6BPUt1&id=Task%3AGrab+Timed+And+Filtered+Logcat).
##


### Install Instructions For Tasker In Android

1. Import `grab_timed_and_filtered_logcat/Grab_Timed_And_Filtered_Logcat.tsk.xml` Task file into Tasker.
##

### Usage

Set/Update variables in the `Set User Modifiable Variables*` section of the task and then run it either with a desktop shortcut or through Tasker task play button.

Check [Grab_Timed_And_Filtered_Logcat Task Info](Grab_Timed_And_Filtered_Logcat.tsk.md) file for more info on how to use the task.
##


### Current Features

- Grab a logcat for x seconds with custom tag filters.
- Apply regex filters.
- Write unfiltered and filtered logcat output to log files.
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
