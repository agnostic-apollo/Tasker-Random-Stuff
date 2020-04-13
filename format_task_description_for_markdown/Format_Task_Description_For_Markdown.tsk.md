# Format Task Description For Markdown

## Export Info:
**Tasker Version:** `5.9.3.beta.2`  
**Timestamp:** `2020-04-13 16.18.08`  
**sha256sum:** `cebc2a877f0d927f39527645c87fe5f0dc9f940fc609879c76d065343d8643cf`  



## Profile Names:
**Count:** `0`




## Scene Names:
**Count:** `0`




## Task Names:
**Count:** `1`

- *`Format Task Description For Markdown`*



## Profiles Info:



## Tasks Info:

**#:** `1`  
**Name:** `Format Task Description For Markdown`  
**ID:** `875`  
**Collision Handling:** `Abort New Task`  
**Keep Device Awake:** `false`  
**Help:**
```
A helper task to format an exported tasker task description/code into a more readable and markdown compatible format for websites like reddit and github.

For basic usage, just run this task after running "Export" -> "Description To Clipboard" on a task and it will read the description from the %CLIP variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents.


If %par1 is not passed, then default values are automatically used.

If it is passed then it's parameters must be set to the following:

indent_character_type is the type of character that should be used for indents. Valid values are "space" and "tab". Default value is "space".

min_indent_character_count is the minimum indent that should be present for actions and comments. It must be a valid integer. Default value is "4".

max_indent_character_count is the maximum indent that should be present for actions and comments depending "If" and "For" related actions. It must be a valid integer and is only considered if cap_indents_at_max_indent_character_count is set to "1" and it must not be less than min_indent_character_count. Default value is "12".

single_indent_character_count is a number of characters of indent_character_type that must be considered as one indent. It can be same as min_indent_character_count. It must be a valid integer and must not be greater than min_indent_character_count. Default value is "4".

cap_indents_at_max_indent_character_count is a toggle that decides if there should be limit on max indents based on max_indent_character_count. This is helpful if too many nested conditions exist in the task increasing the indents to a point that it makes it harder to read without using horizontal scrolling. It must be set to "0" or "1". Default value is "0".

convert_code_to_markdown_code_block is a toggle that decides whether the formatted code should automatically be converted to markdown code block by prefixing and suffixing the code with a minimum of 3 backticks. This is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default. Moreover, the task automatically checks if the code itself contains any backticks and then uses (max numbers of consecutive backticks found + 3) backticks for prefixing and suffixing so that any backticks in the code can be escaped and the entire code is enclosed in the code block. It must be set to "0" or "1". Default value is "1".

set_clipboard_to_formatted_code is a toggle that decides if the formatted code is put back in the clipboard using the "Set Clipboard" action at the end. It must be set to "0" or "1". Default value is "1".


If %par2 is not passed, then data from the clipboard using the tasker variable %CLIP is used as the code.

If %par2 is passed, then it is used as the code.

The first line of the task description must be in the format "task_name (task_code)". It can optionally be prefixed with zero or more whitespace characters.


Input %par1: #optional
"
indent_character_type
min_indent_character_count
max_indent_character_count
single_indent_character_count
cap_indents_at_max_indent_character_count
convert_code_to_markdown_code_block
set_clipboard_to_formatted_code
"

Input %par2: #optional
"
code
"

Returns:
"
formatted_code
"

If task is successful, then formatted_code will contain the formatted code description.
Otherwise it will not be set.
```
##

