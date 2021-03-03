# Format Task Description For Markdown

The `Format Task Description For Markdown` task formats an exported tasker task or profile description/code into a more readable and markdown compatible format for websites like reddit and github.

It is also automatically called by the `Format Task Description For Markdown On Clipboard Copy` profile if the primary clipboard is set to a task or profile description, like when the user exports a task or profile description to clipboard from the tasker UI.

Automatic conversion to markdown code block by default is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default.

The task is currently tested and working for the currently latest tasker version `v.5.12.3-beta`. If it breaks for newer versions or in case of bugs, please report to the author of the task.
##



### Contents
- [Compatibility](#Compatibility)
- [Downloads](#Downloads)
- [Install Instructions For Tasker In Android](#Install-Instructions-For-Tasker-In-Android)
- [Usage](#Usage)
- [Example Output Of Formatted Task Description](#Example-Output-Of-Formatted-Description)
- [Current Features](#Current-Features)
- [Planned Features](#Planned-Features)
- [Issues](#Issues)
- [Changelog](#Changelog)
- [Contributions](#Contributions)
##



### Compatibility

- Android using [Tasker App].
##



### Downloads

Latest version is `v0.4.0`.

- [GitHub releases](https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases).
##



### Install Instructions For Tasker In Android

- `Taskernet`  
    Import `Format Task Description For Markdown Task` from `Taskernet` from [here](https://taskernet.com/shares/?user=AS35m8mXdvaT1Vj8TwkSaCaoMUv220IIGtHe3pG4MymrCUhpgzrat6njEOnDVVulhAIHLi6BPUt1&id=Task%3AFormat+Task+Description+For+Markdown).  
    Import `Format Task Description For Markdown On Clipboard Copy Profile` from `Taskernet` from [here](https://taskernet.com/shares/?user=AS35m8mXdvaT1Vj8TwkSaCaoMUv220IIGtHe3pG4MymrCUhpgzrat6njEOnDVVulhAIHLi6BPUt1&id=Profile%3AFormat+Task+Description+For+Markdown+On+Clipboard+Copy).  

- `XML`  
    Download the [Format Task Description For Markdown Task XML](Format_Task_Description_For_Markdown.tsk.xml) and [Format Task Description For Markdown On Clipboard Copy Profile XML](Format_Task_Description_For_Markdown_On_Clipboard_Copy.prf.xml) files to the android download directory. To download, right-click or hold the `Raw` button at the top after opening a file link and select `Download/Save link` or use `curl` from a termux shell. Then import the downloaded task file into Tasker by long pressing the `Task` tab button in Tasker home and selecting `Import Task`.  

    `curl -L 'https://github.com/agnostic-apollo/Tasker-Random-Stuff/raw/master/format_task_description_for_markdown/Format_Task_Description_For_Markdown.tsk.xml' -o "/storage/emulated/0/Download/Format_Task_Description_For_Markdown.tsk.xml"`  

    `curl -L 'https://github.com/agnostic-apollo/Tasker-Random-Stuff/raw/master/format_task_description_for_markdown/Format_Task_Description_For_Markdown_On_Clipboard_Copy.prf.xml' -o "/storage/emulated/0/Download/Format_Task_Description_For_Markdown_On_Clipboard_Copy.prf.xml"`  


Check [Format Task Description For Markdown Task Info](Format_Task_Description_For_Markdown.tsk.md) file for more info on the task.
Check [Format Task Description For Markdown On Clipboard Copy Profile Info](Format_Task_Description_For_Markdown_On_Clipboard_Copy.prf.md) file for more info on the profile.
##



### Usage

For basic usage, just run this task after running `Export` -> `Description To Clipboard` on a task and it will read the description from the `%CLIP` variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents. However, if you have enabled the `Format Task Description For Markdown On Clipboard Copy` profile, you don't need to call this task manually, it will automatically be called when you export.

Depending on the number of actions, the device specs and the parameters, it will take a few seconds to a minute to format the description. Run using a launcher desktop shortcut instead of with the play button in tasker UI for faster execution.
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



### Changelog

Check [CHANGELOG.md](CHANGELOG.md) file for the **Changelog**.
##



### Contributions

- [u/Ratchet_Guy](https://www.reddit.com/user/Ratchet_Guy/) for his [Process REDDIT Code](https://www.reddit.com/r/tasker/comments/34dapt/best_way_to_format_task_descriptions_for_reddits/) task on which this was based on.
##



[Tasker App]: https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm
