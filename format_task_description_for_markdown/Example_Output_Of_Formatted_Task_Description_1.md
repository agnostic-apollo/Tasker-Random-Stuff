
````
Task Name: Format Task Description For Markdown

Actions:
    <A helper task to format an exported profile or tasker task description/code into a more readable and markdown compatible format for websites like reddit and github.
    
    For basic usage, just run this task after running "Export" -> "Description To Clipboard" on a task and it will read the description from the %CLIP variable and after formatting it, it will put the formatted description back into the clipboard as a markdown code block with space indents.
    
    
    If %par1 is not passed, then default values are automatically used.
    
    If it is passed then it's parameters must be set to the following:
    
    indent_character_type is the type of character that should be used for indents. Valid values are "space" and "tab". Default value is "space".
    
    min_indent_character_count is the minimum indent that should be present for actions and comments. It must be a valid integer. Default value is "4".
    
    max_indent_character_count is the maximum indent that should be present for actions and comments depending "If" and "For" related actions. It must be a valid integer and is only considered if cap_indents_at_max_indent_character_count is set to "1" and it must not be less than min_indent_character_count. Default value is "12".
    
    single_indent_character_count is a number of characters of indent_character_type that must be considered as one indent. It can be same as min_indent_character_count. It must be a valid integer and must not be greater than min_indent_character_count. Default value is "4".
    
    split_action_parameters_on_multiple_lines is a toggle that decides if parameters of actions in description are split over multiple lines or not. If this is enabled, then each parameter will be on a different line making it easier to read. It should work for most actions but will not work for actions whose action name is modified depending on its configuration other than the "Else" action whose name is modified to "Else If" if there is a condition added to it. It will also not for plugins and actions whose parameter names are repeated in the description in any way. This uses EXPERIMENTAL CODE including tasker internal java functions which may stop working after an update to tasker, in that case, wait for the dev to update this task to be compatible with latest tasker version. Use at your own risk. Disable it if it is not working properly or you are receiving exceptions. Enabling this will also slow down the task even more than normal because of all the extra processing. It must be set to "0" or "1". Default value is "1".
    
    cap_indents_at_max_indent_character_count is a toggle that decides if there should be limit on max indents based on max_indent_character_count. This is helpful if too many nested conditions exist in the task increasing the indents to a point that it makes it harder to read without using horizontal scrolling. It must be set to "0" or "1". Default value is "0".
    
    convert_code_to_markdown_code_block is a toggle that decides whether the formatted code should automatically be converted to markdown code block by prefixing and suffixing the code with a minimum of 3 backticks. This is helpful because a lot of users are not aware that code blocks exist and they just paste the description without it in posts and comments destroying all order making it impossibly hard to be read and understood by others. It also makes it slightly faster to post the description since it's automatically prefixed and suffixed with backticks by default. Moreover, the task automatically checks if the code itself contains any backticks and then uses (max numbers of consecutive backticks found + 3) backticks for prefixing and suffixing so that any backticks in the code can be escaped and the entire code is enclosed in the code block. It must be set to "0" or "1". Default value is "1".
    
    set_clipboard_to_formatted_code is a toggle that decides if the formatted code is put back in the clipboard using the "Set Clipboard" action at the end. It must be set to "0" or "1". Default value is "1".
    
    
    If %par2 is not passed, then data from the clipboard using the tasker variable %CLIP is used as the code.
    
    If %par2 is passed, then it is used as the code.
    
    The first line of the task description must be in the format "task_name (task_code)" or "Profile: profile_name (profile_code)". It can optionally be prefixed with whitespace characters.
    
    Depending on the number of actions, the device specs and the parameters, it will take a few seconds to a minute to format the description. Run using a launcher desktop shortcut instead of with the play button in tasker UI for faster execution.
    
    
    Control:
    "
    version_number: 0.3.0
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

    A2: Variable Set [ Name:%task_name To:Format Task Description For Markdown Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Enable this action if you want to flash log messages while running this task>
    A3: [X] Variable Set [ Name:%enable_flash_actions To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Set action codes whose action parameters should be force split even if duplicates found
    Default:
    664
    Java Function>
    A4: Variable Set [ Name:%force_split_action_parameters_on_multiple_lines_action_codes To:664 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Set Newline Character>
    A5: Variable Set [ Name:%newline To:
         Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Parse And Validate Parameters>
    A6: Anchor 

    A7: [X] Variable Set [ Name:%par1 To:space
        4
        12
        4
        1
        0
        1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If %par1 Not Received>
    A8: If [ %par1 eq \%par1 ]

        <Set User Modifiable Variables Start>
        A9: Anchor 

        <Set indent_character_type
        Default: "space">
        A10: Variable Set [ Name:%indent_character_type To:space Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set min_indent_character_count
        Default: "4">
        A11: Variable Set [ Name:%min_indent_character_count To:4 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set max_indent_character_count
        Default: "12">
        A12: Variable Set [ Name:%max_indent_character_count To:12 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set single_indent_character_count
        Default: "4">
        A13: Variable Set [ Name:%single_indent_character_count To:4 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set cap_indents_at_max_indent_character_count
        Default: "0">
        A14: Variable Set [ Name:%cap_indents_at_max_indent_character_count To:0 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set split_action_parameters_on_multiple_lines
        Default: "1">
        A15: Variable Set [ Name:%split_action_parameters_on_multiple_lines To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set convert_code_to_markdown_code_block
        Default: "1">
        A16: Variable Set [ Name:%convert_code_to_markdown_code_block To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set set_clipboard_to_formatted_code
        Default: "1">
        A17: Variable Set [ Name:%set_clipboard_to_formatted_code To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set User Modifiable Variables End>
        A18: Anchor 

    A19: Else 

        A20: Variable Set [ Name:%format_task_description_for_markdown_parameter_1 To:%par1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A21: Variable Split [ Name:%format_task_description_for_markdown_parameter_1 Splitter:%newline Delete Base:Off ] 

        <Set indent_character_type>
        A22: Variable Set [ Name:%indent_character_type To:%format_task_description_for_markdown_parameter_1(1) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set min_indent_character_count>
        A23: Variable Set [ Name:%min_indent_character_count To:%format_task_description_for_markdown_parameter_1(2) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set max_indent_character_count>
        A24: Variable Set [ Name:%max_indent_character_count To:%format_task_description_for_markdown_parameter_1(3) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set single_indent_character_count>
        A25: Variable Set [ Name:%single_indent_character_count To:%format_task_description_for_markdown_parameter_1(4) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set cap_indents_at_max_indent_character_count>
        A26: Variable Set [ Name:%cap_indents_at_max_indent_character_count To:%format_task_description_for_markdown_parameter_1(5) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set split_action_parameters_on_multiple_lines>
        A27: Variable Set [ Name:%split_action_parameters_on_multiple_lines To:%split_action_parameters_on_multiple_lines(6) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set convert_code_to_markdown_code_block>
        A28: Variable Set [ Name:%convert_code_to_markdown_code_block To:%format_task_description_for_markdown_parameter_1(7) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set set_clipboard_to_formatted_code>
        A29: Variable Set [ Name:%set_clipboard_to_formatted_code To:%format_task_description_for_markdown_parameter_1(8) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A30: End If 

    <If %par2 Not Received>
    A31: If [ %par2 eq \%par2 ]

        <Set Clipboard Text To code>
        A32: Variable Set [ Name:%code To:%CLIP Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A33: Else 

        <Set %par2 To code>
        A34: Variable Set [ Name:%code To:%par2 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A35: End If 

    <Set Tab Character>
    A36: Variable Set [ Name:%tab To:    Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Set Space Character>
    A37: Variable Set [ Name:%space To:  Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If indent_character_type Is Set To "space">
    A38: If [ %indent_character_type eq space ]

        <Set "%space" to indent_character>
        A39: Variable Set [ Name:%indent_character To:%space Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If indent_character_type Is Set To "tab">
    A40: Else If [ %indent_character_type eq tab ]

        <Set "%tab" to indent_character>
        A41: Variable Set [ Name:%indent_character To:%tab Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A42: End If 

    <Set Default Indent Character Count>
    A43: Variable Set [ Name:%indent_character_count To:%min_indent_character_count Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A44: Variable Set [ Name:%regex_single_indent_prefix To:^[%indent_character]{%single_indent_character_count} Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A45: Variable Set [ Name:%regex_set_max_indent To:^[%indent_character]{%max_indent_character_count,} Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A46: Variable Set [ Name:%regex_valid_number To:^[0-9]+$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A47: Variable Set [ Name:%regex_valid_bool_value To:^[0-1]$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A48: Variable Set [ Name:%regex_task_or_profile_name_and_code_line To:^[\s]*(.+) \([0-9]+\)$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A49: Variable Set [ Name:%regex_profile_name_and_code_line To:^[\s]*Profile: (.+) \([0-9]+\)$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A50: Variable Set [ Name:%regex_enter_task_name_and_code_line To:^[\s]*Enter: (.+) \([0-9]+\)$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A51: Variable Set [ Name:%regex_exit_task_name_and_code_line To:^[\s]*Exit: (.+) \([0-9]+\)$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A52: Variable Set [ Name:%regex_task_collision_handling_value_line To:^[\s]+(Abort New Task)|(Abort Existing Task)|(Run Both Together)$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A53: Variable Set [ Name:%regex_action_line_start To:^[\s]+A[0-9]+: . Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A54: Variable Set [ Name:%regex_action_line_end To: \](%space)?$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A55: Variable Set [ Name:%regex_action_line_with_parameters To:^[\s]+A[0-9]+: (?:\[X\] )?([^\\\[]+) \[.* Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A56: Variable Set [ Name:%regex_comment_line_start To:^[\s]+\< Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A57: Variable Set [ Name:%regex_comment_line_end To:\>$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A58: Variable Set [ Name:%regex_whitespace_only_line To:^[\s]+$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A59: Variable Set [ Name:%regex_valid_comma_separated_numbers_list To:^[0-9]+(,[0-9]+)*$ Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A60: Test Variable [ Type:Length Data:%indent_character Store Result In:%indent_character_length Continue Task After Error:On ] 

    A61: If [ %indent_character neq %space &+ %indent_character neq %tab | %indent_character_length neq 1 | %min_indent_character_count !~R %regex_valid_number | %cap_indents_at_max_indent_character_count !~R %regex_valid_bool_value | %cap_indents_at_max_indent_character_count eq 1 & %max_indent_character_count !~R %regex_valid_number |+ %max_indent_character_count < %min_indent_character_count | %single_indent_character_count !~R %regex_valid_number | %single_indent_character_count > %min_indent_character_count | %convert_code_to_markdown_code_block !~R %regex_valid_bool_value | %set_clipboard_to_formatted_code !~R %regex_valid_bool_value | %split_action_parameters_on_multiple_lines !~R %regex_valid_bool_value | %force_split_action_parameters_on_multiple_lines_action_codes !~R %regex_valid_comma_separated_numbers_list ]

        A62: Flash [ Text:Invalid Parameters To %task_name
            %task_name Failed
            
            indent_character_type = "%indent_character_type"
            
            min_indent_character_count = "%min_indent_character_count"
            
            max_indent_character_count = "%max_indent_character_count"
            
            single_indent_character_count = "%single_indent_character_count"
            
            cap_indents_at_max_indent_character_count = "%cap_indents_at_max_indent_character_count"
            
            split_action_parameters_on_multiple_lines = "%split_action_parameters_on_multiple_lines"
            
            convert_code_to_markdown_code_block = "%convert_code_to_markdown_code_block"
            
            set_clipboard_to_formatted_code = "%set_clipboard_to_formatted_code"
            
            force_split_action_parameters_on_multiple_lines_action_codes = "%force_split_action_parameters_on_multiple_lines_action_codes" Long:On ] 

        A63: Stop [ With Error:Off Task: ] 

    A64: End If 

    <Generate single_indent_string Based On Current single_indent_character_count>
    A65: For [ Variable:%num Items:1:%single_indent_character_count ] 

        A66: Variable Set [ Name:%single_indent_string To:%indent_character Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

    A67: End For 

    <If split_action_parameters_on_multiple_lines Equals "1">
    A68: If [ %split_action_parameters_on_multiple_lines eq 1 ]

        <Get Tasker Package Version Code>
        A69: Anchor 

        A70: Variable Set [ Name:%field_name To:versionCode Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A71: Variable Set [ Name:%package_name To:net.dinglisch.android.taskerm Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A72: Java Function [ Return:package_manager Class Or Object:CONTEXT Function:getPackageManager
            {PackageManager} () Param: Param: Param: Param: Param: Param: Param: ] 

        A73: Java Function [ Return:package_info Class Or Object:package_manager Function:getPackageInfo
            {PackageInfo} (String, int) Param:%package_name Param:0 Param: Param: Param: Param: Param: ] 

        A74: Java Function [ Return:%tasker_package_version_code Class Or Object:package_info.%field_name Function:assign
            {Object} () Param: Param: Param: Param: Param: Param: Param: ] 

        A75: [X] Flash [ Text:%tasker_package_version_code Long:Off ] 

        <Run format_task_description_for_markdown_set_java_class_and_method_variables_js>
        A76: Anchor 

        A77: Variable Clear [ Name:%javascript_failed Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

        A78: JavaScriptlet [ Code://Set Default Variables Start
            
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
            
            
            //Validate Tasker Package Version Code
            var tasker_package_version_code = tasker_package_version_code;
            if ( !REGEX_VALID_NUMBER.test(tasker_package_version_code) ) {
            log_error("Invalid tasker_package_version_code: '" + tasker_package_version_code + "'");
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
            
            //Set TaskerUtils Class
            var TCUJV_C_TaskerUtils = "net.dinglisch.android.taskerm.gm";
            
            
            
            //Define Tasker Config Utils Java Method Variables
            log(1, "Defining TCUJV_CE and TCUJV_CM variables");
            
            
            //TaskerActionsList Class Methods
            
            var TCUJV_CM_TaskerActionsList_GetActionNamesList = "l";
            var TCUJV_CM_TaskerActionsList_GetActionCodeByName = "b";
            var TCUJV_CM_TaskerActionsList_GetArgNameAtIndexOfActionWithCode = "a";
            var TCUJV_CM_TaskerActionsList_GetArgsSizeOfActionWithCode = "n";
            
            
            
            //TaskerUtils Class Methods
            
            var TCUJV_CM_TaskerUtils_GetIndexOfStringInArray = "b";
            
            
            
            //Convert all TCUJV variables to tasker local variables
            log(1, "Converting all TCUJV variables to tasker local variables");
            
            var tasker_config_utils_java_variables_to_set = [
            "TCUJV_C_TaskerActionsList", "TCUJV_C_TaskerUtils",
            "TCUJV_CM_TaskerActionsList_GetActionNamesList", "TCUJV_CM_TaskerActionsList_GetActionCodeByName", "TCUJV_CM_TaskerActionsList_GetArgNameAtIndexOfActionWithCode", "TCUJV_CM_TaskerActionsList_GetArgsSizeOfActionWithCode",
            "TCUJV_CM_TaskerUtils_GetIndexOfStringInArray"];
            
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
            exit_js(0); Libraries: Auto Exit:Off Timeout (Seconds):50 Continue Task After Error:On ] 

        A79: Variable Set [ Name:%javascript_failed To:exit_code = "%err"
            
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
            " Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %err Set | %errmsg Set | %js_exit_code neq 0 ]

        A80: If [ %javascript_failed Set ]

            A81: Flash [ Text:format_task_description_for_markdown_set_java_class_and_method_variables_js Failed.
                
                %javascript_failed Long:On ] 

            A82: Stop [ With Error:Off Task: ] 

        A83: Else 

            A84: [X] Flash [ Text:format_task_description_for_markdown_set_java_class_and_method_variables_js Output:
                
                js_exit_code = "%js_exit_code"
                
                js_output =
                "
                %js_output
                "
                
                js_errors =
                "
                %js_errors
                " Long:On ] 

        A85: End If 

        <Get All Action Names And Convert To Array>
        A86: Anchor 

        A87: Java Function [ Return:resources Class Or Object:CONTEXT Function:getResources
            {Resources} () Param: Param: Param: Param: Param: Param: Param: ] 

        A88: Java Function [ Return:action_names_list Class Or Object:%tcujv_c_taskeractionslist Function:%tcujv_cm_taskeractionslist_getactionnameslist
            {List} () Param: Param: Param: Param: Param: Param: Param: ] 

        A89: Java Function [ Return: Class Or Object:Objects Function:requireNonNull
            {Object} (Object) Param:action_names_list Param: Param: Param: Param: Param: Param: Continue Task After Error:On ] 

        <If exception not raised>
        A90: If [ %err eq \%err ]

            A91: Variable Set [ Name:%is_action_names_list_null To:false Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Else if exception raised>
        A92: Else 

            A93: Variable Set [ Name:%is_action_names_list_null To:true Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A94: End If 

        A95: Java Function [ Return:%action_names_list_size Class Or Object:action_names_list Function:size
            {int} () Param: Param: Param: Param: Param: Param: Param: ] If [ %is_action_names_list_null eq false ]

        A96: If [ %action_names_list_size eq 0 | %is_action_names_list_null eq true ]

            A97: Flash [ Text:Error! Failed To Get List Of All Action Names In Tasker
                %task_name Failed Long:On ] 

            A98: Stop [ With Error:Off Task: ] 

        A99: End If 

        A100: Java Function [ Return:new_string_array Class Or Object:String[] Function:new
            {String[]} (int) Param:%action_names_list_size Param: Param: Param: Param: Param: Param: ] 

        A101: Java Function [ Return:action_names_string_array Class Or Object:action_names_list Function:toArray
            {Object[]} (Object[]) Param:new_string_array Param: Param: Param: Param: Param: Param: ] 

    A102: End If 

    <Split Code On Newline To Create Code Array>
    A103: Variable Split [ Name:%code Splitter:%newline Delete Base:Off ] 

    A104: Variable Set [ Name:%line_num To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A105: Variable Set [ Name:%current_line To:%code(%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A106: Variable Set [ Name:%next_line_num To:%line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A107: Variable Set [ Name:%next_line To:%code(%next_line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If First Line Doesn't Contain Task Or Profile Name And Code>
    A108: If [ %current_line !~R %regex_task_or_profile_name_and_code_line ]

        A109: Flash [ Text:Error! Task Or Profile Name And Code Not Found In Line %line_num Of Description Being Used
            %task_name Failed
            
            Line %line_num = "%current_line" Long:On ] 

        A110: Stop [ With Error:Off Task: ] 

    A111: End If 

    A112: Variable Set [ Name:%lines_count To:%code(#) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Remove Last Line If Only Whitespaces>
    A113: Array Pop [ Variable Array:%code Position:%lines_count To Var: ] If [ %code(%lines_count) ~R %regex_whitespace_only_line ]

    A114: Variable Set [ Name:%lines_count To:%code(#) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If First Line Doesn't Contain Profile Name And Code Or If Second Line Equals A Collision Handling Value Or First Action Or Comment Start Line (Last 3 checks exist to prevent false negatives where task name starts with "Profile: ">
    A115: If [ %current_line !~R %regex_profile_name_and_code_line | %next_line ~R %regex_task_collision_handling_value_line | %next_line ~R ^[\s]+A1: . | %next_line ~R %regex_comment_line_start ]

        <Set "0" to is_profile_description>
        A116: Variable Set [ Name:%is_profile_description To:0 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Goto Process Task Description Start>
        A117: Goto [ Type:Action Label Number:1 Label:Process Task Description Start ] 

    A118: End If 

    <Process Profile Description Start>
    A119: Anchor 

    A120: Variable Set [ Name:%description_name To:%current_line Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Get Profile Description Name From First Line>
    A121: Variable Search Replace [ Variable:%description_name Search:%regex_profile_name_and_code_line Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:$1 ] 

    <Set First Line To "Profile Name: %description_name">
    A122: Variable Set [ Name:%code(%line_num) To:Profile Name: %description_name Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A123: Flash [ Text:Formatting "%description_name" Profile Description For Markdown Long:Off ] 

    <Set "1" to is_profile_description>
    A124: Variable Set [ Name:%is_profile_description To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Process Profile Code Loop Start>
    A125: Anchor 

    <Next Profile Line>
    A126: Anchor 

    A127: Variable Set [ Name:%line_num To:%line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A128: Variable Set [ Name:%current_line To:%code(%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Goto Process Profile Code Loop Start If Next Line Does Not Match Entry Or Exit Task First Line>
    A129: Goto [ Type:Action Label Number:1 Label:Process Profile Code Loop Start ] If [ %line_num < %lines_count + 1 & %current_line !~R %regex_enter_task_name_and_code_line & %current_line !~R %regex_exit_task_name_and_code_line ]

    <Goto Process Task Code Loop End>
    A130: Goto [ Type:Action Label Number:1 Label:Process Task Code Loop End ] If [ %line_num > %lines_count ]

    <Process Profile Code Loop End>
    A131: Anchor 

    <Process Task Description Start>
    A132: Anchor 

    <Set Default Indent Character Count>
    A133: Variable Set [ Name:%indent_character_count To:%min_indent_character_count Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A134: Variable Set [ Name:%current_line To:%code(%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A135: Variable Set [ Name:%description_name To:%current_line Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If is_profile_description Equals "1">
    A136: If [ %is_profile_description eq 1 ]

        <If Current Line Starts An Entry Task>
        A137: If [ %current_line ~R %regex_enter_task_name_and_code_line ]

            <Get Entry Task Description Name From First Line>
            A138: Variable Search Replace [ Variable:%description_name Search:%regex_enter_task_name_and_code_line Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:$1 ] 

            <Set First Line To "%newline%newline%newline">
            A139: Variable Set [ Name:%code(%line_num) To:%newline%newline%newline Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

            <Append "Entry Task Name: %description_name" To First Line>
            A140: Variable Set [ Name:%code(%line_num) To:Entry Task Name: %description_name Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

            <Set "1" to is_entry_task_description>
            A141: Variable Set [ Name:%is_entry_task_description To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Current Line Starts An Exit Task>
        A142: Else If [ %current_line ~R %regex_exit_task_name_and_code_line ]

            <Get Exit Task Description Name From First Line>
            A143: Variable Search Replace [ Variable:%description_name Search:%regex_exit_task_name_and_code_line Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:$1 ] 

            <Set First Line To "%newline" If is_entry_task_description Equals "1">
            A144: Variable Set [ Name:%code(%line_num) To:%newline Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %is_entry_task_description eq 1 ]

            <Set First Line To "%newline%newline%newline" If is_entry_task_description Does Not Equal "1">
            A145: Variable Set [ Name:%code(%line_num) To:%newline%newline%newline Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %is_entry_task_description neq 1 ]

            <Append "Exit Task Name: %description_name" To First Line>
            A146: Variable Set [ Name:%code(%line_num) To:Exit Task Name: %description_name Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

            <Set "1" to is_exit_task_description>
            A147: Variable Set [ Name:%is_exit_task_description To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A148: End If 

    A149: Else 

        <Get Task Description Name From First Line>
        A150: Variable Search Replace [ Variable:%description_name Search:%regex_task_or_profile_name_and_code_line Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:$1 ] 

        <Set First Line To "Task Name: %description_name">
        A151: Variable Set [ Name:%code(%line_num) To:Task Name: %description_name Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A152: Flash [ Text:Formatting "%description_name" Task Description For Markdown Long:Off ] 

    A153: End If 

    A154: Variable Set [ Name:%line_num To:%line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A155: Variable Set [ Name:%current_line To:%code(%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If Second Line Of Task Description Equals A Collision Handling Value>
    A156: If [ %current_line ~R %regex_task_collision_handling_value_line ]

        <Remove Pre-existing "^[\s]{4}(%tab)?" Indent>
        A157: Variable Search Replace [ Variable:%code(%line_num) Search:^[\s]{4}(%tab)? Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With: ] 

        <Set Second Line To "Collision Handling: collision_handling_value">
        A158: Variable Set [ Name:%code(%line_num) To:Collision Handling: %code(%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A159: Variable Set [ Name:%code_start_line_num To:%line_num + 1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A160: Else 

        A161: Variable Set [ Name:%code_start_line_num To:%line_num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A162: End If 

    A163: Variable Set [ Name:%actions_label To:
        Actions: Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Push actions_label At code_start_line_num>
    A164: Array Push [ Variable Array:%code Position:%code_start_line_num Value:%actions_label Fill Spaces:Off ] 

    A165: Variable Set [ Name:%lines_count To:%code(#) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A166: Variable Set [ Name:%code_start_line_num To:%code_start_line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A167: Variable Set [ Name:%line_num To:%code_start_line_num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A168: Variable Clear [ Name:%current_code_type Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

    A169: Variable Set [ Name:%current_code_type_line_count To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A170: Variable Set [ Name:%current_code_type_start_line_num To:%line_num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <Process Task Code Loop Start>
    A171: Anchor 

    A172: [X] Flash [ Text:%code(%line_num) Long:Off ] 

    A173: Variable Set [ Name:%current_line To:%code(%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A174: Variable Set [ Name:%next_line_num To:%line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A175: Variable Set [ Name:%next_line To:%code(%next_line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A176: Variable Set [ Name:%next_to_next_line_num To:%line_num + 2 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    A177: Variable Set [ Name:%next_to_next_line To:%code(%next_to_next_line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    <If Processing Entry Task And Next Line Contains Only Whitespaces And Next To Next Line Starts An Exit Task>
    A178: If [ %is_entry_task_description eq 1 & %next_line ~R %regex_whitespace_only_line & %next_to_next_line ~R %regex_exit_task_name_and_code_line ]

        <Set "1" to exit_task_starting_next>
        A179: Variable Set [ Name:%exit_task_starting_next To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Remove Pre-existing "^[\s]+" Indent From Next Line>
        A180: Variable Search Replace [ Variable:%code(%next_line_num) Search:^[\s]+ Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With: ] 

    A181: Else 

        <Set "0" to exit_task_starting_next>
        A182: Variable Set [ Name:%exit_task_starting_next To:0 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A183: End If 

    <If Not Processing Any Code Type>
    A184: If [ %current_code_type eq \%current_code_type ]

        <If Current Line Starts A Comment>
        A185: If [ %current_line ~R %regex_comment_line_start ]

            <Set "comment" To current_code_type>
            A186: Variable Set [ Name:%current_code_type To:comment Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Current Line Starts An Action>
        A187: Else If [ %current_line ~R %regex_action_line_start ]

            <Set "action" To current_code_type>
            A188: Variable Set [ Name:%current_code_type To:action Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Current Line Starts The Exit Task Of A Profile>
        A189: Else If [ %current_line ~R %regex_exit_task_name_and_code_line ]

            <Goto Process Task Description Start>
            A190: Goto [ Type:Action Label Number:1 Label:Process Task Description Start ] 

        <If Current Line Is Empty Or Contains Only Whitespaces>
        A191: Else If [ %current_line eq \%code%line_num | %current_line ~R %regex_whitespace_only_line ]

            <Goto Next Task Line>
            A192: Goto [ Type:Action Label Number:1 Label:Next Task Line ] 

        <Else Unknown current_code_type>
        A193: Else 

            A194: Flash [ Text:Error! Unknown Code Type At Line %line_num "%current_line" While Processing "%description_task_name" Description Long:On ] 

            A195: Stop [ With Error:Off Task: ] 

        A196: End If 

        <Set "1" to current_code_type_line_count>
        A197: Variable Set [ Name:%current_code_type_line_count To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Set line_num to current_code_type_start_line_num>
        A198: Variable Set [ Name:%current_code_type_start_line_num To:%line_num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A199: End If 

    <If First Line Of Action>
    A200: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "Else If", "Else" "End If" Or "End For">
        A201: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

            <Decrement indent_character_count by single_indent_character_count>
            A202: Variable Set [ Name:%indent_character_count To:%indent_character_count - %single_indent_character_count Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

        A203: End If 

    A204: End If 

    A205: Variable Clear [ Name:%indent_string Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

    <Generate indent_string Based On Current indent_character_count>
    A206: For [ Variable:%num Items:1:%indent_character_count ] 

        A207: Variable Set [ Name:%indent_string To:%indent_character Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

    A208: End For 

    <If First Line Of Action>
    A209: If [ %current_code_type_line_count eq 1 & %current_code_type eq action ]

        <If Current Action Is "If", "Else If", "Else" Or "For">
        A210: If [ %current_line ~R ^[\s]+A[0-9]+: (\[X\] )?((If)|(Else If)|(Else)|(For)).* ]

            <Increment indent_character_count by single_indent_character_count>
            A211: Variable Set [ Name:%indent_character_count To:%indent_character_count + %single_indent_character_count Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

        A212: End If 

    A213: End If 

    <If Processing Comment>
    A214: If [ %current_code_type eq comment ]

        <Replace Pre-existing "^[\s]{4}(%tab)?" Indent With "%indent_string">
        A215: Variable Search Replace [ Variable:%code(%line_num) Search:^[\s]{4}(%tab)? Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string ] 

        <If Comment Ended>
        A216: If [ %current_line ~R %regex_comment_line_end & %next_line ~R %regex_action_line_start ]

            A217: Variable Clear [ Name:%current_code_type Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

            <If Next Action Is "Else If", "Else" "End If" Or "End For">
            A218: If [ %next_line ~R ^[\s]+A[0-9]+: (\[X\] )?((Else If)|(Else)|(End If)|(End For)).* ]

                <For Loop From current_code_type_start_line_num to line_num>
                A219: For [ Variable:%num Items:%current_code_type_start_line_num:%line_num ] 

                    <Remove Single Indent Prefix>
                    A220: Variable Search Replace [ Variable:%code(%num) Search:%regex_single_indent_prefix Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With: ] 

                A221: End For 

            A222: End If 

        A223: End If 

    <Else If Processing Action>
    A224: Else If [ %current_code_type eq action ]

        <Replace Pre-existing "^[\s]{4}(%tab)?" Indent With "%indent_string">
        A225: Variable Search Replace [ Variable:%code(%line_num) Search:^[\s]{4}(%tab)? Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string ] 

        <If Action Ended>
        A226: If [ %current_code_type_line_count eq 1 &+ %current_line !~ *[* | %current_line ~R %regex_action_line_end & %next_line ~R %regex_action_line_start |+ %next_line ~R %regex_comment_line_start |+ %next_line_num > %lines_count | %exit_task_starting_next eq 1 ]

            <Set "0" to skipping_split_action_parameters_on_multiple_lines>
            A227: Variable Set [ Name:%skipping_split_action_parameters_on_multiple_lines To:0 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

            <If split_action_parameters_on_multiple_lines Equals "0">
            A228: If [ %split_action_parameters_on_multiple_lines eq 0 ]

                <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
                A229: Variable Set [ Name:%skipping_split_action_parameters_on_multiple_lines To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

                <Goto End Action Processing>
                A230: Goto [ Type:Action Label Number:1 Label:End Action Processing ] 

            A231: End If 

        A232: Else 

            <Goto Continue Action Processing>
            A233: Goto [ Type:Action Label Number:1 Label:Continue Action Processing ] 

        A234: End If 

        <Process End Of Action>
        A235: Anchor 

        A236: Variable Set [ Name:%action_first_line To:%code(%current_code_type_start_line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        A237: Variable Set [ Name:%action_all_lines To:%code(%current_code_type_start_line_num:%line_num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Action Does Not Contain Parameters>
        A238: If [ %action_first_line !~R %regex_action_line_with_parameters ]

            <Goto End Action Processing>
            A239: Goto [ Type:Action Label Number:1 Label:End Action Processing ] 

        A240: End If 

        A241: Variable Set [ Name:%action_name To:%action_first_line Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <Extract Action Name From First Line Of Action>
        A242: Variable Search Replace [ Variable:%action_name Search:%regex_action_line_with_parameters Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:$1 ] 

        <Set "Else" To action_name If It Is Set To "Else If">
        A243: Variable Set [ Name:%action_name To:Else Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %action_name eq Else If ]

        <Check if action name exists in action names string array is necessary since otherwise if an invalid action name is passed to get action code function, then a popup/warning is generated in tasker>
        A244: Anchor 

        <Get Action Index From Action Names String Array>
        A245: Java Function [ Return:%action_index Class Or Object:%tcujv_c_taskerutils Function:%tcujv_cm_taskerutils_getindexofstringinarray
            {int} (String, String[]) Param:%action_name Param:action_names_string_array Param: Param: Param: Param: Param: Continue Task After Error:On ] 

        <If Action Code Is Not Valid>
        A246: If [ %action_index !~R %regex_valid_number ]

            A247: Flash [ Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Action Index "%action_index" In Action Names List Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
            A248: Variable Set [ Name:%skipping_split_action_parameters_on_multiple_lines To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

            <Goto End Action Processing>
            A249: Goto [ Type:Action Label Number:1 Label:End Action Processing ] 

        A250: End If 

        <Get Action Code From Action Name>
        A251: Java Function [ Return:%action_code Class Or Object:%tcujv_c_taskeractionslist Function:%tcujv_cm_taskeractionslist_getactioncodebyname
            {int} (String) Param:%action_name Param: Param: Param: Param: Param: Param: Continue Task After Error:On ] 

        <If Action Code Is Not Valid>
        A252: If [ %action_code !~R %regex_valid_number | %action_code < 1 ]

            A253: Flash [ Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Action Code "%action_code" Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
            A254: Variable Set [ Name:%skipping_split_action_parameters_on_multiple_lines To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

            <Goto End Action Processing>
            A255: Goto [ Type:Action Label Number:1 Label:End Action Processing ] 

        A256: End If 

        <Find Arguments Size Of Action>
        A257: Anchor 

        A258: Java Function [ Return:%arguments_list_size Class Or Object:%tcujv_c_taskeractionslist Function:%tcujv_cm_taskeractionslist_getargssizeofactionwithcode
            {int} (int) Param:%action_code Param: Param: Param: Param: Param: Param: Continue Task After Error:On ] 

        <If Arguments Size Of Action Is Invalid Or Less Than 1>
        A259: If [ %arguments_list_size !~R %regex_valid_number | %arguments_list_size < 1 ]

            A260: Flash [ Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Invalid Arguments List Size "%arguments_list_size" Long:Off ] If [ %enable_flash_actions eq 1 ]

            <Goto End Action Processing>
            A261: Goto [ Type:Action Label Number:1 Label:End Action Processing ] 

        A262: End If 

        A263: Variable Set [ Name:%arguments_list_size To:%arguments_list_size - 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

        A264: Array Clear [ Variable Array:%argument_names_list ] 

        A265: For [ Variable:%num Items:0:%arguments_list_size ] 

            A266: Variable Set [ Name:%argument_number To:%num Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

            A267: Java Function [ Return:%argument_name Class Or Object:%tcujv_c_taskeractionslist Function:%tcujv_cm_taskeractionslist_getargnameatindexofactionwithcode
                {String} (Resources, int, int) Param:resources Param:%action_code Param:%argument_number Param: Param: Param: Param: ] 

            A268: Java Function [ Return:%argument_name_for_regex Class Or Object:Pattern Function:quote
                {String} (String) Param:%argument_name Param: Param: Param: Param: Param: Param: ] 

            A269: [X] Flash [ Text:argument_name_for_regex: "%argument_name_for_regex" Long:Off ] 

            A270: Variable Set [ Name:%regex_argument_name_repeated To:.*%argument_name_for_regex:.*%argument_name_for_regex:.* Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

            <If Arguments Name Is Repeated In Action Description And Action Code Not In force_split_action_parameters_on_multiple_lines_action_codes, Then Not Safe To Split Action On Multiple Lines>
            A271: If [ %action_all_lines ~R %regex_argument_name_repeated & ,%force_split_action_parameters_on_multiple_lines_action_codes, !~ *,%action_code,* ]

                A272: Flash [ Text:Skipping Split Action On Multiple Lines For Action At Line "%line_num" Named "%action_name" Due To Argument Name "%argument_name" Repetition Long:Off ] If [ %enable_flash_actions eq 1 ]

                <Set "1" to skipping_split_action_parameters_on_multiple_lines if current_code_type_start_line_num < line_num>
                A273: Variable Set [ Name:%skipping_split_action_parameters_on_multiple_lines To:1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] If [ %current_code_type_start_line_num < %line_num ]

                <Goto End Action Processing>
                A274: Goto [ Type:Action Label Number:1 Label:End Action Processing ] 

            A275: End If 

            A276: Variable Set [ Name:%position To:%argument_names_list(#) + 1 Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

            A277: Array Push [ Variable Array:%argument_names_list Position:%position Value:%argument_name Fill Spaces:Off ] 

        A278: End For 

        <For Loop On All Argument Names In argument_names_list>
        A279: For [ Variable:%num Items:1:%argument_names_list(#) ] 

            A280: Variable Set [ Name:%argument_name To:%argument_names_list(%num) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

            A281: Java Function [ Return:%argument_name_for_regex Class Or Object:Pattern Function:quote
                {String} (String) Param:%argument_name Param: Param: Param: Param: Param: Param: ] 

            A282: Variable Set [ Name:%regex_argument_name_exists To:(.*)(%argument_name_for_regex:.*) Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

            <For Loop From current_code_type_start_line_num to line_num>
            A283: For [ Variable:%num1 Items:%current_code_type_start_line_num:%line_num ] 

                <If Action Line Contains The Argument Name>
                A284: If [ %code(%num1) ~R %regex_argument_name_exists ]

                    <Add "%newline%indent_string%single_indent_string" Before argument_name>
                    A285: Variable Search Replace [ Variable:%code(%num1) Search:%regex_argument_name_exists Ignore Case:Off Multi-Line:Off One Match Only:On Store Matches In Array: Replace Matches:On Replace With:$1%newline%indent_string%single_indent_string$2 ] 

                    <Goto Start Of For Loop On All Argument Names In argument_names_list>
                    A286: Goto [ Type:Action Label Number:1 Label:For Loop On All Argument Names In argument_names_list ] 

                A287: End If 

            A288: End For 

        A289: End For 

        <End Action Processing>
        A290: Anchor 

        <If skipping_split_action_parameters_on_multiple_lines Equals "1">
        A291: If [ %skipping_split_action_parameters_on_multiple_lines eq 1 ]

            A292: Variable Set [ Name:%current_code_type_start_line_num_plus_1 To:%current_code_type_start_line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

            <For Loop From current_code_type_start_line_num_plus_1+1 to line_num>
            A293: For [ Variable:%num Items:%current_code_type_start_line_num_plus_1:%line_num ] If [ %current_code_type_start_line_num < %line_num ]

                <Replace Previously Set "^%indent_string" Indent With "%indent_string%single_indent_string">
                A294: Variable Search Replace [ Variable:%code(%num) Search:^%indent_string Ignore Case:Off Multi-Line:Off One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string%single_indent_string ] 

            A295: End For 

        A296: End If 

        A297: Variable Clear [ Name:%current_code_type Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

        <Append Newline To Line>
        A298: Variable Set [ Name:%code(%line_num) To:%newline Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

        <Continue Action Processing>
        A299: Anchor 

    A300: End If 

    A301: Variable Set [ Name:%current_code_type_line_count To:%current_code_type_line_count + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    <Next Task Line>
    A302: Anchor 

    A303: Variable Set [ Name:%line_num To:%line_num + 1 Recurse Variables:Off Do Maths:On Append:Off Max Rounding Digits:3 ] 

    <Goto Process Task Code Loop Start>
    A304: Goto [ Type:Action Label Number:1 Label:Process Task Code Loop Start ] If [ %line_num < %lines_count + 1 ]

    <Process Task Code Loop End>
    A305: Anchor 

    <Join Code Array On Newline>
    A306: Variable Join [ Name:%code Joiner:%newline Delete Parts:Off ] 

    <If cap_indents_at_max_indent_character_count Equals "1">
    A307: If [ %cap_indents_at_max_indent_character_count eq 1 ]

        A308: Variable Clear [ Name:%indent_string Pattern Matching:Off Local Variables Only:Off Clear All Variables:Off ] 

        <Generate indent_string Based On max_indent_character_count>
        A309: For [ Variable:%num Items:1:%max_indent_character_count ] 

            A310: Variable Set [ Name:%indent_string To:%indent_character Recurse Variables:Off Do Maths:Off Append:On Max Rounding Digits:3 ] 

        A311: End For 

        <Replace Indents Greater Than max_indent_character_count With "%indent_string">
        A312: Variable Search Replace [ Variable:%code Search:%regex_set_max_indent Ignore Case:Off Multi-Line:On One Match Only:Off Store Matches In Array: Replace Matches:On Replace With:%indent_string ] 

    A313: End If 

    <If convert_code_to_markdown_code_block Equals "1">
    A314: If [ %convert_code_to_markdown_code_block eq 1 ]

        A315: Variable Set [ Name:%code_for_shell To:%code Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <replace all single quotes (') with nothing>
        A316: Variable Search Replace [ Variable:%code_for_shell Search:' Ignore Case:Off Multi-Line:On One Match Only:Off Store Matches In Array: Replace Matches:On Replace With: ] If [ %code Set ]

        <Find Backticks To Print>
        A317: Run Shell [ Command:code='%code_for_shell'
            
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

        A318: Variable Set [ Name:%exit_code To:%err Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

        <If Failed>
        A319: If [ %exit_code neq \%err | %errors Set ]

            A320: Flash [ Text:Failed To Find Backticks To Print To Convert "%description_task_name" Task Description To Markdown Code Block
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

            A321: Stop [ With Error:Off Task: ] 

        A322: End If 

        <Convert Code To Markdown Code Block>
        A323: Variable Set [ Name:%code To:%backticks_to_print
            %code
            %backticks_to_print Recurse Variables:Off Do Maths:Off Append:Off Max Rounding Digits:3 ] 

    A324: End If 

    A325: Flash [ Text:Format Complete Long:Off ] 

    <If set_clipboard_to_formatted_code Equals "1">
    A326: If [ %set_clipboard_to_formatted_code eq 1 ]

        <Set code To Clipboard Text>
        A327: Set Clipboard [ Text:%code Add:Off ] 

    A328: End If 

    <Return>
    A329: Anchor 

    A330: Return [ Value:%code Stop:On Local Variable Passthrough:Off Replace On Passthrough:Off Limit Passthrough To: ] 

````
