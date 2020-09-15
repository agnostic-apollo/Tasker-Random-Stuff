# Format Task Description For Markdown

This project provides a Tasker task to format an exported tasker task or profile description/code into a more readable and markdown compatible format for websites like reddit and github.

For basic usage, just run the task provided after running `Export` -> `Description To Clipboard` on a task and it will read the description from the `%CLIP` variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents. Automatic conversion to markdown code block by default is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default.

Depending on the number of actions, the device specs and the parameters, it will take a few seconds to a minute to format the description. Run using a launcher desktop shortcut instead of with the play button in tasker UI for faster execution.

Check [Format_Task_Description_For_Markdown Task Info](Format_Task_Description_For_Markdown.tsk.md) file for more info on the task.
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

Latest version is `v0.3.0`.

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
- [TaskerNet](https://taskernet.com/shares/?user=AS35m8mXdvaT1Vj8TwkSaCaoMUv220IIGtHe3pG4MymrCUhpgzrat6njEOnDVVulhAIHLi6BPUt1&id=Task%3AFormat+Task+Description+For+Markdown).

##


### Install Instructions For Tasker In Android

1. Import `format_task_description_for_markdown/Format_Task_Description_For_Markdown.tsk.xml` Task file into Tasker.
##

### Usage

For basic usage, just run the task provided after running `Export` -> `Description To Clipboard` on a task and it will read the description from the `%CLIP` variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents.

Check [Format_Task_Description_For_Markdown Task Info](Format_Task_Description_For_Markdown.tsk.md) file for more info on how to use the task.
##


### Example Output Of Formatted Description

For examples of the formatted task description, check:

- [`split_action_parameters_on_multiple_lines` Disabled](Example_Output_Of_Formatted_Task_Description_1.md)
- [`split_action_parameters_on_multiple_lines` Enabled](Example_Output_Of_Formatted_Task_Description_2.md)
##


### Current Features

- Replaces all pre-existing indents with spaces by default.
- Automatically increases indents for `If` and `For` related actions with support for capping indents at a max indent character count.
- Supports splitting action parameters of most action descriptions on multiple lines to increase readability. **[Experimental]**
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

Check [CHANGELOG.md](CHANGELOG.md) file for the **Changelog**.
##


### Contributions

- [u/Ratchet_Guy](https://www.reddit.com/user/Ratchet_Guy/) for his [Process REDDIT Code](https://www.reddit.com/r/tasker/comments/34dapt/best_way_to_format_task_descriptions_for_reddits/) task on which this was based on.
##


[Tasker App]: https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm
