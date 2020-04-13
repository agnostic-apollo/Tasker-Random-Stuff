# Format Task Description For Markdown

This project provides a Tasker task to format an exported tasker task description/code into a more readable and markdown compatible format for websites like reddit and github.

For basic usage, just run the task provided after running `Export` -> `Description To Clipboard` on a task and it will read the description from the `%CLIP` variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents. Automatic conversion to markdown code block by default is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default.

Depending on the number of actions and the device specs, it will take a few seconds to format the description.
##


### Contents
- [Compatibility](#Compatibility)
- [Dependencies](#Dependencies)
- [Downloads](#Downloads)
- [Install Instructions For Tasker In Android](#Install-Instructions-For-Tasker-In-Android)
- [Usage](#Usage)
- [Example Output Of Formatted Task Description](#Example-Output-Of-Formatted-Description)
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

`-`
##


### Downloads

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
##


### Install Instructions For Tasker In Android

1. Import `format_task_description_for_markdown/Format_Task_Description_For_Markdown.tsk.xml` Task file into Tasker.
##

### Usage

Check [Format_Task_Description_For_Markdown Task Info](Format_Task_Description_For_Markdown.tsk.md) file for more info on how to use the task.
##


### Example Output Of Formatted Description

Check [Example_Output_Of_Formatted_Task_Description](Example_Output_Of_Formatted_Task_Description.md) file for an example of the formatted task description.
##


### Current Features

- Replaces all pre-existing indents with spaces by default.
- Automatically increases indents for `If` and `For` related actions with support for capping indents at a max indent character count.
- Allows prefixing and suffixing the formatted description with required number of backticks to create a markdown code block. 
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
