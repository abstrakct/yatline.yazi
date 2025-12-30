# String-based Components

These components automatically created by a function which takes the string from desired function.

## Custom

A custom parameter lets you create components from the given string in name parameter.

> e.g. A custom component
>
> ```lua
> {type = "string", custom = true, name = "Hello World!"},
> ```

## Default

### Hovered Name

Create a component that has hovered file's or directory's name.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "hovered_name"},
> ```

> e.g. With default config parameters
>
> ```lua
> {type = "string", custom = false, name = "hovered_name", params = {{ trimed = false, show_symlink = false, max_length=24, trim_length=10 }},
> ```

### Hovered Path

Create a component that has hovered file's or directory's path.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "hovered_path"},
> ```

> e.g. With default config parameters
>
> ```lua
> {type = "string", custom = false, name = "hovered_path", params = {{ trimed = false, max_length=24, trim_length=10 }},
> ```

### Hovered Size

Create a component that has hovered file's or directory's size.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "hovered_size"},
> ```

### Hovered Mime

Create a component that has hovered file's mime.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "hovered_mime"},
> ```

### Hovered Ownership

Create a component that has hovered file's user and group ownership. Only for unix-like systems.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "hovered_ownership"},
> ```

### Hovered File Extension

Create a component that has hovered file's or directory's extension.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "hovered_file_extension"},
> ```

### Tab Path

Create a component that has current active tab's path.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "tab_path"},
> ```

> e.g. With default config parameters.
>
> ```lua
> {type = "string", custom = false, name = "tab_path", params = {{ trimed = false, max_length=24, trim_length=10 }},
> ```

### Tab Mode

Create a component that has active tab's mode.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "tab_mode"},
> ```

### Tab Mode

Create a component that has number of files in the current active tab.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "tab_num_files"},
> ```

### Cursor Position

Create a component that has cursor's position in the current active tab.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "cursor_position"},
> ```

### Cursor Percentage

Create a component that has cursor's percentage in the current active tab.

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "cursor_percentage"},
> ```

### Date

Create a component that has date according to the given format (See [formats](https://www.lua.org/pil/22.1.html)).

> e.g.
>
> ```lua
> {type = "string", custom = false, name = "date", params = {"%A, %d %B %Y"}},
> ```

# Coloreds-based Components

Coloreds is an array of pair of string and color. These components used to multi-colorize single component but they can also used with single pair of string and color, too.

## Custom

A custom parameter lets you create components from the given coloreds in name parameter.

> e.g. A custom component
>
> ```lua
> {type = "coloreds", custom = true, name = {{"Hello ", "red"}, {"World", "green"}}},
> ```

## Default

### Permissions

Create a component that has hovered file's or directory's permissions. Colors of these component can be configured in config. Only for unix-like systems.

> e.g.
>
> ```lua
> {type = "coloreds", custom = false, name = "permissions"},
> ```
>
> ![permissions](https://github.com/imsi32/yatline.yazi/assets/81227251/57ea6c10-c8fb-497e-933d-8a900e1c5fa8)


### Count

Create a component that has number of selected and yanked (copied or cut) files of the active tab. If the `filter` parameter is set `true`, it will also show current active tabs' number of files or filtered files, by default it is `false`. Colors of these component can be configured in config.

> e.g.
>
> ```lua
> {type = "coloreds", custom = false, name = "count"},
> ```
>
> ![count_selected_and_copied](https://github.com/imsi32/yatline.yazi/assets/81227251/4780677c-7e35-4a4c-93a4-6dc99d5b287b)  
> ![count_selected_and_cut](https://github.com/imsi32/yatline.yazi/assets/81227251/860d1376-39b8-4b06-ab7a-2b8d5214f6b6)

> e.g. With additional 'filter' parameter
>
> ```lua
> {type = "coloreds", custom = false, name = "count", params = "true"},
> ```
>
> ![count_number_of_files](https://github.com/user-attachments/assets/47c0f476-0d6f-4539-9e41-33c45c8fb436)  
> ![count_number_of_filtered_files](https://github.com/user-attachments/assets/0bbc1b28-6d56-49c7-81f3-baf27afc313a)


### Task States

Create a component that has number of task states. Colors of these component can be configured in config.

> e.g.
>
> ```lua
> {type = "coloreds", custom = false, name = "task_states"},
> ```
>
> ![task_states](https://github.com/imsi32/yatline.yazi/assets/81227251/21b3ca61-9dca-453e-9b16-6d34ed02930d)

### Task Workload

Create a component that has number of task workloads. Colors of these component can be configured in config.

> e.g.
>
> ```lua
> {type = "coloreds", custom = false, name = "task_workload"},
> ```
>
> ![task_workload](https://github.com/imsi32/yatline.yazi/assets/81227251/70ca67ad-384f-4d73-a244-ae9745831ef5)

### String-based Component

Create a component that has a colored string-based component.

> e.g.
>
> ```lua
> {type = "coloreds", custom = false, name = "string_based_component", params = {"date", "blue", {"%A, %d %B %Y"}}},
> ```

# Line-based Components

These components are the most complex components type. They need to manually created and adjusted.

## Custom

A custom parameter lets you create components from the given line in name parameter.

> e.g. A custom component
>
> ```lua
> {type = "line", custom = true, name = custom_line},
> ```

## Default

### Tabs

Create a component that shows tabs. The side which will be needs to be written again in params parameter.

> e.g.
>
> ```lua
> {type = "line", custom = false, name = "tabs", params = {"left"}},
> ```
>
> ![tabs_normal](https://github.com/imsi32/yatline.yazi/assets/81227251/fed8724d-8be8-4b5f-8881-cdd6609a0cb1)  
> ![tabs_select](https://github.com/imsi32/yatline.yazi/assets/81227251/41891ca6-4844-4c36-9a21-3bbe46b50ec1)  
> ![tabs_un_set](https://github.com/imsi32/yatline.yazi/assets/81227251/6cf61f61-0e62-4705-8b73-427f1fe12222)  
