# Grab Timed And Filtered Logcat

## Export Info:
**Tasker Version:** `5.9.3`  
**Timestamp:** `2020-09-15 10.22.15`  
**sha256sum:** `be9f0785f23a4ad7d00ace47ffaea9028e058970ec08de55e72d81d61b0eb797`  



## Profile Names:
**Count:** `0`




## Scene Names:
**Count:** `0`




## Task Names:
**Count:** `1`

- *`Grab Timed And Filtered Logcat`*



## Profiles Info:



## Tasks Info:

**#:** `1`  
**Name:** `Grab Timed And Filtered Logcat`  
**ID:** `865`  
**Collision Handling:** `Abort New Task`  
**Keep Device Awake:** `false`  
**Control:**
```

version_number: 0.3.0
```
**Help:**
```
A tasks that allows user to capture logcats starting from current time for the next x amount of seconds. It also allows capturing logcat entries of specific tags and application of regex to filter specific entries.

Reading logcat requires root or ADB access or "android.permission.READ_LOGS" permission to be granted to tasker.
Reading dmesg or last_kmesg requires root or ADB access.

The Tasker "Located Entry" Profile capturing mechanism sometimes doesn't allow the user to see the exact flow of logcat entries in a user friendly way specially if a lot of entries are captured. Moreover, sometimes the user doesn't know what filters to apply without seeing all the logcat entries first.

It can also help in capturing logcat dumps for other devs for debugging purposes.

The "Set User Modifiable Variables*" section defines a few variables to alter the behaviour of the task.

The logcat_tag_filter variable defines the parameters passed to the logcat command to filter specific tags. Check the "Filtering log output" section of logcat user guide at "https://developer.android.com/studio/command-line/logcat" for more info.

The logcat_filter_regex is a java regex that can be used to filter logcat entries using the Tasker "Variable Search Replace" action. By default it uses the regex OR "|" operator to only keep entries matching the strings defined in the regex.

The timeout_seconds are the seconds for which to capture the logcat output after starting this task. It must a valid integer and must be less than 1000.

The unfiltered_logcat_file defines the path to the file to which to output the logcat command output before the logcat_filter_regex is applied. It must be an absolute path and must be under "/storage/emulated/0". The default is "/storage/emulated/0/unfiltered_logcat.txt".

The filtered_logcat_file defines the path to the file to which to output the logcat command output after the logcat_filter_regex is applied. It must be an absolute path and must be under "/storage/emulated/0". The default is "/storage/emulated/0/filtered_logcat.txt".

There are 4 possible logcat filtering behaviours of this task which can be modified by enabling or disabling the logcat_tag_filter and logcat_filter_regex "Variable Set" actions.

If both are enabled, then the logcat_tag_filter will be passed to the logcat command and the logcat_filter_regex will also be applied. Both the unfiltered_logcat_file and filtered_logcat_file files will be created.

If only logcat_tag_filter is enabled, then the logcat_tag_filter will be passed to the logcat command. Only the unfiltered_logcat_file file will be created.

If only logcat_filter_regex is enabled, then the logcat_tag_filter will not be passed to the logcat command and only the logcat_filter_regex will applied to the logcat output. Both the unfiltered_logcat_file and filtered_logcat_file files will be created.

If both are disabled, then the logcat_tag_filter will not be passed to the logcat command and the logcat_filter_regex will also not be applied. Only the unfiltered_logcat_file file will be created.

To use the task, make a desktop shortcut if required or use the Tasker task play button to run the task, then do things for which you want to capture logcat entries for. Do not do extra things. Moreover, you might need to wait a couple of seconds for things to be added to logcat so finish doing what you want to capture entries for a few seconds before the timeout expires and then wait for it to expire.

If the logcat command fails with a non-zero exit code but you still see the logcat output flashed, then this may be because the timeout command killed the logcat command and its exiting with a non-zero exit to show that. Just add the exit code you received to the logcat_success_exit_codes variable at the start of the task, which stores a comma separated list of exit code integers that will be considered as success instead of failures. Normally, 0 is the only exit code that is considered a success. Currently, only exit codes 0, 124, 142 and 257 are considered as success but additional ones may need to be added for some devices.


Control:
"
version_number: 0.3.0
"

This task does not take any parameters or return anything.
```
##

