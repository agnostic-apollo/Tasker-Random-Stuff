# Format Task Description For Markdown On Clipboard Copy

&nbsp;
## Export Info:
**Tasker Version:** `5.12.3-beta`  
**Timestamp:** `2021-03-03 18.55.21`  
&nbsp;



&nbsp;
## Profile Names:
**Count:** `1`

- `Format Task Description For Markdown On Clipboard Copy`



## Scene Names:
**Count:** `0`




## Task Names:
**Count:** `1`

- `Anonymous (982)`
##
&nbsp;



&nbsp;
## Profiles Info:
&nbsp;

### Profile 1
**Name:** `Format Task Description For Markdown On Clipboard Copy`  
**ID:** `981`  
**Entry Task:** `Anonymous (982)`  

#### Comment:

A profile that detects if a tasker task or profile description is copied to clipboard and then calls the `Format Task Description For Markdown` task with the clipboard text as `%par2`.

It detects this by checking if the clipboard text contains an indented "A1" action line and if it starts with a task or profile name and code line.
##
&nbsp;




&nbsp;
## Tasks Info:
&nbsp;

### Task 1
**Name:** `Anonymous (982)`  
**ID:** `982`  
**Collision Handling:** `Abort New Task`  
**Keep Device Awake:** `false`  
**Help:** `-`
##
&nbsp;



&nbsp;
## Code Description:
&nbsp;

```
Profile Name: Format Task Description For Markdown On Clipboard Copy
    	Restore: no
    	Variables: [  ]
    	Event: Variable Set [ Variable:%CLIP Value:* User Variables Only:Off ]



Entry Task Name: Anon

Actions:
    A1: If [ %evtprm(1) eq \%CLIP ]

        A2: Variable Set [ 
            Name:%code 
            To:%evtprm(2) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <If code contains an indented "A1" action line and starts with a task or profile name and code line>
        A3: Perform Task [ 
            Name:Format Task Description For Markdown 
            Priority:%priority 
            Parameter 1 (%par1): 
            Parameter 2 (%par2):%code 
            Return Value Variable: 
            Stop:Off 
            Local Variable Passthrough:Off 
            Limit Passthrough To: 
            Reset Return Variable:Off 
            Allow Overwrite Variables:Off 
            Structure Output:Off ] If [ %code ~R (?m)^\s{4}\tA1: . & %code ~R ^[\s]*(.+) \([0-9]+\)\n ]

    A4: End If 
```

##
&nbsp;


*This file was automatically generated using [tasker_config_utils v0.5.0](https://github.com/Taskomater/tasker_config_utils).*
