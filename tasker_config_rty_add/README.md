# Tasker Config rty Add

A helper script to fix tasker configs of people who updated from Tasker v5.8.5 to v5.9.beta.3 and had their collision handling messed up because the update removed all `<rty>2</rty>` tags.

The tasker config stores the collision handling option of each task in the `<rty>` tags of the task.

```
<rty>0</rty> or "no tags" == Abort New Task

<rty>1</rty> == Abort Existing Task

<rty>2</rty> == Run Both Together
```

The script finds all tasks with `Run Both Together <rty>2</rty>` tags in an old config file and then adds the same tag to all tasks in the current config file overriding any existing `<rty>` tags of the tasks found. (The previous duplication issue has been fixed)

Note that the `<rty>` tags are added before the `<pri>` tags but you can export another backup from tasker to fix the order, it shouldn't matter during importing the new config to tasker.

The script can also work to add `<rty>1</rty>` instead by changing the `rty_number` variable to `1` in the script. 

You should have GNU sed installed in your system.
- Termux (non-root shell): `apt install sed`
- Linux distros: `sudo apt install sed`
- Windows: You can use cygwin installer.

## Usage:

Set `old_config`, `current_config` and `new_config` variables in the script to the names or paths of the configs.

```
#run script in your android device or linux distro or cygwin in windows
bash tasker_config_rty_add
```
