# Save logcat dmesg last kmesg

## Export Info:
**Tasker Version:** `5.9.3`  
**Timestamp:** `2020-09-12 13.42.16`  
**sha256sum:** `98aec1408d58608817234b62dc0eed1cf2702ad70af83932784b450375e6ba40`  



## Profile Names:
**Count:** `0`




## Scene Names:
**Count:** `0`




## Task Names:
**Count:** `1`

- *`Save logcat;dmesg;last_kmesg`*



## Profiles Info:



## Tasks Info:

**#:** `1`  
**Name:** `Save logcat;dmesg;last_kmesg`  
**ID:** `990`  
**Collision Handling:** `Abort New Task`  
**Keep Device Awake:** `false`  
**Control:**
```

version_number: 0.1.0
```
**Help:**
```
A helper task to save logcat, dmesg and last_kmesg/console-ramoops to the android storage.

Reading logcat requires root or ADB access or "android.permission.READ_LOGS" permission to be granted to tasker.
Reading dmesg or last_kmesg requires root or ADB access.

"logcat" is the log of android OS system and app messages. It can be used to debug errors like why an app crashed or to monitor what in going on underneath in the android OS. Android OS has a lot of components that output a lot of information to the logcat about their state. Installed apps may optionally also output information to the logcat. The tasker "Logcat Event" profile may be used to run specific actions when a certain entry is outputted to the logcat. By default, when this task runs the logcat command, the output of every component of only the last few minutes of the logcat is saved to the file. You may set additional options in the logcat_command_options variable to pass them to the logcat command to get specific logcat entries. If you want to record logcat entries of a specific event, then run this task as soon as the desired event finishes. For more information on logcat, check https://developer.android.com/studio/command-line/logcat.

"dmesg" is the log of the android kernel, i.e linux kernel. It contains information outputted by the kernel components like device drivers or selinux. This normally isn't needed by android app devs or users, other than if root actions are being run. By default, when this task runs the dmesg command, the output of every component of only the last few minutes of the dmesg is saved to the file. You may set additional options in the dmesg_command_options variable to pass them to the dmesg command to get specific dmesg entries. For more information on dmesg, check https://man7.org/linux/man-pages/man1/dmesg.1.html

The "/proc/last_kmsg" or the "/sys/fs/pstore/console-ramoops" file in android>=6 stores the last few android kernel messages just before an android phone crashes or has a kernel panic. The file can be read on the next boot up to debug why the phone crashed earlier. This file will not exist on a boot up if the phone didn't have a crash on the last boot and was normally rebooted or booted up. For more information on last_kmesg, check https://android.googlesource.com/kernel/common/+/android-3.18/Documentation/ramoops.txt

The "Set User Modifiable Variables*" section defines a few variables to alter the behaviour of the task.

The logcat_file defines the path to the file to which to save the logcat. It must be an absolute path and must be under "/storage/emulated/0". The default is "/storage/emulated/0/logcat.txt".

The dmesg_file defines the path to the file to which to save the dmesg. It must be an absolute path and must be under "/storage/emulated/0". The default is "/storage/emulated/0/dmesg.txt".

The last_kmesg_file defines the path to the file to which to save the last_kmesg. It must be an absolute path and must be under "/storage/emulated/0". The default is "/storage/emulated/0/last_kmesg.txt".


Control:
"
version_number: 0.1.0
"

This task does not take any parameters or return anything.
```
##

