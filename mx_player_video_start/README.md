# MX Player Video Start

This project provides Tasker tasks that allows a user to start videos in [MX Player Ad App] or [MX Player Pro App] by sending intents through the [Tasker App].

Check [MX Player Api](https://sites.google.com/site/mxvpen/api) for more information on how to send an intent to MX Player.
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

- Requires [MX Player Ad App] or [MX Player Pro App] to be installed in the android phone.
##


### Downloads

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
##


### Install Instructions For Tasker In Android

1. Import `mx_player_video_start/MX_Player_Video_Start.tsk.xml` and `mx_player_video_start/Start_Video_With_MX_Player_Template.tsk.xml` Task files into Tasker.
##

### Usage

The `MX Player Video Start` task can be used to send an intent to MX Player Video Player on android to start a video with subtitles optionally. It requires video and an optional subtitle file path as parameters. The paths must be absolute unix file paths. Check the task's help anchor for more info on how to use it.

The `Start Video With MX Player Template` template task can be used to call the `MX Player Video Start` task. Set `%video_path` and optionally set the `%subtitle_path` and run the task. You may disable the `subtitle_path` variable set action if subtitles do not need to be passed.

Check [MX_Player_Video_Start Task Info](MX_Player_Video_Start.tsk.md) and [Start_Video_With_MX_Player_Template Task Info](Start_Video_With_MX_Player_Template.tsk.md) files for more info on how to use the tasks.
##


### Current Features

- Start a video in MX Player App by sending intents through the Tasker App.
- Allows subtitle to be optionally passed.
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
[MX Player Ad App]: https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.ad
[MX Player Pro App]: https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.pro
