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
    Otherwise it will not be set.>
    A1: Anchor 

    A2: Variable Set [ Name:%task_name To:Format Task Description For Markdown Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Set Newline Character>
    A3: Variable Set [ Name:%newline To:
         Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Parse And Validate Parameters>
    A4: Anchor 

    A5: [X] Variable Set [ Name:%par1 To:space
        4
        12
        4
        0
        1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If %par1 Not Received>
    A6: If [ %par1 eq \%par1 ]

        <Set User Modifiable Variables Start>
        A7: Anchor 

        <Set indent_character_type
        Default: "space">
        A8: Variable Set [ Name:%indent_character_type To:space Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set min_indent_character_count
        Default: "4">
        A9: Variable Set [ Name:%min_indent_character_count To:4 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set max_indent_character_count
        Default: "12">
        A10: Variable Set [ Name:%max_indent_character_count To:12 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set single_indent_character_count
        Default: "4">
        A11: Variable Set [ Name:%single_indent_character_count To:4 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set cap_indents_at_max_indent_character_count
        Default: "0">
        A12: Variable Set [ Name:%cap_indents_at_max_indent_character_count To:0 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set convert_code_to_markdown_code_block
        Default: "1">
        A13: Variable Set [ Name:%convert_code_to_markdown_code_block To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set set_clipboard_to_formatted_code
        Default: "1">
        A14: Variable Set [ Name:%set_clipboard_to_formatted_code To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set User Modifiable Variables End>
        A15: Anchor 

    A16: Else 

        A17: Variable Set [ Name:%format_task_description_for_markdown_parameter_1 To:%par1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A18: Variable Split [ Name:%format_task_description_for_markdown_parameter_1 Splitter:%newline Delete Base:Off ] 

        <Set indent_character_type>
        A19: Variable Set [ Name:%indent_character_type To:%format_task_description_for_markdown_parameter_1(1) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set min_indent_character_count>
        A20: Variable Set [ Name:%min_indent_character_count To:%format_task_description_for_markdown_parameter_1(2) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set max_indent_character_count>
        A21: Variable Set [ Name:%max_indent_character_count To:%format_task_description_for_markdown_parameter_1(3) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set single_indent_character_count>
        A22: Variable Set [ Name:%single_indent_character_count To:%format_task_description_for_markdown_parameter_1(4) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set cap_indents_at_max_indent_character_count>
        A23: Variable Set [ Name:%cap_indents_at_max_indent_character_count To:%format_task_description_for_markdown_parameter_1(5) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set convert_code_to_markdown_code_block>
        A24: Variable Set [ Name:%convert_code_to_markdown_code_block To:%format_task_description_for_markdown_parameter_1(6) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set set_clipboard_to_formatted_code>
        A25: Variable Set [ Name:%set_clipboard_to_formatted_code To:%format_task_description_for_markdown_parameter_1(7) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A26: End If 

    <If %par2 Not Received>
    A27: If [ %par2 eq \%par2 ]

        <Set Clipboard Text To code>
        A28: Variable Set [ Name:%code To:%CLIP Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A29: Else 

        <Set %par2 To code>
        A30: Variable Set [ Name:%code To:%par2 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A31: End If 

    <Set Tab Character>
    A32: Variable Set [ Name:%tab To:    Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Set Space Character>
    A33: Variable Set [ Name:%space To:  Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If indent_character_type Is Set To "space">
    A34: If [ %indent_character_type eq space ]

        <Set "%space" to indent_character>
        A35: Variable Set [ Name:%indent_character To:%space Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If indent_character_type Is Set To "tab">
    A36: Else If [ %indent_character_type eq tab ]

        <Set "%tab" to indent_character>
        A37: Variable Set [ Name:%indent_character To:%tab Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A38: End If 

    <Set Default Indent Character Count>
    A39: Variable Set [ Name:%indent_character_count To:%min_indent_character_count Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A40: Variable Set [ Name:%regex_single_indent_prefix To:^[%indent_character]{%single_indent_character_count} Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A41: Variable Set [ Name:%regex_set_max_indent To:^[%indent_character]{%max_indent_character_count,} Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A42: Variable Set [ Name:%regex_valid_number To:^[0-9]+$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A43: Variable Set [ Name:%regex_valid_bool_value To:^[0-1]$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A44: Variable Set [ Name:%regex_action_line_start To:^[\s]+A[0-9]+: . Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A45: Variable Set [ Name:%regex_action_line_end To: \](%space)?$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A46: Variable Set [ Name:%regex_comment_line_start To:^[\s]+\< Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A47: Variable Set [ Name:%regex_comment_line_end To:\>$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A48: Test Variable [ Type:Length Data:%indent_character Store Result In:%indent_character_length Continue Task After Error:On ] 

    A49: If [ %indent_character neq %space &+ %indent_character neq %tab | %indent_character_length neq 1 | %min_indent_character_count !~R %regex_valid_number | %cap_indents_at_max_indent_character_count !~R %regex_valid_bool_value | %cap_indents_at_max_indent_character_count eq 1 & %max_indent_character_count !~R %regex_valid_number |+ %max_indent_character_count < %min_indent_character_count | %single_indent_character_count !~R %regex_valid_number | %single_indent_character_count > %min_indent_character_count | %convert_code_to_markdown_code_block !~R %regex_valid_bool_value | %set_clipboard_to_formatted_code !~R %regex_valid_bool_value ]

        A50: Flash [ Text:Invalid Parameters To %task_name
                %task_name Failed
                
                indent_character_type = "%indent_character_type"
                
                min_indent_character_count = "%min_indent_character_count"
                
                max_indent_character_count = "%max_indent_character_count"
                
                single_indent_character_count = "%single_indent_character_count"
                
                cap_indents_at_max_indent_character_count = "%cap_indents_at_max_indent_character_count"
                
                convert_code_to_markdown_code_block = "%convert_code_to_markdown_code_block"
                
                set_clipboard_to_formatted_code = "%set_clipboard_to_formatted_code" Long:On ] 

        A51: Stop [ With Error:Off Task: ] 

    A52: End If 

    <Task Start>
    A53: Anchor 

    <Split Code On Newline To Create Code Array>
    A54: Variable Split [ Name:%code Splitter:%newline Delete Base:Off ] 

    <Check If First Line Consists Of Task Name And Code>
    A55: If [ %code(1) !~R ^[\s]*(.+) \([0-9]+\)$ ]

        A56: Flash [ Text:Error! Task Name And Code Not Found In Line 1 Of Task Description Being Used
                %task_name Failed
                
                Line 1 = "%code(1)" Long:On ] 

        A57: Stop [ With Error:Off Task: ] 

    A58: End If 

    A59: Variable Set [ Name:%description_task_name To:%code(1) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Get Description Task Name From First Line>
    A60: Variable Search Replace [ Variable:%description_task_name Search:^[\s]*(.+) \([0-9]+\)$ Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:$1 ] 

    A61: Flash [ Text:Formatting "%description_task_name" Task Description For Markdown Long:Off ] 

    <Set Line 1 To "Task Name: %description_task_name">
    A62: Variable Set [ Name:%code(1) To:Task Name: %description_task_name Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If Second Line Equals "Abort New Task", "Abort Existing Task" Or "Run Both Together">
    A63: If [ %code(2) ~R ^[\s]+(Abort New Task)|(Abort Existing Task)|(Run Both Together)$ ]

        <Remove Pre-existing "^[\s]{4}(%tab)?" Indent>
        A64: Variable Search Replace [ Variable:%code(2) Search:^[\s]{4}(%tab)? Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With: ] 

        <Set Line 1 To "Collision Handling: %code(2)">
        A65: Variable Set [ Name:%code(2) To:Collision Handling: %code(2) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A66: Variable Set [ Name:%code_start_line_num To:3 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A67: Else 

        A68: Variable Set [ Name:%code_start_line_num To:2 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A69: End If 

    A70: Variable Set [ Name:%actions_label To:
        Actions: Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Push actions_label At code_start_line_num>
    A71: Array Push [ Variable Array:%code Position:%code_start_line_num Value:%actions_label Fill Spaces:Off ] 

    A72: Variable Set [ Name:%code_start_line_num To:%code_start_line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A73: Variable Set [ Name:%lines_count To:%code(#) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Remove Last Line If Only Whitespaces>
    A74: Array Pop [ Variable Array:%code Position:%lines_count To Var: ] If [ %code(%lines_count) ~R ^[\s]+$ ]

    A75: Variable Set [ Name:%lines_count To:%code(#) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A76: Variable Set [ Name:%line_num To:%code_start_line_num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A77: Variable Clear [ Name:%current_code_type Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

    A78: Variable Set [ Name:%current_code_type_line_count To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A79: Variable Set [ Name:%current_code_type_start_line_num To:%line_num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Start Of Process Code Loop>
    A80: Anchor 

    A81: [X] Flash [ Text:%code(%line_num) Long:Off ] 

    A82: Variable Set [ Name:%next_line_num To:%line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A83: Variable Set [ Name:%current_line To:%code(%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A84: Variable Set [ Name:%next_line To:%code(%next_line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If Not Processing Any Code Type>
    A85: If [ %current_code_type eq \%current_code_type ]

        <If Current Line Starts A Comment>
        A86: If [ %current_line ~R %regex_comment_line_start ]

            <Set "comment" To current_code_type>
            A87: Variable Set [ Name:%current_code_type To:comment Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Current Line Starts An Action>
        A88: Else If [ %current_line ~R %regex_action_line_start ]

            <Set "action" To current_code_type>
            A89: Variable Set [ Name:%current_code_type To:action Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Current Line Is Empty>
        A90: Else If [ %current_line eq \%code%line_num ]

            <Goto Next Line>
            A91: Goto [ Type:Action Label Number:1 Label:Next Line ] 

        <Else Unknown current_code_type>
        A92: Else 

            A93: Flash [ Text:Error! Unknown Code Type At Line %line_num "%current_line" While Processing "%description_task_name" Description Long:On ] 

            A94: Stop [ With Error:Off Task: ] 

        A95: End If 

        <Set "1" to current_code_type_line_count>
        A96: Variable Set [ Name:%current_code_type_line_count To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set line_num to current_code_type_start_line_num>
        A97: Variable Set [ Name:%current_code_type_start_line_num To:%line_num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A98: End If 

    <If First Line Of Action>
    A99: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "Else If", "Else" "End If" Or "End For">
        A100: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

            <Decrement indent_character_count by single_indent_character_count>
            A101: Variable Set [ Name:%indent_character_count To:%indent_character_count - %single_indent_character_count Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

        A102: End If 

    A103: End If 

    A104: Variable Clear [ Name:%indent_string Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

    <Generate indent_string Based On Current indent_character_count>
    A105: For [ Variable:%num Items:1:%indent_character_count ] 

        A106: Variable Set [ Name:%indent_string To:%indent_character Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

    A107: End For 

    <If First Line Of Action>
    A108: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "If", "Else If", "Else" Or "For">
        A109: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((If)|(Else If)|(Else)|(For)).* ]

            <Increment indent_character_count by single_indent_character_count>
            A110: Variable Set [ Name:%indent_character_count To:%indent_character_count + %single_indent_character_count Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

        A111: End If 

    A112: End If 

    <If Processing Comment>
    A113: If [ %current_code_type eq comment ]

        <Replace Pre-existing "^[\s]{4}(%tab)?" Indent With "%indent_string">
        A114: Variable Search Replace [ Variable:%code(%line_num) Search:^[\s]{4}(%tab)? Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string ] 

        <If Comment Ended>
        A115: If [ %current_line ~R %regex_comment_line_end & %next_line ~R %regex_action_line_start ]

            A116: Variable Clear [ Name:%current_code_type Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

            <If Next Action Is "Else If", "Else" "End If" Or "End For">
            A117: If [ %next_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

                <For Loop From current_code_type_start_line_num to line_num>
                A118: For [ Variable:%num Items:%current_code_type_start_line_num:%line_num ] 

                    <Remove Single Indent Prefix>
                    A119: Variable Search Replace [ Variable:%code(%num) Search:%regex_single_indent_prefix Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With: ] 

                A120: End For 

            A121: End If 

        A122: End If 

    <Else If Processing Action>
    A123: Else If [ %current_code_type eq action ]

        <If First Line Of Action>
        A124: If [ %current_code_type_line_count eq 1 ]

            <Replace Pre-existing "^[\s]{4}%tab" Indent With "%indent_string">
            A125: Variable Search Replace [ Variable:%code(%line_num) Search:^[\s]{4}%tab Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string ] 

        <If Action Continues On More Than 1 Line>
        A126: Else 

            <Replace Pre-existing "^[\s]{4}" Indent With "%indent_string%indent_string">
            A127: Variable Search Replace [ Variable:%code(%line_num) Search:^[\s]{4} Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string%indent_string ] 

        A128: End If 

        <If Action Ended>
        A129: If [ %current_code_type_line_count eq 1 &+ %current_line !~ *[* | %current_line ~R %regex_action_line_end & %next_line ~R %regex_action_line_start |+ %next_line ~R %regex_comment_line_start ]

            A130: Variable Clear [ Name:%current_code_type Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

            <Append Newline To Line>
            A131: Variable Set [ Name:%code(%line_num) To:%newline Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

        A132: End If 

    A133: End If 

    A134: Variable Set [ Name:%current_code_type_line_count To:%current_code_type_line_count + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    <Next Line>
    A135: Anchor 

    A136: Variable Set [ Name:%line_num To:%line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    <Goto Start Of Process Code Loop>
    A137: Goto [ Type:Action Label Number:1 Label:Start Of Process Code Loop ] If [ %line_num < %lines_count + 1 ]

    <End Of Process Code Loop>
    A138: Anchor 

    <Join Code Array On Newline>
    A139: Variable Join [ Name:%code Joiner:%newline Delete Parts:Off ] 

    <If cap_indents_at_max_indent_character_count Equals "1">
    A140: If [ %cap_indents_at_max_indent_character_count eq 1 ]

        A141: Variable Clear [ Name:%indent_string Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

        <Generate indent_string Based On max_indent_character_count>
        A142: For [ Variable:%num Items:1:%max_indent_character_count ] 

            A143: Variable Set [ Name:%indent_string To:%indent_character Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

        A144: End For 

        <Replace Indents Greater Than max_indent_character_count With "%indent_string">
        A145: Variable Search Replace [ Variable:%code Search:%regex_set_max_indent Ignore Case:Off Multi-Line:On One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string ] 

    A146: End If 

    <If convert_code_to_markdown_code_block Equals "1">
    A147: If [ %convert_code_to_markdown_code_block eq 1 ]

        A148: Variable Set [ Name:%code_for_shell To:%code Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <replace all single quotes (') with nothing>
        A149: Variable Search Replace [ Variable:%code_for_shell Search:' Ignore Case:Off Multi-Line:On One Match Only:Off Store Matches In Array: Replace Matches:On Replace With: ] If [ %code Set ]

        <Find Backticks To Print>
        A150: Run Shell [ Command:code='%code_for_shell'
                
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
                echo "$backticks_to_print" Timeout (Seconds):0 Use Root:Off Store Output In:%backticks_to_print Store Errors In:%errors Store Result In: Continue Task After Error:On ] 

        A151: Variable Set [ Name:%exit_code To:%err Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Failed>
        A152: If [ %exit_code neq \%err | %errors Set ]

            A153: Flash [ Text:Failed To Find Backticks To Print To Convert "%description_task_name" Task Description To Markdown Code Block
                        %task_name Failed
                        
                        exit_code = "%exit_code"
                        
                        errors =
                        "
                        %errors
                        "
                        
                        output =
                        "
                        %backticks_to_print
                        " Long:On ] 

            A154: Stop [ With Error:Off Task: ] 

        A155: End If 

        <Convert Code To Markdown Code Block>
        A156: Variable Set [ Name:%code To:%backticks_to_print
                %code
                %backticks_to_print Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A157: End If 

    A158: Flash [ Text:Format Complete Long:Off ] 

    <If set_clipboard_to_formatted_code Equals "1">
    A159: If [ %set_clipboard_to_formatted_code eq 1 ]

        <Set code To Clipboard Text>
        A160: Set Clipboard [ Text:%code Add:Off ] 

    A161: End If 

    <Return>
    A162: Anchor 

    A163: Return [ Value:%code Stop:On ] 
````