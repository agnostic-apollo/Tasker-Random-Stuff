````
Task Name: Format Task Description For Markdown

Actions:
    <A helper task to format an exported tasker task description/code into a more readable and markdown compatible format for websites like reddit and github.
    
    For basic usage, just run this task after running "Export" -> "Description To Clipboard" on a task and it will read the description from the %CLIP variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents.
    
    
    If %par1 is not passed, then default values are automatically used.
    
    If it is passed then it's parameters must be set to the following:
    
    indent_character_type is the type of character that should be used for indents. Valid values are "space" and "tab". Default value is "space".
    
    min_indent_character_count is the minimum indent that should be present for actions and comments. It must be a valid integer. Default value is "4".
    
    max_indent_character_count is the maximum indent that should be present for actions and comments depending "If" and "For" related actions. It must be a valid integer and is only considered if cap_indents_at_max_indent_character_count is set to "1" and it must not be less than min_indent_character_count. Default value is "12".
    
    single_indent_character_count is a number of characters of indent_character_type that must be considered as one indent. It can be same as min_indent_character_count. It must be a valid integer and must not be greater than min_indent_character_count. Default value is "4".
    
    split_action_parameters_on_multiple_lines is a toggle that decides if parameters of actions in description are split over multiple lines or not. If this is enabled, then each parameter will be on a different line making it easier to read. It should work for most actions but will not work for actions whose action name is modified depending on its configuration other than the "Else" action whose name is modified to "Else If" if there is a condition added to it. It will also not for plugins and actions whose parameter names are repeated in the description in any way. This uses experimental code including tasker internal java functions. Use at your own risk. Disable it if it is not working properly or you are receiving exceptions. Enabling this will also slow down the task even more than normal because of all the extra processing. It must be set to "0" or "1". Default value is "1".
    
    cap_indents_at_max_indent_character_count is a toggle that decides if there should be limit on max indents based on max_indent_character_count. This is helpful if too many nested conditions exist in the task increasing the indents to a point that it makes it harder to read without using horizontal scrolling. It must be set to "0" or "1". Default value is "0".
    
    convert_code_to_markdown_code_block is a toggle that decides whether the formatted code should automatically be converted to markdown code block by prefixing and suffixing the code with a minimum of 3 backticks. This is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default. Moreover, the task automatically checks if the code itself contains any backticks and then uses (max numbers of consecutive backticks found + 3) backticks for prefixing and suffixing so that any backticks in the code can be escaped and the entire code is enclosed in the code block. It must be set to "0" or "1". Default value is "1".
    
    set_clipboard_to_formatted_code is a toggle that decides if the formatted code is put back in the clipboard using the "Set Clipboard" action at the end. It must be set to "0" or "1". Default value is "1".
    
    
    If %par2 is not passed, then data from the clipboard using the tasker variable %CLIP is used as the code.
    
    If %par2 is passed, then it is used as the code.
    
    The first line of the task description must be in the format "task_name (task_code)". It can optionally be prefixed with zero or more whitespace characters.
    
    Depending on the number of actions, the device specs and the parameters, it will take a few seconds to a minute to format the description.
    
    
    Comments:
    "
    **version_number**: `0.1.0`
    "
    
    Input %par1: #optional
    "
    indent_character_type
    min_indent_character_count
    max_indent_character_count
    single_indent_character_count
    cap_indents_at_max_indent_character_count
    split_action_parameters_on_multiple_lines
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
    Otherwise it will not be set.>
    A1: Anchor 

    A2: Variable Set [ 
        Name:%task_name 
        To:Format Task Description For Markdown 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Enable this action if you want to flash log messages while running this task>
    A3: [X] Variable Set [ 
        Name:%enable_flash_actions 
        To:1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Set Newline Character>
    A4: Variable Set [ 
        Name:%newline 
        To:
     
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Parse And Validate Parameters>
    A5: Anchor 

    A6: [X] Variable Set [ 
        Name:%par1 
        To:space
    4
    12
    4
    1
    0
    1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <If %par1 Not Received>
    A7: If [ %par1 eq \%par1 ]

        <Set User Modifiable Variables Start>
        A8: Anchor 

        <Set indent_character_type
        Default: "space">
        A9: Variable Set [ 
            Name:%indent_character_type 
            To:space 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set min_indent_character_count
        Default: "4">
        A10: Variable Set [ 
            Name:%min_indent_character_count 
            To:4 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set max_indent_character_count
        Default: "12">
        A11: Variable Set [ 
            Name:%max_indent_character_count 
            To:12 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set single_indent_character_count
        Default: "4">
        A12: Variable Set [ 
            Name:%single_indent_character_count 
            To:4 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set cap_indents_at_max_indent_character_count
        Default: "0">
        A13: Variable Set [ 
            Name:%cap_indents_at_max_indent_character_count 
            To:0 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set split_action_parameters_on_multiple_lines
        Default: "1">
        A14: Variable Set [ 
            Name:%split_action_parameters_on_multiple_lines 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set convert_code_to_markdown_code_block
        Default: "1">
        A15: Variable Set [ 
            Name:%convert_code_to_markdown_code_block 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set set_clipboard_to_formatted_code
        Default: "1">
        A16: Variable Set [ 
            Name:%set_clipboard_to_formatted_code 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set User Modifiable Variables End>
        A17: Anchor 

    A18: Else 

        A19: Variable Set [ 
            Name:%format_task_description_for_markdown_parameter_1 
            To:%par1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        A20: Variable Split [ 
            Name:%format_task_description_for_markdown_parameter_1 
            Splitter:%newline 
            Delete Base:Off ] 

        <Set indent_character_type>
        A21: Variable Set [ 
            Name:%indent_character_type 
            To:%format_task_description_for_markdown_parameter_1(1) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set min_indent_character_count>
        A22: Variable Set [ 
            Name:%min_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(2) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set max_indent_character_count>
        A23: Variable Set [ 
            Name:%max_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(3) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set single_indent_character_count>
        A24: Variable Set [ 
            Name:%single_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(4) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set cap_indents_at_max_indent_character_count>
        A25: Variable Set [ 
            Name:%cap_indents_at_max_indent_character_count 
            To:%format_task_description_for_markdown_parameter_1(5) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set split_action_parameters_on_multiple_lines>
        A26: Variable Set [ 
            Name:%split_action_parameters_on_multiple_lines 
            To:%split_action_parameters_on_multiple_lines(6) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set convert_code_to_markdown_code_block>
        A27: Variable Set [ 
            Name:%convert_code_to_markdown_code_block 
            To:%format_task_description_for_markdown_parameter_1(7) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set set_clipboard_to_formatted_code>
        A28: Variable Set [ 
            Name:%set_clipboard_to_formatted_code 
            To:%format_task_description_for_markdown_parameter_1(8) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A29: End If 

    <If %par2 Not Received>
    A30: If [ %par2 eq \%par2 ]

        <Set Clipboard Text To code>
        A31: Variable Set [ 
            Name:%code 
            To:%CLIP 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A32: Else 

        <Set %par2 To code>
        A33: Variable Set [ 
            Name:%code 
            To:%par2 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A34: End If 

    <Set Tab Character>
    A35: Variable Set [ 
        Name:%tab 
        To:	 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Set Space Character>
    A36: Variable Set [ 
        Name:%space 
        To:  
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <If indent_character_type Is Set To "space">
    A37: If [ %indent_character_type eq space ]

        <Set "%space" to indent_character>
        A38: Variable Set [ 
            Name:%indent_character 
            To:%space 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    <If indent_character_type Is Set To "tab">
    A39: Else If [ %indent_character_type eq tab ]

        <Set "%tab" to indent_character>
        A40: Variable Set [ 
            Name:%indent_character 
            To:%tab 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A41: End If 

    <Set Default Indent Character Count>
    A42: Variable Set [ 
        Name:%indent_character_count 
        To:%min_indent_character_count 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A43: Variable Set [ 
        Name:%regex_single_indent_prefix 
        To:^[%indent_character]{%single_indent_character_count} 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A44: Variable Set [ 
        Name:%regex_set_max_indent 
        To:^[%indent_character]{%max_indent_character_count,} 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A45: Variable Set [ 
        Name:%regex_valid_number 
        To:^[0-9]+$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A46: Variable Set [ 
        Name:%regex_valid_bool_value 
        To:^[0-1]$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A47: Variable Set [ 
        Name:%regex_action_line_start 
        To:^[\s]+A[0-9]+: . 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A48: Variable Set [ 
        Name:%regex_action_line_end 
        To: \](%space)?$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A49: Variable Set [ 
        Name:%regex_action_line_with_parameters 
        To:^[\s]+A[0-9]+: (?:\[X\] )?([^\\\[]+) \[.* 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A50: Variable Set [ 
        Name:%regex_comment_line_start 
        To:^[\s]+\< 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A51: Variable Set [ 
        Name:%regex_comment_line_end 
        To:\>$ 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A52: Test Variable [ 
        Type:Length 
        Data:%indent_character 
        Store Result In:%indent_character_length Continue Task After Error:On ] 

    A53: If [ %indent_character neq %space &+ %indent_character neq %tab | %indent_character_length neq 1 | %min_indent_character_count !~R %regex_valid_number | %cap_indents_at_max_indent_character_count !~R %regex_valid_bool_value | %cap_indents_at_max_indent_character_count eq 1 & %max_indent_character_count !~R %regex_valid_number |+ %max_indent_character_count < %min_indent_character_count | %single_indent_character_count !~R %regex_valid_number | %single_indent_character_count > %min_indent_character_count | %convert_code_to_markdown_code_block !~R %regex_valid_bool_value | %set_clipboard_to_formatted_code !~R %regex_valid_bool_value | %split_action_parameters_on_multiple_lines !~R %regex_valid_bool_value ]

        A54: Flash [ 
            Text:Invalid Parameters To %task_name
        %task_name Failed
        
        indent_character_type = "%indent_character_type"
        
        min_indent_character_count = "%min_indent_character_count"
        
        max_indent_character_count = "%max_indent_character_count"
        
        single_indent_character_count = "%single_indent_character_count"
        
        cap_indents_at_max_indent_character_count = "%cap_indents_at_max_indent_character_count"
        
        split_action_parameters_on_multiple_lines = "%split_action_parameters_on_multiple_lines"
        
        convert_code_to_markdown_code_block = "%convert_code_to_markdown_code_block"
        
        set_clipboard_to_formatted_code = "%set_clipboard_to_formatted_code" 
            Long:On ] 

        A55: Stop [ 
            With Error:Off 
            Task: ] 

    A56: End If 

    <Generate single_indent_string Based On Current single_indent_character_count>
    A57: For [ 
        Variable:%num 
        Items:1:%single_indent_character_count ] 

        A58: Variable Set [ 
            Name:%single_indent_string 
            To:%indent_character 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:On 
            Max Rounding Digits:3 ] 

    A59: End For 

    <Task Start>
    A60: Anchor 

    <Split Code On Newline To Create Code Array>
    A61: Variable Split [ 
        Name:%code 
        Splitter:%newline 
        Delete Base:Off ] 

    <Check If First Line Consists Of Task Name And Code>
    A62: If [ %code(1) !~R ^[\s]*(.+) \([0-9]+\)$ ]

        A63: Flash [ 
            Text:Error! Task Name And Code Not Found In Line 1 Of Task Description Being Used
        %task_name Failed
        
        Line 1 = "%code(1)" 
            Long:On ] 

        A64: Stop [ 
            With Error:Off 
            Task: ] 

    A65: End If 

    A66: Variable Set [ 
        Name:%description_task_name 
        To:%code(1) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Get Description Task Name From First Line>
    A67: Variable Search Replace [ 
        Variable:%description_task_name 
        Search:^[\s]*(.+) \([0-9]+\)$ 
        Ignore Case:Off 
        Multi-Line:Off 
        One Match Only:Off 
        Store Matches In Array: 
        Replace Matches:On 
        Replace With:$1 ] 

    A68: Flash [ 
        Text:Formatting "%description_task_name" Task Description For Markdown 
        Long:Off ] 

    <Set Line 1 To "Task Name: %description_task_name">
    A69: Variable Set [ Name:%code(1) To:Task Name: %description_task_name Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If Second Line Equals "Abort New Task", "Abort Existing Task" Or "Run Both Together">
    A70: If [ %code(2) ~R ^[\s]+(Abort New Task)|(Abort Existing Task)|(Run Both Together)$ ]

        <Remove Pre-existing "^[\s]{4}(%tab)?" Indent>
        A71: Variable Search Replace [ 
            Variable:%code(2) 
            Search:^[\s]{4}(%tab)? 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With: ] 

        <Set Line 1 To "Collision Handling: %code(2)">
        A72: Variable Set [ 
            Name:%code(2) 
            To:Collision Handling: %code(2) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        A73: Variable Set [ 
            Name:%code_start_line_num 
            To:3 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A74: Else 

        A75: Variable Set [ 
            Name:%code_start_line_num 
            To:2 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A76: End If 

    A77: Variable Set [ 
        Name:%actions_label 
        To:
    Actions: 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Push actions_label At code_start_line_num>
    A78: Array Push [ 
        Variable Array:%code 
        Position:%code_start_line_num 
        Value:%actions_label 
        Fill Spaces:Off ] 

    A79: Variable Set [ 
        Name:%code_start_line_num 
        To:%code_start_line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 ] 

    A80: Variable Set [ 
        Name:%lines_count 
        To:%code(#) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Remove Last Line If Only Whitespaces>
    A81: Array Pop [ 
        Variable Array:%code 
        Position:%lines_count 
        To Var: ] If [ %code(%lines_count) ~R ^[\s]+$ ]

    A82: Variable Set [ 
        Name:%lines_count 
        To:%code(#) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A83: Variable Set [ 
        Name:%line_num 
        To:%code_start_line_num 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A84: Variable Clear [ 
        Name:%current_code_type 
        Pattern Matching:Off 
        Local Variables Only:Off 
        Clear All Variables:Off ] 

    A85: Variable Set [ 
        Name:%current_code_type_line_count 
        To:1 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A86: Variable Set [ 
        Name:%current_code_type_start_line_num 
        To:%line_num 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <If split_action_parameters_on_multiple_lines Equals "1">
    A87: If [ %split_action_parameters_on_multiple_lines eq 1 ]

        A88: Java Function [ Return:resources Class Or Object:CONTEXT Function:getResources
            {Resources} () Param: Param: Param: Param: Param: Param: Param: ] 

        A89: Java Function [ Return:action_names_list Class Or Object:net.dinglisch.android.taskerm.n Function:l
            {List} () Param: Param: Param: Param: Param: Param: Param: ] 

        A90: Java Function [ Return: Class Or Object:Objects Function:requireNonNull
            {Object} (Object) Param:action_names_list Param: Param: Param: Param: Param: Param: Continue Task After Error:On ] 

        <If exception not raised>
        A91: If [ %err eq \%err ]

            A92: Variable Set [ 
                Name:%is_action_names_list_null 
                To:false 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

        <Else if exception raised>
        A93: Else 

            A94: Variable Set [ 
                Name:%is_action_names_list_null 
                To:true 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

        A95: End If 

        A96: Java Function [ Return:%action_names_list_size Class Or Object:action_names_list Function:size
            {int} () Param: Param: Param: Param: Param: Param: Param: ] If [ %is_action_names_list_null eq false ]

        A97: If [ %action_names_list_size eq 0 | %is_action_names_list_null eq true ]

            A98: Flash [ 
                Text:Error! Failed To Get List Of All Action Names In Tasker
            %task_name Failed 
                Long:On ] 

            A99: Stop [ 
                With Error:Off 
                Task: ] 

        A100: End If 

        A101: Java Function [ Return:new_string_array Class Or Object:String[] Function:new
            {String[]} (int) Param:%action_names_list_size Param: Param: Param: Param: Param: Param: ] 

        A102: Java Function [ Return:action_names_string_array Class Or Object:action_names_list Function:toArray
            {Object[]} (Object[]) Param:new_string_array Param: Param: Param: Param: Param: Param: ] 

    A103: End If 

    <Start Of Process Code Loop>
    A104: Anchor 

    A105: [X] Flash [ 
        Text:%code(%line_num) 
        Long:Off ] 

    A106: Variable Set [ 
        Name:%next_line_num 
        To:%line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 ] 

    A107: Variable Set [ 
        Name:%current_line 
        To:%code(%line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    A108: Variable Set [ 
        Name:%next_line 
        To:%code(%next_line_num) 
        Recurse Variables:Off 
        Do Maths:Off 
        Append:Off 
        Max Rounding Digits:3 ] 

    <If Not Processing Any Code Type>
    A109: If [ %current_code_type eq \%current_code_type ]

        <If Current Line Starts A Comment>
        A110: If [ %current_line ~R %regex_comment_line_start ]

            <Set "comment" To current_code_type>
            A111: Variable Set [ 
                Name:%current_code_type 
                To:comment 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

        <If Current Line Starts An Action>
        A112: Else If [ %current_line ~R %regex_action_line_start ]

            <Set "action" To current_code_type>
            A113: Variable Set [ 
                Name:%current_code_type 
                To:action 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

        <If Current Line Is Empty>
        A114: Else If [ %current_line eq \%code%line_num ]

            <Goto Next Line>
            A115: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Next Line ] 

        <Else Unknown current_code_type>
        A116: Else 

            A117: Flash [ 
                Text:Error! Unknown Code Type At Line %line_num "%current_line" While Processing "%description_task_name" Description 
                Long:On ] 

            A118: Stop [ 
                With Error:Off 
                Task: ] 

        A119: End If 

        <Set "1" to current_code_type_line_count>
        A120: Variable Set [ 
            Name:%current_code_type_line_count 
            To:1 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Set line_num to current_code_type_start_line_num>
        A121: Variable Set [ 
            Name:%current_code_type_start_line_num 
            To:%line_num 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A122: End If 

    <If First Line Of Action>
    A123: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "Else If", "Else" "End If" Or "End For">
        A124: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

            <Decrement indent_character_count by single_indent_character_count>
            A125: Variable Set [ 
                Name:%indent_character_count 
                To:%indent_character_count - %single_indent_character_count 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 ] 

        A126: End If 

    A127: End If 

    A128: Variable Clear [ 
        Name:%indent_string 
        Pattern Matching:Off 
        Local Variables Only:Off 
        Clear All Variables:Off ] 

    <Generate indent_string Based On Current indent_character_count>
    A129: For [ 
        Variable:%num 
        Items:1:%indent_character_count ] 

        A130: Variable Set [ 
            Name:%indent_string 
            To:%indent_character 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:On 
            Max Rounding Digits:3 ] 

    A131: End For 

    <If First Line Of Action>
    A132: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "If", "Else If", "Else" Or "For">
        A133: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((If)|(Else If)|(Else)|(For)).* ]

            <Increment indent_character_count by single_indent_character_count>
            A134: Variable Set [ 
                Name:%indent_character_count 
                To:%indent_character_count + %single_indent_character_count 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 ] 

        A135: End If 

    A136: End If 

    <If Processing Comment>
    A137: If [ %current_code_type eq comment ]

        <Replace Pre-existing "^[\s]{4}(%tab)?" Indent With "%indent_string">
        A138: Variable Search Replace [ 
            Variable:%code(%line_num) 
            Search:^[\s]{4}(%tab)? 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:%indent_string ] 

        <If Comment Ended>
        A139: If [ %current_line ~R %regex_comment_line_end & %next_line ~R %regex_action_line_start ]

            A140: Variable Clear [ 
                Name:%current_code_type 
                Pattern Matching:Off 
                Local Variables Only:Off 
                Clear All Variables:Off ] 

            <If Next Action Is "Else If", "Else" "End If" Or "End For">
            A141: If [ %next_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

                <For Loop From current_code_type_start_line_num to line_num>
                A142: For [ 
                    Variable:%num 
                    Items:%current_code_type_start_line_num:%line_num ] 

                    <Remove Single Indent Prefix>
                    A143: Variable Search Replace [ 
                        Variable:%code(%num) 
                        Search:%regex_single_indent_prefix 
                        Ignore Case:Off 
                        Multi-Line:Off 
                        One Match Only:Off 
                        Store Matches In Array: 
                        Replace Matches:On 
                        Replace With: ] 

                A144: End For 

            A145: End If 

        A146: End If 

    <Else If Processing Action>
    A147: Else If [ %current_code_type eq action ]

        <Replace Pre-existing "^[\s]{4}(%tab)?" Indent With "%indent_string">
        A148: Variable Search Replace [ 
            Variable:%code(%line_num) 
            Search:^[\s]{4}(%tab)? 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:%indent_string ] 

        <If Action Ended>
        A149: If [ %current_code_type_line_count eq 1 &+ %current_line !~ *[* | %current_line ~R %regex_action_line_end & %next_line ~R %regex_action_line_start |+ %next_line ~R %regex_comment_line_start ]

            <Set "0" to skipping_split_action_parameters_on_multiple_lines>
            A150: Variable Set [ 
                Name:%skipping_split_action_parameters_on_multiple_lines 
                To:0 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

            <If split_action_parameters_on_multiple_lines Equals "0">
            A151: If [ %split_action_parameters_on_multiple_lines eq 0 ]

                <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
                A152: Variable Set [ 
                    Name:%skipping_split_action_parameters_on_multiple_lines 
                    To:1 
                    Recurse Variables:Off 
                    Do Maths:Off 
                    Append:Off 
                    Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

                <Goto End Action Processing>
                A153: Goto [ 
                    Type:Action Label 
                    Number:1 
                    Label:End Action Processing ] 

            A154: End If 

        A155: Else 

            <Goto Continue Action Processing>
            A156: Goto [ 
                Type:Action Label 
                Number:1 
                Label:Continue Action Processing ] 

        A157: End If 

        <Process End Of Action>
        A158: Anchor 

        A159: Variable Set [ 
            Name:%action_first_line 
            To:%code(%current_code_type_start_line_num) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        A160: Variable Set [ 
            Name:%action_all_lines 
            To:%code(%current_code_type_start_line_num:%line_num) 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <If Action Does Not Contain Parameters>
        A161: If [ %action_first_line !~R %regex_action_line_with_parameters ]

            <Goto End Action Processing>
            A162: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A163: End If 

        A164: Variable Set [ 
            Name:%action_name 
            To:%action_first_line 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <Extract Action Name From First Line Of Action>
        A165: Variable Search Replace [ 
            Variable:%action_name 
            Search:%regex_action_line_with_parameters 
            Ignore Case:Off 
            Multi-Line:Off 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:$1 ] 

        <Set "Else" To action_name If It Is Set To "Else If">
        A166: Variable Set [ 
            Name:%action_name 
            To:Else 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] If [ %action_name eq Else If ]

        <Check if action name exists in action names string array is necessary since otherwise if an invalid action name is passed to get action code function, then a popup/warning is generated in tasker>
        A167: Anchor 

        <Get Action Index From Action Names String Array>
        A168: Java Function [ Return:%action_index Class Or Object:net.dinglisch.android.taskerm.gm Function:b
            {int} (String, String[]) Param:%action_name Param:action_names_string_array Param: Param: Param: Param: Param: Continue Task After Error:On ] 

        <If Action Code Is Not Valid>
        A169: If [ %action_index !~R %regex_valid_number ]

            A170: Flash [ 
                Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Action Index "%action_index" In Action Names List 
                Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
            A171: Variable Set [ 
                Name:%skipping_split_action_parameters_on_multiple_lines 
                To:1 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

            <Goto End Action Processing>
            A172: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A173: End If 

        <Get Action Code From Action Name>
        A174: Java Function [ Return:%action_code Class Or Object:net.dinglisch.android.taskerm.n Function:b
            {int} (String) Param:%action_name Param: Param: Param: Param: Param: Param: Continue Task After Error:On ] 

        <If Action Code Is Not Valid>
        A175: If [ %action_code !~R %regex_valid_number | %action_code < 1 ]

            A176: Flash [ 
                Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Action Code "%action_code" 
                Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
            A177: Variable Set [ 
                Name:%skipping_split_action_parameters_on_multiple_lines 
                To:1 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

            <Goto End Action Processing>
            A178: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A179: End If 

        <Find Arguments Size Of Action>
        A180: Anchor 

        A181: Java Function [ Return:%arguments_list_size Class Or Object:net.dinglisch.android.taskerm.n Function:n
            {int} (int) Param:%action_code Param:%action_code Param:0 Param: Param: Param: Param: Continue Task After Error:On ] 

        <If Arguments Size Of Action Is Invalid Or Less Than 1>
        A182: If [ %arguments_list_size !~R %regex_valid_number | %arguments_list_size < 1 ]

            A183: Flash [ 
                Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Arguments List Size "%arguments_list_size" 
                Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Goto End Action Processing>
            A184: Goto [ 
                Type:Action Label 
                Number:1 
                Label:End Action Processing ] 

        A185: End If 

        A186: Variable Set [ 
            Name:%arguments_list_size 
            To:%arguments_list_size - 1 
            Recurse Variables:Off 
            Do Maths:On 
            Append:Off 
            Max Rounding Digits:3 ] 

        A187: Array Clear [ 
            Variable Array:%argument_names_list ] 

        A188: For [ 
            Variable:%num 
            Items:0:%arguments_list_size ] 

            A189: Variable Set [ 
                Name:%argument_number 
                To:%num 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

            A190: Java Function [ Return:%argument_name Class Or Object:net.dinglisch.android.taskerm.n Function:a
                {String} (Resources, int, int) Param:resources Param:%action_code Param:%argument_number Param: Param: Param: Param: ] 

            A191: Variable Set [ 
                Name:%regex_argument_name_repeated 
                To:.*%argument_name:.*%argument_name:.* 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

            <If Arguments Name Is Repeated In Action Description, Then Not Safe To Split Action On Multiple Lines>
            A192: If [ %action_all_lines ~R %regex_argument_name_repeated ]

                A193: Flash [ 
                    Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Argument Name "%argument_name" Repetition 
                    Long:Off ] If [ %enable_flash_actions eq 1 ]

                <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
                A194: Variable Set [ 
                    Name:%skipping_split_action_parameters_on_multiple_lines 
                    To:1 
                    Recurse Variables:Off 
                    Do Maths:Off 
                    Append:Off 
                    Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

                <Goto End Action Processing>
                A195: Goto [ 
                    Type:Action Label 
                    Number:1 
                    Label:End Action Processing ] 

            A196: End If 

            A197: Variable Set [ 
                Name:%position 
                To:%argument_names_list(#) + 1 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

            A198: Array Push [ 
                Variable Array:%argument_names_list 
                Position:%position 
                Value:%argument_name 
                Fill Spaces:Off ] 

        A199: End For 

        <For Loop On All Argument Names In argument_names_list>
        A200: For [ 
            Variable:%num 
            Items:1:%argument_names_list(#) ] 

            A201: Variable Set [ 
                Name:%argument_name 
                To:%argument_names_list(%num) 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

            A202: Variable Set [ 
                Name:%regex_argument_name_exists 
                To:(.*)(%argument_name:.*) 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:Off 
                Max Rounding Digits:3 ] 

            <For Loop From current_code_type_start_line_num to line_num>
            A203: For [ 
                Variable:%num1 
                Items:%current_code_type_start_line_num:%line_num ] 

                <If Action Line Contains The Argument Name>
                A204: If [ %code(%num1) ~R %regex_argument_name_exists ]

                    <Add "%newline%indent_string%single_indent_string" Before argument_name>
                    A205: Variable Search Replace [ 
                        Variable:%code(%num1) 
                        Search:%regex_argument_name_exists 
                        Ignore Case:Off 
                        Multi-Line:Off 
                        One Match Only:Off 
                        Store Matches In Array: 
                        Replace Matches:On 
                        Replace With:$1%newline%indent_string%single_indent_string$2 ] 

                    <Goto Start Of For Loop On All Argument Names In argument_names_list>
                    A206: Goto [ 
                        Type:Action Label 
                        Number:1 
                        Label:For Loop On All Argument Names In argument_names_list ] 

                A207: End If 

            A208: End For 

        A209: End For 

        <End Action Processing>
        A210: Anchor 

        <If skipping_split_action_parameters_on_multiple_lines Equals "1">
        A211: If [ %skipping_split_action_parameters_on_multiple_lines eq 1 ]

            A212: Variable Set [ 
                Name:%current_code_type_start_line_num_plus_1 
                To:%current_code_type_start_line_num + 1 
                Recurse Variables:Off 
                Do Maths:On 
                Append:Off 
                Max Rounding Digits:3 ] 

            <For Loop From current_code_type_start_line_num_plus_1+1 to line_num>
            A213: For [ 
                Variable:%num 
                Items:%current_code_type_start_line_num_plus_1:%line_num ] If [ %current_code_type_start_line_num < %line_num ]

                <Replace Previously Set "^%indent_string" Indent With "%indent_string%single_indent_string">
                A214: Variable Search Replace [ 
                    Variable:%code(%num) 
                    Search:^%indent_string 
                    Ignore Case:Off 
                    Multi-Line:Off 
                    One Match Only:Off 
                    Store Matches In Array: 
                    Replace Matches:On 
                    Replace With:%indent_string%single_indent_string ] 

            A215: End For 

        A216: End If 

        A217: Variable Clear [ 
            Name:%current_code_type 
            Pattern Matching:Off 
            Local Variables Only:Off 
            Clear All Variables:Off ] 

        <Append Newline To Line>
        A218: Variable Set [ 
            Name:%code(%line_num) 
            To:%newline 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:On 
            Max Rounding Digits:3 ] 

        <Continue Action Processing>
        A219: Anchor 

    A220: End If 

    A221: Variable Set [ 
        Name:%current_code_type_line_count 
        To:%current_code_type_line_count + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Next Line>
    A222: Anchor 

    A223: Variable Set [ 
        Name:%line_num 
        To:%line_num + 1 
        Recurse Variables:Off 
        Do Maths:On 
        Append:Off 
        Max Rounding Digits:3 ] 

    <Goto Start Of Process Code Loop>
    A224: Goto [ 
        Type:Action Label 
        Number:1 
        Label:Start Of Process Code Loop ] If [ %line_num < %lines_count + 1 ]

    <End Of Process Code Loop>
    A225: Anchor 

    <Join Code Array On Newline>
    A226: Variable Join [ 
        Name:%code 
        Joiner:%newline 
        Delete Parts:Off ] 

    <If cap_indents_at_max_indent_character_count Equals "1">
    A227: If [ %cap_indents_at_max_indent_character_count eq 1 ]

        A228: Variable Clear [ 
            Name:%indent_string 
            Pattern Matching:Off 
            Local Variables Only:Off 
            Clear All Variables:Off ] 

        <Generate indent_string Based On max_indent_character_count>
        A229: For [ 
            Variable:%num 
            Items:1:%max_indent_character_count ] 

            A230: Variable Set [ 
                Name:%indent_string 
                To:%indent_character 
                Recurse Variables:Off 
                Do Maths:Off 
                Append:On 
                Max Rounding Digits:3 ] 

        A231: End For 

        <Replace Indents Greater Than max_indent_character_count With "%indent_string">
        A232: Variable Search Replace [ 
            Variable:%code 
            Search:%regex_set_max_indent 
            Ignore Case:Off 
            Multi-Line:On 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With:%indent_string ] 

    A233: End If 

    <If convert_code_to_markdown_code_block Equals "1">
    A234: If [ %convert_code_to_markdown_code_block eq 1 ]

        A235: Variable Set [ 
            Name:%code_for_shell 
            To:%code 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <replace all single quotes (') with nothing>
        A236: Variable Search Replace [ 
            Variable:%code_for_shell 
            Search:' 
            Ignore Case:Off 
            Multi-Line:On 
            One Match Only:Off 
            Store Matches In Array: 
            Replace Matches:On 
            Replace With: ] If [ %code Set ]

        <Find Backticks To Print>
        A237: Run Shell [ 
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
        echo "$backticks_to_print" Timeout (Seconds):0 
            Use Root:Off 
            Store Output In:%backticks_to_print 
            Store Errors In:%errors 
            Store Result In: Continue Task After Error:On ] 

        A238: Variable Set [ 
            Name:%exit_code 
            To:%err 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

        <If Failed>
        A239: If [ %exit_code neq \%err | %errors Set ]

            A240: Flash [ 
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

            A241: Stop [ 
                With Error:Off 
                Task: ] 

        A242: End If 

        <Convert Code To Markdown Code Block>
        A243: Variable Set [ 
            Name:%code 
            To:%backticks_to_print
        %code
        %backticks_to_print 
            Recurse Variables:Off 
            Do Maths:Off 
            Append:Off 
            Max Rounding Digits:3 ] 

    A244: End If 

    A245: Flash [ 
        Text:Format Complete 
        Long:Off ] 

    <If set_clipboard_to_formatted_code Equals "1">
    A246: If [ %set_clipboard_to_formatted_code eq 1 ]

        <Set code To Clipboard Text>
        A247: Set Clipboard [ 
            Text:%code 
            Add:Off ] 

    A248: End If 

    <Return>
    A249: Anchor 

    A250: Return [ Value:%code Stop:On ] 
````