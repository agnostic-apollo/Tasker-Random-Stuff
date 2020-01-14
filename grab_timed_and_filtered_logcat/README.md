# Grab Timed And Filtered Logcat

This project allows a user to capture logcats starting from the current time for the next x seconds using the [Tasker App]. It also allows capturing logcat entries of specific tags and also the usage of regexes to filter specific entries.
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

- No specific dependencies other than requires Tasker to be granted `android.permission.READ_LOGS`. Either grant it over adb manually using `pm grant net.dinglisch.android.taskerm android.permission.READ_LOGS` command or use the script in [tasker_package_utils](https://github.com/Taskomater/tasker_package_utils) project which has a few more features. Root users are automatically granted permissions by Tasker if required.
##


### Downloads

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
##


### Install Instructions For Tasker In Android

1. Import `grab_timed_and_filtered_logcat/Grab_Timed_And_Filtered_Logcat.tsk.xml` Task file into Tasker.
##

### Usage

Set/Update variables in the `Set User Modifiable Variables*` section of the task and then run it either with a desktop shortcut or through Tasker task play button.

Check [Grab_Timed_And_Filtered_Logcat](Grab_Timed_And_Filtered_Logcat.tsk.md) Task Info file for more info on how to use the task.
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

Check [CHANGELOG.md](../CHANGELOG.md) file for the **Changelog**.

##


### Contributions

`-`
##


[Tasker App]: https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm
