# Extract Task Caller Array Values

## Export Info:
**Tasker Version:** `5.9.3.beta`  
**Timestamp:** `2020-02-22 22.46.08`  



## Profile Names:
**Count:** `0`




## Scene Names:
**Count:** `0`




## Task Names:
**Count:** `1`

- *`Extract Task Caller Array Values`*



## Profiles Info:



## Tasks Info:

**#:** `1`  
**Name:** `Extract Task Caller Array Values`  
**ID:** `814`  
**Collision Handling:** `Run Both Together`  
**Keep Device Awake:** `false`  
**Help:**
```
A helper task to extract values from the "%caller" array passed to every task that contains the information of the caller in the format "callertype(=callername(:subcallername)".

For more info on what the "%caller" array contains check the "Task Caller %caller" section of Tasker Variables guide.

"https://tasker.joaoapps.com/userguide/en/variables.html"

index must be a valid number that should refer to the item number of the "%caller" array from which extraction should be done. The caller array does not contain the information of the current task but when the current task calls the "Extract Task Caller Array Values" task, the caller(1) refers to the information of the current task. caller(2) refers to the information that called the current task and so on... However, the index should be passed in reference to the task calling the "Extract Task Caller Array Values" task. If you want information of the current task, then set it to "0". If you want information of the task that called the current task, then set to "1". The index is automatically incremented by 1 by the "Extract Task Caller Array Values" task while processing. If %par1 is not passed, index defaults to "0".

extraction_mode must be value that should be extracted. The valid values are any value from "callertype,callername,subcallername,callername_and_subcallername,callertype_callername_and_subcallername". If %par2 is not passed, extraction_mode defaults to "callername_and_subcallername".

Examples:

Get name of current task:
index="0"
extraction_mode="callername_and_subcallername"

Get callername:subcallername of caller that called current task:
index="1"
extraction_mode="callername_and_subcallername"

Get callertype of caller that called current task:
index="1"
extraction_mode="callertype"

Get callername of task that called current task:
index="1"
extraction_mode="callername"

Get subcallername of task that called current task:
index="1"
extraction_mode="subcallername"

Get callername:subcallername of caller of caller that called current task:
index="2"
extraction_mode="callername_and_subcallername"


Input %par1:
"
index
"

Input %par2:
"
extraction_mode
"

Returns:
"
result_string
"

If result_string exists and is not empty, it is returned, otherwise return value is not set. Return value will also not be set if invalid parameters are received or there are exceptions while running the task.
```
##

