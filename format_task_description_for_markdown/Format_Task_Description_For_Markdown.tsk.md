# Format Task Description For Markdown

&nbsp;
## Export Info:
**Tasker Version:** `5.12.3-beta`  
**Timestamp:** `2021-03-03 18.59.21`  
&nbsp;



&nbsp;
## Profile Names:
**Count:** `0`




## Scene Names:
**Count:** `0`




## Task Names:
**Count:** `1`

- `Format Task Description For Markdown`
##
&nbsp;



&nbsp;
## Profiles Info:
&nbsp;



&nbsp;
## Tasks Info:
&nbsp;

### Task 1
**Name:** `Format Task Description For Markdown`  
**ID:** `1024`  
**Collision Handling:** `Abort New Task`  
**Keep Device Awake:** `false`  

#### Help:

The `Format Task Description For Markdown` task formats an exported tasker task or profile description/code into a more readable and markdown compatible format for websites like reddit and github.

It is also automatically called by the `Format Task Description For Markdown On Clipboard Copy` profile if the clipboard is set to task or profile description, like when the user exports a task or profile description to clipboard from the tasker UI.

For basic usage, just run this task after running `Export` -> `Description To Clipboard` on a task and it will read the description from the `%CLIP` variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents. However, if you enabled the `Format Task Description For Markdown On Clipboard Copy` profile, you don't need to call this task manually, it will automatically be called when you export.


If %par1 is not passed, then default values are automatically used.

If it is passed then it's parameters must be set to the following:

indent_character_type is the type of character that should be used for indents. Valid values are `space` and `tab`. Default value is `space`.

min_indent_character_count is the minimum indent that should be present for actions and comments. It must be a valid integer. Default value is `4`.

max_indent_character_count is the maximum indent that should be present for actions and comments depending `If` and `For` related actions. It must be a valid integer and is only considered if cap_indents_at_max_indent_character_count is set to `1` and it must not be less than min_indent_character_count. Default value is `12`.

single_indent_character_count is a number of characters of indent_character_type that must be considered as one indent. It can be same as min_indent_character_count. It must be a valid integer and must not be greater than min_indent_character_count. Default value is `4`.

split_action_parameters_on_multiple_lines is a toggle that decides if parameters of actions in description are split over multiple lines or not. If this is enabled, then each parameter will be on a different line making it easier to read. It should work for most actions but will not work for actions whose action name is modified depending on its configuration other than the `Else` action whose name is modified to `Else If` if there is a condition added to it. It will also not for actions whose parameter names are repeated in the description in any way. This uses EXPERIMENTAL CODE including tasker internal java functions which may stop working after an update to tasker, in that case, wait for the author of this task to release an update to make it compatible with the latest tasker version. Use at your own risk. Disable it if it is not working properly or you are receiving exceptions. Enabling this will also slow down the task even more than normal because of all the extra processing. It must be set to `0` or `1`. Default value is `1`.

cap_indents_at_max_indent_character_count is a toggle that decides if there should be limit on max indents based on max_indent_character_count. This is helpful if too many nested conditions exist in the task increasing the indents to a point that it makes it harder to read without using horizontal scrolling. It must be set to `0` or `1`. Default value is `0`.

convert_code_to_markdown_code_block is a toggle that decides whether the formatted code should automatically be converted to markdown code block by prefixing and suffixing the code with a minimum of 3 backticks. This is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default. Moreover, the task automatically checks if the code itself contains any backticks and then uses (max numbers of consecutive backticks found + 3) backticks for prefixing and suffixing so that any backticks in the code can be escaped and the entire code is enclosed in the code block. It must be set to `0` or `1`. Default value is `1`.

set_clipboard_to_formatted_code is a toggle that decides if the formatted code is put back in the clipboard using the `Set Clipboard` action at the end. It must be set to `0` or `1`. Default value is `1`.


If %par2 is not passed, then data from the clipboard using the tasker variable `%CLIP` is used as the code.

If %par2 is passed, then it is used as the code.

The first line of the task description must be in the format `task_name (task_code)` or `Profile: profile_name (profile_code)`. It can optionally be prefixed with whitespace characters.

Depending on the number of actions, the device specs and the parameters, it will take a few seconds to a minute to format the description. Run using a launcher desktop shortcut instead of with the play button in tasker UI for faster execution.

This task is currently tested and working for the currently latest tasker version `v.5.12.3-beta`. If it breaks for newer versions or in case of bugs, please report to the author of this task.
##


**Parameter `%par1`:** (optional)
```
indent_character_type
min_indent_character_count
max_indent_character_count
single_indent_character_count
cap_indents_at_max_indent_character_count
split_action_parameters_on_multiple_lines
convert_code_to_markdown_code_block
set_clipboard_to_formatted_code
```


**Parameter `%par2`:** (optional)
```
code
```


**Returns:**

```
formatted_code
```

If task is successful, then formatted_code will contain the formatted code description.
Otherwise it will not be set.


**Control:**

```
author: agnostic-apollo (agnosticapollo@gmail.com)
version_name: 0.4.0
```
##
&nbsp;



&nbsp;
## Code Description:
&nbsp;

``````
Task Name: Format Task Description For Markdown

Actions:
    <The `Format Task Description For Markdown` task formats an exported tasker task or profile description/code into a more readable and markdown compatible format for websites like reddit and github.
    
    It is also automatically called by the `Format Task Description For Markdown On Clipboard Copy` profile if the clipboard is set to task or profile description, like when the user exports a task or profile description to clipboard from the tasker UI.
    
    For basic usage, just run this task after running `Export` -> `Description To Clipboard` on a task and it will read the description from the `%CLIP` variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents. However, if you enabled the `Format Task Description For Markdown On Clipboard Copy` profile, you don't need to call this task manually, it will automatically be called when you export.
    
    
    If %par1 is not passed, then default values are automatically used.
    
    If it is passed then it's parameters must be set to the following:
    
    indent_character_type is the type of character that should be used for indents. Valid values are `space` and `tab`. Default value is `space`.
    
    min_indent_character_count is the minimum indent that should be present for actions and comments. It must be a valid integer. Default value is `4`.
    
    max_indent_character_count is the maximum indent that should be present for actions and comments depending `If` and `For` related actions. It must be a valid integer and is only considered if cap_indents_at_max_indent_character_count is set to `1` and it must not be less than min_indent_character_count. Default value is `12`.
    
    single_indent_character_count is a number of characters of indent_character_type that must be considered as one indent. It can be same as min_indent_character_count. It must be a valid integer and must not be greater than min_indent_character_count. Default value is `4`.
    
    split_action_parameters_on_multiple_lines is a toggle that decides if parameters of actions in description are split over multiple lines or not. If this is enabled, then each parameter will be on a different line making it easier to read. It should work for most actions but will not work for actions whose action name is modified depending on its configuration other than the `Else` action whose name is modified to `Else If` if there is a condition added to it. It will also not for actions whose parameter names are repeated in the description in any way. This uses EXPERIMENTAL CODE including tasker internal java functions which may stop working after an update to tasker, in that case, wait for the author of this task to release an update to make it compatible with the latest tasker version. Use at your own risk. Disable it if it is not working properly or you are receiving exceptions. Enabling this will also slow down the task even more than normal because of all the extra processing. It must be set to `0` or `1`. Default value is `1`.
    
    cap_indents_at_max_indent_character_count is a toggle that decides if there should be limit on max indents based on max_indent_character_count. This is helpful if too many nested conditions exist in the task increasing the indents to a point that it makes it harder to read without using horizontal scrolling. It must be set to `0` or `1`. Default value is `0`.
    
    convert_code_to_markdown_code_block is a toggle that decides whether the formatted code should automatically be converted to markdown code block by prefixing and suffixing the code with a minimum of 3 backticks. This is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default. Moreover, the task automatically checks if the code itself contains any backticks and then uses (max numbers of consecutive backticks found + 3) backticks for prefixing and suffixing so that any backticks in the code can be escaped and the entire code is enclosed in the code block. It must be set to `0` or `1`. Default value is `1`.
    
    set_clipboard_to_formatted_code is a toggle that decides if the formatted code is put back in the clipboard using the `Set Clipboard` action at the end. It must be set to `0` or `1`. Default value is `1`.
    
    
    If %par2 is not passed, then data from the clipboard using the tasker variable `%CLIP` is used as the code.
    
    If %par2 is passed, then it is used as the code.
    
    The first line of the task description must be in the format `task_name (task_code)` or `Profile: profile_name (profile_code)`. It can optionally be prefixed with whitespace characters.
    
    Depending on the number of actions, the device specs and the parameters, it will take a few seconds to a minute to format the description. Run using a launcher desktop shortcut instead of with the play button in tasker UI for faster execution.
    
    This task is currently tested and working for the currently latest tasker version `v.5.12.3-beta`. If it breaks for newer versions or in case of bugs, please report to the author of this task.
    ##
    
    
    **Parameter `%par1`:** (optional)
    ```
    indent_character_type
    min_indent_character_count
    max_indent_character_count
    single_indent_character_count
    cap_indents_at_max_indent_character_count
    split_action_parameters_on_multiple_lines
    convert_code_to_markdown_code_block
    set_clipboard_to_formatted_code
    ```
    
    
    **Parameter `%par2`:** (optional)
    ```
    code
    ```
    
    
    **Returns:**
    
    ```
    formatted_code
    ```
    
    If task is successful, then formatted_code will contain the formatted code description.
    Otherwise it will not be set.
    
    
    **Control:**
    
    ```
    author: agnostic-apollo (agnosticapollo@gmail.com)
    version_name: 0.4.0
    ```>
    A1: Anchor 

    A2: Variable Set [ 
        Name:%task_name 
        To:Format Task Description For Markdown 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Enable this action if you want to flash log messages while running this task>
    A3: [X] Variable Set [ 
        Name:%enable_flash_actions 
        To:1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Set action codes whose action parameters should be force split even if duplicates found
    Default:
    664
    Java Function>
    A4: Variable Set [ 
        Name:%force_split_action_parameters_on_multiple_lines_action_codes 
        To:664 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Set Newline Character>
    A5: Variable Set [ 
        Name:%newline 
        To:
     
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Parse And Validate Parameters>
    A6: Anchor 

    A7: [X] Variable Set [ 
        Name:%par1 
        To:space
    4
    12
    4
    0
    1
    1
    1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <If %par1 Not Received>
    A8: If [ %par1 eq \%par1 ]

        <Set User Modifiable Variables Start>
        A9: Anchor 

        <Set indent_character_type
        Default: "space">
        A10: Variable Set [ 
            Name:%indent_character_type 
            To:space 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set min_indent_character_count
        Default: "4">
        A11: Variable Set [ 
            Name:%min_indent_character_count 
            To:4 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set max_indent_character_count
        Default: "12">
        A12: Variable Set [ 
            Name:%max_indent_character_count 
            To:12 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set single_indent_character_count
        Default: "4">
        A13: Variable Set [ 
            Name:%single_indent_character_count 
            To:4 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set cap_indents_at_max_indent_character_count
        Default: "0">
        A14: Variable Set [ 
            Name:%cap_indents_at_max_indent_character_count 
            To:0 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set split_action_parameters_on_multiple_lines
        Default: "1">
        A15: Variable Set [ 
            Name:%split_action_parameters_on_multiple_lines 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set convert_code_to_markdown_code_block
        Default: "1">
        A16: Variable Set [ 
            Name:%convert_code_to_markdown_code_block 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set set_clipboard_to_formatted_code
        Default: "1">
        A17: Variable Set [ 
            Name:%set_clipboard_to_formatted_code 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set User Modifiable Variables End>
        A18: Anchor 

    A19: Else 

        A20: Variable Set [ 
            Name:%format_task_description_for_markdown_parameter_1 
            To:%par1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A21: Variable Split [ 
            Name:%format_task_description_for_markdown_parameter_1 
            Splitter:%newline 
            Delete Base:Off ] 

        <Set indent_character_type>
        A22: Variable Set [ 
            Name:%indent_character_type 
            To:%format_task_description_for_markdown_parameter_1(1) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set min_indent_character_count>
        A23: Variable Set [ 
            Name:%min_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(2) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set max_indent_character_count>
        A24: Variable Set [ 
            Name:%max_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(3) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set single_indent_character_count>
        A25: Variable Set [ 
            Name:%single_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(4) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set cap_indents_at_max_indent_character_count>
        A26: Variable Set [ 
            Name:%cap_indents_at_max_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(5) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set split_action_parameters_on_multiple_lines>
        A27: Variable Set [ 
            Name:%split_action_parameters_on_multiple_lines 
            To:%format_task_description_for_markdown_parameter_1(6) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set convert_code_to_markdown_code_block>
        A28: Variable Set [ 
            Name:%convert_code_to_markdown_code_block 
            To:%format_task_description_for_markdown_parameter_1(7) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set set_clipboard_to_formatted_code>
        A29: Variable Set [ 
            Name:%set_clipboard_to_formatted_code 
            To:%format_task_description_for_markdown_parameter_1(8) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A30: End If 

    <If %par2 Not Received>
    A31: If [ %par2 eq \%par2 ]

        <Set Clipboard Text To code>
        A32: Variable Set [ 
            Name:%code 
            To:%CLIP 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A33: Else 

        <Set %par2 To code>
        A34: Variable Set [ 
            Name:%code 
            To:%par2 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A35: End If 

    <Set Tab Character>
    A36: Variable Set [ 
        Name:%tab 
        To:	 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Set Space Character>
    A37: Variable Set [ 
        Name:%space 
        To:  
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <If indent_character_type Is Set To "space">
    A38: If [ %indent_character_type eq space ]

        <Set "%space" to indent_character>
        A39: Variable Set [ 
            Name:%indent_character 
            To:%space 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    <If indent_character_type Is Set To "tab">
    A40: Else If [ %indent_character_type eq tab ]

        <Set "%tab" to indent_character>
        A41: Variable Set [ 
            Name:%indent_character 
            To:%tab 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A42: End If 

    <Set Default Indent Character Count>
    A43: Variable Set [ 
        Name:%indent_character_count 
        To:%min_indent_character_count 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A44: Variable Set [ 
        Name:%regex_single_indent_prefix 
        To:^[%indent_character]{%single_indent_character_count} 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A45: Variable Set [ 
        Name:%regex_set_max_indent 
        To:^[%indent_character]{%max_indent_character_count,} 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A46: Variable Set [ 
        Name:%regex_valid_number 
        To:^[0-9]+$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A47: Variable Set [ 
        Name:%regex_valid_bool_value 
        To:^[0-1]$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A48: Variable Set [ 
        Name:%regex_task_or_profile_name_and_code_line 
        To:^[\s]*(.+) \([0-9]+\)$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A49: Variable Set [ 
        Name:%regex_profile_name_and_code_line 
        To:^[\s]*Profile: (.+) \([0-9]+\)$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A50: Variable Set [ 
        Name:%regex_enter_task_name_and_code_line 
        To:^[\s]*Enter: (.+) \([0-9]+\)$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A51: Variable Set [ 
        Name:%regex_exit_task_name_and_code_line 
        To:^[\s]*Exit: (.+) \([0-9]+\)$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A52: Variable Set [ 
        Name:%regex_task_collision_handling_value_line 
        To:^[\s]+(Abort New Task)|(Abort Existing Task)|(Run Both Together)$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A53: Variable Set [ 
        Name:%regex_action_line_start 
        To:^[\s]+A[0-9]+: . 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A54: Variable Set [ 
        Name:%regex_action_line_end 
        To: \](%space)?$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A55: Variable Set [ 
        Name:%regex_action_line_with_parameters 
        To:^[\s]+A[0-9]+: (?:\[X\] )?([^\\\[]+) \[.* 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A56: Variable Set [ 
        Name:%regex_comment_line_start 
        To:^[\s]+\< 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A57: Variable Set [ 
        Name:%regex_comment_line_end 
        To:\>$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A58: Variable Set [ 
        Name:%regex_whitespace_only_line 
        To:^[\s]+$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A59: Variable Set [ 
        Name:%regex_valid_comma_separated_numbers_list 
        To:^[0-9]+(,[0-9]+)*$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A60: Variable Set [ 
        Name:%plugin_action_names_list_splitter 
        To:
    #
    #
    #
     
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A61: Java Function [ 
        Return:plugin_action_names_list_splitter 
        Class Or Object:String 
        Function:new
    {String} (String) 
        Param:%plugin_action_names_list_splitter 
        Param: 
        Param: 
        Param: 
        Param: 
        Param: 
        Param: ] 

    A62: Test Variable [ 
        Type:Length 
        Data:%indent_character 
        Store Result In:%indent_character_length 
        Continue Task After Error:On ] 

    A63: If [ %indent_character neq %space &+ %indent_character neq %tab | %indent_character_length neq 1 | %min_indent_character_count !~R %regex_valid_number | %cap_indents_at_max_indent_character_count !~R %regex_valid_bool_value | %cap_indents_at_max_indent_character_count eq 1 & %max_indent_character_count !~R %regex_valid_number |+ %max_indent_character_count < %min_indent_character_count | %single_indent_character_count !~R %regex_valid_number | %single_indent_character_count > %min_indent_character_count | %convert_code_to_markdown_code_block !~R %regex_valid_bool_value | %set_clipboard_to_formatted_code !~R %regex_valid_bool_value | %split_action_parameters_on_multiple_lines !~R %regex_valid_bool_value | %force_split_action_parameters_on_multiple_lines_action_codes !~R %regex_valid_comma_separated_numbers_list ]

        A64: Variable Set [ 
            Name:%error 
            To:Invalid Parameters To %task_name
        %task_name Failed
        
        indent_character_type = "%indent_character_type"
        
        min_indent_character_count = "%min_indent_character_count"
        
        max_indent_character_count = "%max_indent_character_count"
        
        single_indent_character_count = "%single_indent_character_count"
        
        cap_indents_at_max_indent_character_count = "%cap_indents_at_max_indent_character_count"
        
        split_action_parameters_on_multiple_lines = "%split_action_parameters_on_multiple_lines"
        
        convert_code_to_markdown_code_block = "%convert_code_to_markdown_code_block"
        
        set_clipboard_to_formatted_code = "%set_clipboard_to_formatted_code"
        
        force_split_action_parameters_on_multiple_lines_action_codes = "%force_split_action_parameters_on_multiple_lines_action_codes" 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A65: Flash [ 
            Text:%error 
            Long:On ] 

        A66: Set Clipboard [ 
            Text:%error 
            Add:Off ] 

        A67: Stop [ 
            With Error:Off 
            Task: ] 

    A68: End If 

    <Generate single_indent_string Based On Current single_indent_character_count>
    A69: For [ 
        Variable:%num 
        Items:1:%single_indent_character_count ] 

        A70: Variable Set [ 
            Name:%single_indent_string 
            To:%indent_character 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:On 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A71: End For 

    <If split_action_parameters_on_multiple_lines Equals "1">
    A72: If [ %split_action_parameters_on_multiple_lines eq 1 ]

        <Get Tasker Package Version Name>
        A73: Anchor 

        A74: Variable Set [ 
            Name:%field_name 
            To:versionName 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A75: Variable Set [ 
            Name:%package_name 
            To:net.dinglisch.android.taskerm 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A76: Java Function [ 
            Return:package_manager 
            Class Or Object:CONTEXT 
            Function:getPackageManager
        {PackageManager} () 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A77: Java Function [ 
            Return:package_info 
            Class Or Object:package_manager 
            Function:getPackageInfo
        {PackageInfo} (String, int) 
            Param:%package_name 
            Param:0 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A78: Java Function [ 
            Return:%tasker_package_version_name 
            Class Or Object:package_info.%field_name 
            Function:assign
        {Object} () 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A79: Variable Search Replace [ 
            Variable:%tasker_package_version_name 
            Search:\.(alpha|beta|rc) 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:-$1 ] 

        A80: [X] Flash [ 
            Text:%tasker_package_version_name 
            Long:Off ] 

        A81: Variable Set [ 
            Name:%compare_versions_js 
            To:/*
        title:        compare-versions
        description:  js script to compare semantic versions
        author:       omichelsen
        homepage:     https://github.com/omichelsen/compare-versions
        license:      MIT License
        version:      3.6.0
        */
        
        /* global define */
        (function (root, factory) {
          /* istanbul ignore next */
          if (typeof define === 'function' && define.amd) {
            define([], factory);
          } else if (typeof exports === 'object') {
            module.exports = factory();
          } else {
            root.compareVersions = factory();
          }
        }(this, function () {
        
          var semver = /^v?(?:\d+)(\.(?:[x*]|\d+)(\.(?:[x*]|\d+)(\.(?:[x*]|\d+))?(?:-[\da-z\-]+(?:\.[\da-z\-]+)*)?(?:\+[\da-z\-]+(?:\.[\da-z\-]+)*)?)?)?$/i;
        
          function indexOrEnd(str, q) {
            return str.indexOf(q) === -1 ? str.length : str.indexOf(q);
          }
        
          function split(v) {
            var c = v.replace(/^v/, '').replace(/\+.*$/, '');
            var patchIndex = indexOrEnd(c, '-');
            var arr = c.substring(0, patchIndex).split('.');
            arr.push(c.substring(patchIndex + 1));
            return arr;
          }
        
          function tryParse(v) {
            return isNaN(Number(v)) ? v : Number(v);
          }
        
          function validate(version) {
            if (typeof version !== 'string') {
              throw new TypeError('Invalid argument expected string');
            }
            if (!semver.test(version)) {
              throw new Error('Invalid argument not valid semver (\''+version+'\' received)');
            }
          }
        
          function compareVersions(v1, v2) {
            [v1, v2].forEach(validate);
        
            var s1 = split(v1);
            var s2 = split(v2);
        
            for (var i = 0; i < Math.max(s1.length - 1, s2.length - 1); i++) {
              var n1 = parseInt(s1[i] || 0, 10);
              var n2 = parseInt(s2[i] || 0, 10);
        
              if (n1 > n2) return 1;
              if (n2 > n1) return -1;
            }
        
            var sp1 = s1[s1.length - 1];
            var sp2 = s2[s2.length - 1];
        
            if (sp1 && sp2) {
              var p1 = sp1.split('.').map(tryParse);
              var p2 = sp2.split('.').map(tryParse);
        
              for (i = 0; i < Math.max(p1.length, p2.length); i++) {
                if (p1[i] === undefined || typeof p2[i] === 'string' && typeof p1[i] === 'number') return -1;
                if (p2[i] === undefined || typeof p1[i] === 'string' && typeof p2[i] === 'number') return 1;
        
                if (p1[i] > p2[i]) return 1;
                if (p2[i] > p1[i]) return -1;
              }
            } else if (sp1 || sp2) {
              return sp1 ? -1 : 1;
            }
        
            return 0;
          };
        
          var allowedOperators = [
            '>',
            '>=',
            '=',
            '<',
            '<='
          ];
        
          var operatorResMap = {
            '>': [1],
            '>=': [0, 1],
            '=': [0],
            '<=': [-1, 0],
            '<': [-1]
          };
        
          function validateOperator(op) {
            if (typeof op !== 'string') {
              throw new TypeError('Invalid operator type, expected string but got ' + typeof op);
            }
            if (allowedOperators.indexOf(op) === -1) {
              throw new TypeError('Invalid operator, expected one of ' + allowedOperators.join('|'));
            }
          }
        
          compareVersions.validate = function(version) {
            return typeof version === 'string' && semver.test(version);
          }
        
          compareVersions.compare = function (v1, v2, operator) {
            // Validate operator
            validateOperator(operator);
        
            // since result of compareVersions can only be -1 or 0 or 1
            // a simple map can be used to replace switch
            var res = compareVersions(v1, v2);
            return operatorResMap[operator].indexOf(res) > -1;
          }
        
          return compareVersions;
        }));
         
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Run format_task_description_for_markdown_set_java_class_and_method_variables_js>
        A82: Anchor 

        A83: Variable Clear [ 
            Name:%javascript_failed 
            Pattern Matching:Off 
            Local Variables Only:Off 
            Clear All Variables:Off ] 

        A84: JavaScriptlet [ 
            Code://Set Default Variables Start
        
        var JS_VERBOSE_LEVEL=1; //default to log level 1
        
        var JS_OUTPUT=""; //default to none
        var JS_ERRORS=""; //default to none
        
        var REGEX_VALID_NUMBER= new RegExp('^[0-9]+$');
        var REGEX_VALID_TASKER_VARIABLE_NAME= new RegExp('^[a-zA-Z0-9][a-zA-Z0-9_]{2,}$');
        var REGEX_STRING_ENDS_WITH_UNDERSCORE= new RegExp('_$');
        
        //Set Default Variables End
        
        function log(log_level, output) { if (typeof JS_VERBOSE_LEVEL === 'number' && JS_VERBOSE_LEVEL >= log_level && typeof JS_OUTPUT !== 'undefined') { JS_OUTPUT = JS_OUTPUT + output.toString() + "\n"; } }
        function log_error(errors) { if (typeof JS_ERRORS !== 'undefined') { JS_ERRORS = JS_ERRORS + errors.toString() + "\n"; } }
        function exit_js(exit_code) { setLocal("js_exit_code", exit_code.toString()); setLocal("js_output", JS_OUTPUT); setLocal("js_errors", JS_ERRORS); exit();}
        
        //Import compare-versions.js
        var compare_versions_js = compare_versions_js;
        eval(compare_versions_js);
        
        
        //Validate Tasker Package Version Code
        var tasker_package_version_name = tasker_package_version_name;
        if ( !window.compareVersions.validate(tasker_package_version_name) ) {
        log_error("Invalid tasker_package_version_name: '" + tasker_package_version_name + "'");
        exit_js(1);
        }
        
        
        //Define Tasker Config Utils Java Variables
        //"TCUJV" -> "Tasker Config Utils"
        //"_C_" -> "Class"
        //"_CE_" -> "Class Enum"
        //"_CM_" -> "Class Method"
        
        
        //Define Tasker Config Utils Java Class Variables
        log(1, "Defining TCUJV_C variables");
        
        
        //Set TaskerActionsList Class
        var TCUJV_C_TaskerActionsList = "net.dinglisch.android.taskerm.n";
        
        
        
        
        //Define Tasker Config Utils Java Method Variables
        log(1, "Defining TCUJV_CE and TCUJV_CM variables");
        
        
        //TaskerActionsList Class Methods
        
        var TCUJV_CM_TaskerActionsList_GetActionNamesList = "l";
        var TCUJV_CM_TaskerActionsList_GetActionCodeByName = "b";
        var TCUJV_CM_TaskerActionsList_GetArgNameAtIndexOfActionWithCode = "a";
        var TCUJV_CM_TaskerActionsList_GetArgsSizeOfActionWithCode = "n";
        
        
        
        //Convert all TCUJV variables to tasker local variables
        log(1, "Converting all TCUJV variables to tasker local variables");
        
        var tasker_config_utils_java_variables_to_set = [
        "TCUJV_C_TaskerActionsList",
        "TCUJV_CM_TaskerActionsList_GetActionNamesList", "TCUJV_CM_TaskerActionsList_GetActionCodeByName", "TCUJV_CM_TaskerActionsList_GetArgNameAtIndexOfActionWithCode", "TCUJV_CM_TaskerActionsList_GetArgsSizeOfActionWithCode"];
        
        //setLocal("tasker_config_utils_java_variables_to_set_string", tasker_config_utils_java_variables_to_set.toString());
        
        for(var i=0;i<tasker_config_utils_java_variables_to_set.length;i++) {
        
        var variable_name = tasker_config_utils_java_variables_to_set[i];
        var variable_value = window[tasker_config_utils_java_variables_to_set[i]];
        
        if ( typeof variable_name === 'undefined' ||
        		!variable_name ||
        			!REGEX_VALID_TASKER_VARIABLE_NAME.test(variable_name) ||
        				REGEX_STRING_ENDS_WITH_UNDERSCORE.test(variable_name)) {
        	log_error("Undefined, empty or invalid tasker variable_name in tasker_config_utils_java_variables_to_set: '" + variable_name + "'");
        	exit_js(1);
        }
        
        if ( typeof variable_value === 'undefined' ||
        		!variable_value ) {
        	log_error("Undefined or empty variable_value for variable_name in tasker_config_utils_java_variables_to_set: '" + variable_name + "'");
        	exit_js(1);
        }
        
        setLocal(variable_name.toLowerCase(), variable_value);
        
        }
        
        
        
        //Exit with success
        log(1, "Complete");
        exit_js(0); 
            Libraries: 
            Auto Exit:Off 
            Timeout (Seconds):50 
            Continue Task After Error:On ] 

        A85: Variable Set [ 
            Name:%javascript_failed 
            To:exit_code = "%err"
        
        errors = 
        "
        %errmsg
        "
        
        js_exit_code = "%js_exit_code"
        
        js_output =
        "
        %js_output
        "
        
        js_errors = 
        "
        %js_errors
        " 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] If [ %err Set | %errmsg Set | %js_exit_code neq 0 ]

        A86: If [ %javascript_failed Set ]

            A87: Flash [ 
                Text:format_task_description_for_markdown_set_java_class_and_method_variables_js Failed.
            
            %javascript_failed 
                Long:On ] 

            A88: Stop [ 
                With Error:Off 
                Task: ] 

        A89: Else 

            A90: [X] Flash [ 
                Text:format_task_description_for_markdown_set_java_class_and_method_variables_js Output:
            
            js_exit_code = "%js_exit_code"
            
            js_output =
            "
            %js_output
            "
            
            js_errors =
            "
            %js_errors
            " 
                Long:On ] 

        A91: End If 

        <Get All Non Plugin Action Names And Convert To Array Start>
        A92: Anchor 

        A93: Java Function [ 
            Return:resources 
            Class Or Object:CONTEXT 
            Function:getResources
        {Resources} () 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A94: Java Function [ 
            Return:action_names_list 
            Class Or Object:%tcujv_c_taskeractionslist 
            Function:%tcujv_cm_taskeractionslist_getactionnameslist
        {List} () 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A95: Java Function [ 
            Return: 
            Class Or Object:Objects 
            Function:requireNonNull
        {Object} (Object) 
            Param:action_names_list 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Continue Task After Error:On ] 

        <If exception not raised>
        A96: If [ %err eq \%err ]

            A97: Variable Set [ 
                Name:%is_action_names_list_null 
                To:false 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        <Else if exception raised>
        A98: Else 

            A99: Variable Set [ 
                Name:%is_action_names_list_null 
                To:true 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        A100: End If 

        A101: Java Function [ 
            Return:%action_names_list_size 
            Class Or Object:action_names_list 
            Function:size
        {int} () 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] If [ %is_action_names_list_null eq false ]

        A102: If [ %action_names_list_size eq 0 | %is_action_names_list_null eq true ]

            A103: Flash [ 
                Text:Error! Failed To Get List Of All Non Plugin Action Names In Tasker
            %task_name Failed 
                Long:On ] 

            A104: Stop [ 
                With Error:Off 
                Task: ] 

        A105: End If 

        A106: Java Function [ 
            Return:new_string_array 
            Class Or Object:String[] 
            Function:new
        {String[]} (int) 
            Param:%action_names_list_size 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A107: Java Function [ 
            Return:action_names_array 
            Class Or Object:action_names_list 
            Function:toArray
        {Object[]} (Object[]) 
            Param:new_string_array 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        <Join the java String[] action_names_array into tasker String variable %non_plugin_action_names_list with plugin_action_names_list_splitter as the splitter
        
        The null elements will be added as the literal "null" string but tasker does not have any actions with that name.>
        A108: Java Function [ 
            Return:%non_plugin_action_names_list 
            Class Or Object:TextUtils 
            Function:join
        {String} (CharSequence, Object[]) 
            Param:plugin_action_names_list_splitter 
            Param:action_names_array 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        <Split the String %non_plugin_action_names_list into a tasker array>
        A109: Variable Split [ 
            Name:%non_plugin_action_names_list 
            Splitter:%plugin_action_names_list_splitter 
            Delete Base:Off ] 

        <Get All Non Plugin Action Names And Convert To Array End>
        A110: Anchor 

        <Get All Plugin Action Names And Convert To Array Start>
        A111: Anchor 

        <Set "com.twofortyfouram.locale.intent.action.EDIT_SETTING" to plugin_action_edit_activity_intent_action>
        A112: Variable Set [ 
            Name:%plugin_action_edit_activity_intent_action 
            To:com.twofortyfouram.locale.intent.action.EDIT_SETTING 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A113: Java Function [ 
            Return:package_manager 
            Class Or Object:CONTEXT 
            Function:getPackageManager
        {PackageManager} () 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A114: Java Function [ 
            Return:plugin_action_edit_activity_intent 
            Class Or Object:Intent 
            Function:new
        {Intent} (String) 
            Param:%plugin_action_edit_activity_intent_action 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        <Get plugin_action_edit_activities_list by running queryIntentActivities() for the plugin_action_edit_activity_intent Intent>
        A115: Java Function [ 
            Return:plugin_action_edit_activities_list 
            Class Or Object:package_manager 
            Function:queryIntentActivities
        {List} (Intent, int) 
            Param:plugin_action_edit_activity_intent 
            Param:0 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] 

        A116: Java Function [ 
            Return: 
            Class Or Object:Objects 
            Function:requireNonNull
        {Object} (Object) 
            Param:plugin_action_edit_activities_list 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Continue Task After Error:On ] 

        <If exception not raised>
        A117: If [ %err eq \%err ]

            A118: Variable Set [ 
                Name:%is_plugin_action_edit_activities_list_null 
                To:false 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        <Else if exception raised>
        A119: Else 

            A120: Variable Set [ 
                Name:%is_plugin_action_edit_activities_list_null 
                To:true 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        A121: End If 

        A122: Java Function [ 
            Return:%plugin_action_edit_activities_list_size 
            Class Or Object:plugin_action_edit_activities_list 
            Function:size
        {int} () 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: ] If [ %is_plugin_action_edit_activities_list_null eq false ]

        A123: If [ %plugin_action_edit_activities_list_size eq 0 | %is_plugin_action_edit_activities_list_null eq true ]

            A124: [X] Flash [ 
                Text:No Plugin Action Activities Found 
                Long:Off ] 

            A125: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Get All Plugin Action Names And Convert To Array End ] 

        A126: End If 

        A127: Variable Set [ 
            Name:%plugin_action_edit_activities_list_size 
            To:%plugin_action_edit_activities_list_size - 1 
            Recurse Variables:Off 
            Do Maths:On 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <For Loop On All Activity ResolveInfo In plugin_action_edit_activities_list>
        A128: For [ 
            Variable:%num 
            Items:0:%plugin_action_edit_activities_list_size ] If [ %plugin_action_edit_activities_list_size > -1 ]

            A129: Java Function [ 
                Return:(ResolveInfo) plugin_action_edit_activity_resolve_info 
                Class Or Object:plugin_action_edit_activities_list 
                Function:get
            {Object} (int) 
                Param:%num 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: ] 

            <Get plugin_action_edit_activity_label_charsequence>
            A130: Java Function [ 
                Return:plugin_action_edit_activity_label_charsequence 
                Class Or Object:plugin_action_edit_activity_resolve_info 
                Function:loadLabel
            {CharSequence} (PackageManager) 
                Param:package_manager 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: ] 

            A131: Java Function [ 
                Return: 
                Class Or Object:Objects 
                Function:requireNonNull
            {Object} (Object) 
                Param:plugin_action_edit_activity_label_charsequence 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Continue Task After Error:On ] 

            <If plugin_action_edit_activity_label_charsequence is null>
            A132: Goto [ 
                Type:Top of Loop 
                Number:1 
                Label: ] If [ %err neq \%err ]

            <Get plugin_action_edit_activity_label_string>
            A133: Java Function [ 
                Return:plugin_action_edit_activity_label_string 
                Class Or Object:plugin_action_edit_activity_label_charsequence 
                Function:toString
            {String} () 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: ] 

            A134: Java Function [ 
                Return: 
                Class Or Object:Objects 
                Function:requireNonNull
            {Object} (Object) 
                Param:plugin_action_edit_activity_label_string 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Continue Task After Error:On ] 

            <If plugin_action_edit_activity_label_string is null>
            A135: Goto [ 
                Type:Top of Loop 
                Number:1 
                Label: ] If [ %err neq \%err ]

            <Get plugin_action_edit_activity_label_string_length>
            A136: Java Function [ 
                Return:%plugin_action_edit_activity_label_string_length 
                Class Or Object:plugin_action_edit_activity_label_string 
                Function:length
            {int} () 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: ] 

            <If plugin_action_edit_activity_label_string_length is 0>
            A137: Goto [ 
                Type:Top of Loop 
                Number:1 
                Label: ] If [ %plugin_action_edit_activity_label_string_length eq 0 ]

            A138: Java Function [ 
                Return:%plugin_action_edit_activity_label_string 
                Class Or Object:String 
                Function:new
            {String} (String) 
                Param:plugin_action_edit_activity_label_string 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: 
                Param: ] 

            A139: Variable Set [ 
                Name:%position 
                To:%plugin_action_names_list(#)+1 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <Push plugin_action_edit_activity_label_string into plugin_action_names_list tasker array>
            A140: Array Push [ 
                Variable Array:%plugin_action_names_list 
                Position:%position 
                Value:%plugin_action_edit_activity_label_string 
                Fill Spaces:Off ] 

        A141: End For 

        <Get All Plugin Action Names And Convert To Array End>
        A142: Anchor 

    A143: End If 

    <Split Code On Newline To Create Code Array>
    A144: Variable Split [ 
        Name:%code 
        Splitter:%newline 
        Delete Base:Off ] 

    A145: Variable Set [ 
        Name:%line_num 
        To:1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A146: Variable Set [ 
        Name:%current_line 
        To:%code(%line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A147: Variable Set [ 
        Name:%next_line_num 
        To:%line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A148: Variable Set [ 
        Name:%next_line 
        To:%code(%next_line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <If First Line Doesn't Contain Task Or Profile Name And Code>
    A149: If [ %current_line !~R %regex_task_or_profile_name_and_code_line ]

        A150: Flash [ 
            Text:Error! Task Or Profile Name And Code Not Found In Line %line_num Of Description Being Used
        %task_name Failed
        
        Line %line_num = "%current_line" 
            Long:On ] 

        A151: Stop [ 
            With Error:Off 
            Task: ] 

    A152: End If 

    A153: Variable Set [ 
        Name:%lines_count 
        To:%code(#) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Remove Last Line If Only Whitespaces>
    A154: Array Pop [ 
        Variable Array:%code 
        Position:%lines_count 
        To Var: ] If [ %code(%lines_count) ~R %regex_whitespace_only_line ]

    A155: Variable Set [ 
        Name:%lines_count 
        To:%code(#) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <If First Line Doesn't Contain Profile Name And Code Or If Second Line Equals A Collision Handling Value Or First Action Or Comment Start Line (Last 3 checks exist to prevent false negatives where task name starts with "Profile: ">
    A156: If [ %current_line !~R %regex_profile_name_and_code_line | %next_line ~R %regex_task_collision_handling_value_line | %next_line ~R ^[\s]+A1: . | %next_line ~R %regex_comment_line_start ]

        <Set "0" to is_profile_description>
        A157: Variable Set [ 
            Name:%is_profile_description 
            To:0 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Goto Process Task Description Start>
        A158: Goto [ 
            Type:Action Label 
            Number:1 
            Label:Process Task Description Start ] 

    A159: End If 

    <Process Profile Description Start>
    A160: Anchor 

    A161: Variable Set [ 
        Name:%description_name 
        To:%current_line 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Get Profile Description Name From First Line>
    A162: Variable Search Replace [ 
        Variable:%description_name 
        Search:%regex_profile_name_and_code_line 
        Ignore Case:Off 
        Multi-Line:Off 
        One Match Only:Off 
        Store Matches In Array: 
        Replace Matches:On 
        Replace With:$1 ] 

    <Set First Line To "Profile Name: %description_name">
    A163: Variable Set [ Name:%code(%line_num) To:Profile Name: %description_name Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 Structure Output:Off ] 

    A164: Flash [ 
        Text:Formatting "%description_name" Profile Description For Markdown 
        Long:Off ] If [ %par1 eq \%par1 ]

    <Set "1" to is_profile_description>
    A165: Variable Set [ 
        Name:%is_profile_description 
        To:1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Process Profile Code Loop Start>
    A166: Anchor 

    <Next Profile Line>
    A167: Anchor 

    A168: Variable Set [ 
        Name:%line_num 
        To:%line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A169: Variable Set [ 
        Name:%current_line 
        To:%code(%line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Goto Process Profile Code Loop Start If Next Line Does Not Match Entry Or Exit Task First Line>
    A170: Goto [ 
        Type:Action Label 
        Number:1 
        Label:Process Profile Code Loop Start ] If [ %line_num < %lines_count + 1 & %current_line !~R %regex_enter_task_name_and_code_line & %current_line !~R %regex_exit_task_name_and_code_line ]

    <Goto Process Task Code Loop End>
    A171: Goto [ 
        Type:Action Label 
        Number:1 
        Label:Process Task Code Loop End ] If [ %line_num > %lines_count ]

    <Process Profile Code Loop End>
    A172: Anchor 

    <Process Task Description Start>
    A173: Anchor 

    <Set Default Indent Character Count>
    A174: Variable Set [ 
        Name:%indent_character_count 
        To:%min_indent_character_count 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A175: Variable Set [ 
        Name:%current_line 
        To:%code(%line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A176: Variable Set [ 
        Name:%description_name 
        To:%current_line 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <If is_profile_description Equals "1">
    A177: If [ %is_profile_description eq 1 ]

        <If Current Line Starts An Entry Task But Not A Second Entry Task Of An Instant Profile>
        A178: If [ %current_line ~R %regex_enter_task_name_and_code_line & %is_entry_task_description neq 1 ]

            <Set First Line To "%newline%newline%newline">
            A179: Variable Set [ 
                Name:%code(%line_num) 
                To:%newline%newline%newline 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <Get Entry Task Description Name From First Line>
            A180: Variable Search Replace [ 
                Variable:%description_name 
                Search:%regex_enter_task_name_and_code_line 
                Ignore Case:Off 
                Multi-Line:Off 
                One Match Only:Off 
                Store Matches In Array: 
                Replace Matches:On 
                Replace With:$1 ] 

            <Append "Entry Task Name: %description_name" To First Line>
            A181: Variable Set [ Name:%code(%line_num) To:Entry Task Name: %description_name Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 Structure Output:Off ] 

            <Set "1" to is_entry_task_description>
            A182: Variable Set [ 
                Name:%is_entry_task_description 
                To:1 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        <If Current Line Starts An Exit Task Or A Second Entry Task Of An Instant Profile>
        A183: Else If [ %current_line ~R %regex_exit_task_name_and_code_line | %current_line ~R %regex_enter_task_name_and_code_line ]

            <Set First Line To "%newline" If is_entry_task_description Equals "1">
            A184: Variable Set [ 
                Name:%code(%line_num) 
                To:%newline 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] If [ %is_entry_task_description eq 1 ]

            <Set First Line To "%newline%newline%newline" If is_entry_task_description Does Not Equal "1">
            A185: Variable Set [ 
                Name:%code(%line_num) 
                To:%newline%newline%newline 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] If [ %is_entry_task_description neq 1 ]

            <If Current Line Starts An Exit Task>
            A186: If [ %current_line ~R %regex_exit_task_name_and_code_line ]

                <Get Exit Task Description Name From First Line>
                A187: Variable Search Replace [ 
                    Variable:%description_name 
                    Search:%regex_exit_task_name_and_code_line 
                    Ignore Case:Off 
                    Multi-Line:Off 
                    One Match Only:Off 
                    Store Matches In Array: 
                    Replace Matches:On 
                    Replace With:$1 ] 

                <Append "Exit Task Name: %description_name" To First Line>
                A188: Variable Set [ Name:%code(%line_num) To:Exit Task Name: %description_name Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 Structure Output:Off ] 

            <If Current Line Starts An A Second Entry Task Of An Instant Profile>
            A189: Else If [ %current_line ~R %regex_enter_task_name_and_code_line ]

                <Get Entry Task Description Name From First Line>
                A190: Variable Search Replace [ 
                    Variable:%description_name 
                    Search:%regex_enter_task_name_and_code_line 
                    Ignore Case:Off 
                    Multi-Line:Off 
                    One Match Only:Off 
                    Store Matches In Array: 
                    Replace Matches:On 
                    Replace With:$1 ] 

                <Append "Entry Task Name: %description_name" To First Line>
                A191: Variable Set [ Name:%code(%line_num) To:Entry Task Name: %description_name Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 Structure Output:Off ] 

            A192: End If 

            <Set "1" to is_exit_task_description>
            A193: Variable Set [ 
                Name:%is_exit_task_description 
                To:1 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        A194: End If 

    A195: Else 

        <Get Task Description Name From First Line>
        A196: Variable Search Replace [ 
            Variable:%description_name 
            Search:%regex_task_or_profile_name_and_code_line 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:$1 ] 

        <Set First Line To "Task Name: %description_name">
        A197: Variable Set [ Name:%code(%line_num) To:Task Name: %description_name Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 Structure Output:Off ] 

        A198: Flash [ 
            Text:Formatting "%description_name" Task Description For Markdown 
            Long:Off ] 

    A199: End If 

    A200: Variable Set [ 
        Name:%line_num 
        To:%line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A201: Variable Set [ 
        Name:%current_line 
        To:%code(%line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <If Second Line Of Task Description Equals A Collision Handling Value>
    A202: If [ %current_line ~R %regex_task_collision_handling_value_line ]

        <Remove Pre-existing "^[\s]{4}(%tab)?" Indent>
        A203: Variable Search Replace [ 
            Variable:%code(%line_num) 
            Search:^[\s]{4}(%tab)? 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With: ] 

        <Set Second Line To "Collision Handling: collision_handling_value">
        A204: Variable Set [ 
            Name:%code(%line_num) 
            To:Collision Handling: %code(%line_num) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A205: Variable Set [ 
            Name:%code_start_line_num 
            To:%line_num + 1 
            Recurse Variables:Off 
            Do Maths:On 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A206: Else 

        A207: Variable Set [ 
            Name:%code_start_line_num 
            To:%line_num 
            Recurse Variables:Off 
            Do Maths:On 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A208: End If 

    A209: Variable Set [ 
        Name:%actions_label 
        To:
    Actions: 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Push actions_label At code_start_line_num>
    A210: Array Push [ 
        Variable Array:%code 
        Position:%code_start_line_num 
        Value:%actions_label 
        Fill Spaces:Off ] 

    A211: Variable Set [ 
        Name:%lines_count 
        To:%code(#) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A212: Variable Set [ 
        Name:%code_start_line_num 
        To:%code_start_line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A213: Variable Set [ 
        Name:%line_num 
        To:%code_start_line_num 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A214: Variable Clear [ 
        Name:%current_code_type 
        Pattern Matching:Off 
        Local Variables Only:Off 
        Clear All Variables:Off ] 

    A215: Variable Set [ 
        Name:%current_code_type_line_count 
        To:1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A216: Variable Set [ 
        Name:%current_code_type_start_line_num 
        To:%line_num 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Process Task Code Loop Start>
    A217: Anchor 

    A218: [X] Flash [ 
        Text:%code(%line_num) 
        Long:Off ] 

    A219: Variable Set [ 
        Name:%current_line 
        To:%code(%line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A220: Variable Set [ 
        Name:%next_line_num 
        To:%line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A221: Variable Set [ 
        Name:%next_line 
        To:%code(%next_line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A222: Variable Set [ 
        Name:%next_to_next_line_num 
        To:%line_num + 2 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    A223: Variable Set [ 
        Name:%next_to_next_line 
        To:%code(%next_to_next_line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <If Processing Entry Task And Next Line Contains Only Whitespaces And Next To Next Line Starts An Exit Task Of A Profile Or A Second Entry Task Of An Instant Profile>
    A224: If [ %is_entry_task_description eq 1 & %next_line ~R %regex_whitespace_only_line & %next_to_next_line ~R %regex_exit_task_name_and_code_line |+ %next_to_next_line ~R %regex_enter_task_name_and_code_line ]

        <Set "1" to exit_task_starting_next>
        A225: Variable Set [ 
            Name:%exit_task_starting_next 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Remove Pre-existing "^[\s]+" Indent From Next Line>
        A226: Variable Search Replace [ 
            Variable:%code(%next_line_num) 
            Search:^[\s]+ 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With: ] 

    A227: Else 

        <Set "0" to exit_task_starting_next>
        A228: Variable Set [ 
            Name:%exit_task_starting_next 
            To:0 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A229: End If 

    <If Not Processing Any Code Type>
    A230: If [ %current_code_type eq \%current_code_type ]

        <If Current Line Starts A Comment>
        A231: If [ %current_line ~R %regex_comment_line_start ]

            <Set "comment" To current_code_type>
            A232: Variable Set [ 
                Name:%current_code_type 
                To:comment 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        <If Current Line Starts An Action>
        A233: Else If [ %current_line ~R %regex_action_line_start ]

            <Set "action" To current_code_type>
            A234: Variable Set [ 
                Name:%current_code_type 
                To:action 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        <If Current Line Starts The Exit Task Of A Profile Or A Second Entry Task Of An Instant Profile>
        A235: Else If [ %current_line ~R %regex_exit_task_name_and_code_line | %current_line ~R %regex_enter_task_name_and_code_line ]

            <Goto Process Task Description Start>
            A236: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Process Task Description Start ] 

        <If Current Line Is Empty Or Contains Only Whitespaces>
        A237: Else If [ %current_line eq \%code%line_num | %current_line ~R %regex_whitespace_only_line ]

            <Goto Next Task Line>
            A238: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Next Task Line ] 

        <Else Unknown current_code_type>
        A239: Else 

            A240: Flash [ 
                Text:Error! Unknown Code Type At Line %line_num "%current_line" While Processing "%description_task_name" Description 
                Long:On ] 

            A241: Stop [ 
                With Error:Off 
                Task: ] 

        A242: End If 

        <Set "1" to current_code_type_line_count>
        A243: Variable Set [ 
            Name:%current_code_type_line_count 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Set line_num to current_code_type_start_line_num>
        A244: Variable Set [ 
            Name:%current_code_type_start_line_num 
            To:%line_num 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A245: End If 

    <If First Line Of Action>
    A246: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "Else If", "Else" "End If" Or "End For">
        A247: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

            <Decrement indent_character_count by single_indent_character_count>
            A248: Variable Set [ 
                Name:%indent_character_count 
                To:%indent_character_count - %single_indent_character_count 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        A249: End If 

    A250: End If 

    A251: Variable Clear [ 
        Name:%indent_string 
        Pattern Matching:Off 
        Local Variables Only:Off 
        Clear All Variables:Off ] 

    <Generate indent_string Based On Current indent_character_count>
    A252: For [ 
        Variable:%num 
        Items:1:%indent_character_count ] 

        A253: Variable Set [ 
            Name:%indent_string 
            To:%indent_character 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:On 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A254: End For 

    <If First Line Of Action>
    A255: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "If", "Else If", "Else" Or "For">
        A256: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((If)|(Else If)|(Else)|(For)).* ]

            <Increment indent_character_count by single_indent_character_count>
            A257: Variable Set [ 
                Name:%indent_character_count 
                To:%indent_character_count + %single_indent_character_count 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        A258: End If 

    A259: End If 

    <If Processing Comment>
    A260: If [ %current_code_type eq comment ]

        <Replace Pre-existing "^[\s]{4}(%tab)?" Indent With "%indent_string">
        A261: Variable Search Replace [ 
            Variable:%code(%line_num) 
            Search:^[\s]{4}(%tab)? 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:%indent_string ] 

        <If Comment Ended>
        A262: If [ %current_line ~R %regex_comment_line_end & %next_line ~R %regex_action_line_start ]

            A263: Variable Clear [ 
                Name:%current_code_type 
                Pattern Matching:Off 
                Local Variables Only:Off 
                Clear All Variables:Off ] 

            <If Next Action Is "Else If", "Else" "End If" Or "End For">
            A264: If [ %next_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

                <For Loop From current_code_type_start_line_num to line_num>
                A265: For [ 
                    Variable:%num 
                    Items:%current_code_type_start_line_num:%line_num ] 

                    <Remove Single Indent Prefix>
                    A266: Variable Search Replace [ 
                        Variable:%code(%num) 
                        Search:%regex_single_indent_prefix 
                        Ignore Case:Off 
                        Multi-Line:Off 
                        One Match Only:Off 
                        Store Matches In Array: 
                        Replace Matches:On 
                        Replace With: ] 

                A267: End For 

            A268: End If 

        A269: End If 

    <Else If Processing Action>
    A270: Else If [ %current_code_type eq action ]

        <Replace Pre-existing "^[\s]{4}(%tab)?" Indent With "%indent_string">
        A271: Variable Search Replace [ 
            Variable:%code(%line_num) 
            Search:^[\s]{4}(%tab)? 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:%indent_string ] 

        <If Action Ended>
        A272: If [ %current_code_type_line_count eq 1 &+ %current_line !~ *[* | %current_line ~R %regex_action_line_end & %next_line ~R %regex_action_line_start |+ %next_line ~R %regex_comment_line_start |+ %next_line_num > %lines_count | %exit_task_starting_next eq 1 ]

            <Set "0" to skipping_split_action_parameters_on_multiple_lines>
            A273: Variable Set [ 
                Name:%skipping_split_action_parameters_on_multiple_lines 
                To:0 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <If split_action_parameters_on_multiple_lines Equals "0">
            A274: If [ %split_action_parameters_on_multiple_lines eq 0 ]

                <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
                A275: Variable Set [ 
                    Name:%skipping_split_action_parameters_on_multiple_lines 
                    To:1 
                    Recurse Variables:Off 
                    Do Maths:Off 
                    Append:Off 
                    Max Rounding Digits:3 
                    Structure Output:Off ] If [ %current_code_type_start_line_num < %line_num ]

                <Goto End Action Processing>
                A276: Goto [ 
                    Type:Action Label 
                    Number:1 
                    Label:End Action Processing ] 

            A277: End If 

        A278: Else 

            <Goto Continue Action Processing>
            A279: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Continue Action Processing ] 

        A280: End If 

        <Process End Of Action>
        A281: Anchor 

        A282: Variable Set [ 
            Name:%action_first_line 
            To:%code(%current_code_type_start_line_num) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A283: Variable Set [ 
            Name:%action_all_lines 
            To:%code(%current_code_type_start_line_num:%line_num) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <If Action Does Not Contain Parameters>
        A284: If [ %action_first_line !~R %regex_action_line_with_parameters ]

            <Goto End Action Processing>
            A285: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A286: End If 

        A287: Variable Set [ 
            Name:%action_name 
            To:%action_first_line 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Extract Action Name From First Line Of Action>
        A288: Variable Search Replace [ 
            Variable:%action_name 
            Search:%regex_action_line_with_parameters 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:$1 ] 

        <Set "Else" To action_name If It Is Set To "Else If">
        A289: Variable Set [ 
            Name:%action_name 
            To:Else 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] If [ %action_name eq Else If ]

        <Check if action name exists in action names string array is necessary since otherwise if an invalid action name is passed to get action code function, then a popup/warning is generated in tasker>
        A290: Anchor 

        <If Action Name Exists In non_plugin_action_names_list>
        A291: If [ %non_plugin_action_names_list(#?~R^\Q%action_name\E$) neq 0 ]

            <Goto Get Action Code From Action Name>
            A292: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Get Action Code From Action Name ] 

        <If Action Name Exists In plugin_action_names_list>
        A293: Else If [ %plugin_action_names_list(#?~R^\Q%action_name\E$) neq 0 ]

            <Assume it's a plugin and set action_code to 1000
            
            The action name for plugins is the label of the plugin EDIT_SETTING activity shown in the drop-down when a plugin action of the app is selected. There could be potential conflict if a non plugin action name has been modified to match that of a plugin action name.>
            A294: Variable Set [ 
                Name:%action_code 
                To:1000 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <Goto Find Arguments Size Of Action>
            A295: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Find Arguments Size Of Action ] 

        A296: Else 

            A297: Flash [ 
                Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Action Index "%action_index" In Action Names List 
                Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
            A298: Variable Set [ 
                Name:%skipping_split_action_parameters_on_multiple_lines 
                To:1 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] If [ %current_code_type_start_line_num < %line_num ]

            <Goto End Action Processing>
            A299: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A300: End If 

        <Get Action Code From Action Name>
        A301: Java Function [ 
            Return:%action_code 
            Class Or Object:%tcujv_c_taskeractionslist 
            Function:%tcujv_cm_taskeractionslist_getactioncodebyname
        {int} (String) 
            Param:%action_name 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Continue Task After Error:On ] 

        <If Action Code Is Not Valid>
        A302: If [ %action_code !~R %regex_valid_number | %action_code < 1 ]

            A303: Flash [ 
                Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Action Code "%action_code" 
                Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
            A304: Variable Set [ 
                Name:%skipping_split_action_parameters_on_multiple_lines 
                To:1 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] If [ %current_code_type_start_line_num < %line_num ]

            <Goto End Action Processing>
            A305: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A306: End If 

        <Find Arguments Size Of Action>
        A307: Anchor 

        A308: Java Function [ 
            Return:%arguments_list_size 
            Class Or Object:%tcujv_c_taskeractionslist 
            Function:%tcujv_cm_taskeractionslist_getargssizeofactionwithcode
        {int} (int) 
            Param:%action_code 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Param: 
            Continue Task After Error:On ] 

        <If Arguments Size Of Action Is Invalid>
        A309: If [ %arguments_list_size !~R %regex_valid_number ]

            A310: Flash [ 
                Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Arguments List Size "%arguments_list_size" 
                Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Goto End Action Processing>
            A311: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A312: End If 

        A313: Variable Set [ 
            Name:%arguments_list_size 
            To:%arguments_list_size - 1 
            Recurse Variables:Off 
            Do Maths:On 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        A314: Array Clear [ 
            Variable Array:%argument_names_list ] 

        <For Loop On All Argument Names In Of Action>
        A315: For [ 
            Variable:%num 
            Items:0:%arguments_list_size ] If [ %arguments_list_size > -1 ]

            A316: Java Function [ 
                Return:%argument_name 
                Class Or Object:%tcujv_c_taskeractionslist 
                Function:%tcujv_cm_taskeractionslist_getargnameatindexofactionwithcode
            {String} (Resources, int, int) 
                Param:resources 
                Param:%action_code 
                Param:%num 
                Param: 
                Param: 
                Param: 
                Param: ] 

            A317: [X] Flash [ 
                Text:argument_name: "%argument_name" 
                Long:Off ] 

            A318: Variable Set [ 
                Name:%position 
                To:%argument_names_list(#) + 1 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <Push argument_name into argument_names_list>
            A319: Array Push [ 
                Variable Array:%argument_names_list 
                Position:%position 
                Value:%argument_name 
                Fill Spaces:Off ] 

        A320: End For 

        A321: [X] Flash [ 
            Text:%argument_names_list() 
            Long:Off ] 

        A322: Variable Set [ 
            Name:%position 
            To:%argument_names_list(#) + 1 
            Recurse Variables:Off 
            Do Maths:On 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Push "Continue Task After Error" into argument_names_list>
        A323: Array Push [ 
            Variable Array:%argument_names_list 
            Position:%position 
            Value:Continue Task After Error 
            Fill Spaces:Off ] 

        A324: Array Clear [ 
            Variable Array:%argument_names_to_replace_list ] 

        <For Loop On All Argument Names In argument_names_list>
        A325: For [ 
            Variable:%num 
            Items:1:%argument_names_list(#) ] If [ %argument_names_list(#) > 0 ]

            A326: Variable Set [ 
                Name:%argument_name 
                To:%argument_names_list(%num) 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            A327: Variable Set [ 
                Name:%argument_name_for_regex 
                To:\Q%argument_name\E 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            A328: Variable Set [ 
                Name:%regex_argument_name_repeated 
                To:.*%argument_name_for_regex:.*%argument_name_for_regex:.* 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <If Arguments Name Is Repeated In Action Description And Action Code Not In force_split_action_parameters_on_multiple_lines_action_codes, Then Not Safe To Split Action On Multiple Lines>
            A329: If [ %action_all_lines ~R %regex_argument_name_repeated & ,%force_split_action_parameters_on_multiple_lines_action_codes, !~ *,%action_code,* ]

                A330: Flash [ 
                    Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Argument Name "%argument_name" Repetition 
                    Long:Off ] If [ %enable_flash_actions eq 1 ]

                <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
                A331: Variable Set [ 
                    Name:%skipping_split_action_parameters_on_multiple_lines 
                    To:1 
                    Recurse Variables:Off 
                    Do Maths:Off 
                    Append:Off 
                    Max Rounding Digits:3 
                    Structure Output:Off ] If [ %current_code_type_start_line_num < %line_num ]

                <Goto End Action Processing>
                A332: Goto [ 
                    Type:Action Label 
                    Number:1 
                    Label:End Action Processing ] 

            A333: End If 

            A334: Variable Set [ 
                Name:%position 
                To:%argument_names_to_replace_list(#) + 1 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            A335: Array Push [ 
                Variable Array:%argument_names_to_replace_list 
                Position:%position 
                Value:%argument_name 
                Fill Spaces:Off ] 

        A336: End For 

        <For Loop On All Argument Names In argument_names_to_replace_list>
        A337: For [ 
            Variable:%num 
            Items:1:%argument_names_to_replace_list(#) ] If [ %argument_names_to_replace_list(#) > 0 ]

            A338: Variable Set [ 
                Name:%argument_name 
                To:%argument_names_to_replace_list(%num) 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            A339: [X] Flash [ 
                Text:%argument_name 
                Long:Off ] 

            A340: Variable Set [ 
                Name:%argument_name_for_regex 
                To:\Q%argument_name\E 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            A341: Variable Set [ 
                Name:%regex_argument_name_exists 
                To:(.*)(%argument_name_for_regex:.*) 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <For Loop From current_code_type_start_line_num to line_num>
            A342: For [ 
                Variable:%num1 
                Items:%current_code_type_start_line_num:%line_num ] 

                <If Action Line Contains The Argument Name>
                A343: If [ %code(%num1) ~R %regex_argument_name_exists ]

                    <Add "%newline%indent_string%single_indent_string" Before argument_name>
                    A344: Variable Search Replace [ 
                        Variable:%code(%num1) 
                        Search:%regex_argument_name_exists 
                        Ignore Case:Off 
                        Multi-Line:Off 
                        One Match Only:On 
                        Store Matches In Array: 
                        Replace Matches:On 
                        Replace With:$1%newline%indent_string%single_indent_string$2 ] 

                    <Goto Start Of For Loop On All Argument Names In argument_names_to_replace_list>
                    A345: Goto [ 
                        Type:Action Label 
                        Number:1 
                        Label:For Loop On All Argument Names In argument_names_to_replace_list ] 

                A346: End If 

            A347: End For 

        A348: End For 

        <End Action Processing>
        A349: Anchor 

        <If skipping_split_action_parameters_on_multiple_lines Equals "1">
        A350: If [ %skipping_split_action_parameters_on_multiple_lines eq 1 ]

            A351: Variable Set [ 
                Name:%current_code_type_start_line_num_plus_1 
                To:%current_code_type_start_line_num + 1 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 
                Structure Output:Off ] 

            <For Loop From current_code_type_start_line_num_plus_1+1 to line_num>
            A352: For [ 
                Variable:%num 
                Items:%current_code_type_start_line_num_plus_1:%line_num ] If [ %current_code_type_start_line_num < %line_num ]

                <Replace Previously Set "^%indent_string" Indent With "%indent_string%single_indent_string">
                A353: Variable Search Replace [ 
                    Variable:%code(%num) 
                    Search:^%indent_string 
                    Ignore Case:Off 
                    Multi-Line:Off 
                    One Match Only:Off 
                    Store Matches In Array: 
                    Replace Matches:On 
                    Replace With:%indent_string%single_indent_string ] 

            A354: End For 

        A355: End If 

        A356: Variable Clear [ 
            Name:%current_code_type 
            Pattern Matching:Off 
            Local Variables Only:Off 
            Clear All Variables:Off ] 

        <Append Newline To Line>
        A357: Variable Set [ 
            Name:%code(%line_num) 
            To:%newline 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:On 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <Continue Action Processing>
        A358: Anchor 

    A359: End If 

    A360: Variable Set [ 
        Name:%current_code_type_line_count 
        To:%current_code_type_line_count + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Next Task Line>
    A361: Anchor 

    A362: Variable Set [ 
        Name:%line_num 
        To:%line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 
        Structure Output:Off ] 

    <Goto Process Task Code Loop Start>
    A363: Goto [ 
        Type:Action Label 
        Number:1 
        Label:Process Task Code Loop Start ] If [ %line_num < %lines_count + 1 ]

    <Process Task Code Loop End>
    A364: Anchor 

    <Join Code Array On Newline>
    A365: Variable Join [ 
        Name:%code 
        Joiner:%newline 
        Delete Parts:Off ] 

    <If cap_indents_at_max_indent_character_count Equals "1">
    A366: If [ %cap_indents_at_max_indent_character_count eq 1 ]

        A367: Variable Clear [ 
            Name:%indent_string 
            Pattern Matching:Off 
            Local Variables Only:Off 
            Clear All Variables:Off ] 

        <Generate indent_string Based On max_indent_character_count>
        A368: For [ 
            Variable:%num 
            Items:1:%max_indent_character_count ] 

            A369: Variable Set [ 
                Name:%indent_string 
                To:%indent_character 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:On 
                Max Rounding Digits:3 
                Structure Output:Off ] 

        A370: End For 

        <Replace Indents Greater Than max_indent_character_count With "%indent_string">
        A371: Variable Search Replace [ 
            Variable:%code 
            Search:%regex_set_max_indent 
            Ignore Case:Off 
            Multi-Line:On 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:%indent_string ] 

    A372: End If 

    <If convert_code_to_markdown_code_block Equals "1">
    A373: If [ %convert_code_to_markdown_code_block eq 1 ]

        A374: Variable Set [ 
            Name:%code_for_shell 
            To:%code 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <replace all single quotes (') with nothing>
        A375: Variable Search Replace [ 
            Variable:%code_for_shell 
            Search:' 
            Ignore Case:Off 
            Multi-Line:On 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With: ] If [ %code Set ]

        <Find Backticks To Print>
        A376: Run Shell [ 
            Command:code='%code_for_shell'
        
        backtick='`'
        current_consecutive_backticks_count=0
        max_consecutive_backticks_count=0
        backticks_to_print=""
        
        index=0
        while [ $index -lt ${#code} ]
        do
            character="${code:$index:1}"
        if [ "$character" = '`' ]; then
        	current_consecutive_backticks_count=$(( current_consecutive_backticks_count + 1 ))
        	if [ $current_consecutive_backticks_count -gt $max_consecutive_backticks_count ]; then
        		max_consecutive_backticks_count=$current_consecutive_backticks_count
        	fi
        else
        	current_consecutive_backticks_count=0
        fi
        
            index=$(( index + 1 ))
        done
        
        backticks_count_to_print="$((max_consecutive_backticks_count + 3))"
        
        #create a string with n backticks where n==backticks_count_to_print
        index=0
        while [ $index -lt $backticks_count_to_print ]
        do
            backticks_to_print="$backticks_to_print$backtick"
            index=$(( index + 1 ))
        done
        
        
        #echo backticks_to_print to stdout
        echo "$backticks_to_print" 
            Timeout (Seconds):0 
            Use Root:Off 
            Store Output In:%backticks_to_print 
            Store Errors In:%errors 
            Store Result In: 
            Continue Task After Error:On ] 

        A377: Variable Set [ 
            Name:%exit_code 
            To:%err 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

        <If Failed>
        A378: If [ %exit_code neq \%err | %errors Set ]

            A379: Flash [ 
                Text:Failed To Find Backticks To Print To Convert "%description_task_name" Task Description To Markdown Code Block
            %task_name Failed
            
            exit_code = "%exit_code"
            
            errors =
            "
            %errors
            "
            
            output =
            "
            %backticks_to_print
            " 
                Long:On ] 

            A380: Stop [ 
                With Error:Off 
                Task: ] 

        A381: End If 

        <Convert Code To Markdown Code Block>
        A382: Variable Set [ 
            Name:%code 
            To:%backticks_to_print
        %code
        %backticks_to_print 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 
            Structure Output:Off ] 

    A383: End If 

    A384: Flash [ 
        Text:Format Complete 
        Long:Off ] If [ %par1 eq \%par1 ]

    <If set_clipboard_to_formatted_code Equals "1">
    A385: If [ %set_clipboard_to_formatted_code eq 1 ]

        <Set code To Clipboard Text>
        A386: Set Clipboard [ 
            Text:%code 
            Add:Off ] 

    A387: End If 

    <Return>
    A388: Anchor 

    A389: Return [ 
        Value:%code 
        Stop:On 
        Local Variable Passthrough:Off 
        Replace On Passthrough:Off 
        Limit Passthrough To: ] 
``````

##
&nbsp;


*This file was automatically generated using [tasker_config_utils v0.5.0](https://github.com/Taskomater/tasker_config_utils).*
