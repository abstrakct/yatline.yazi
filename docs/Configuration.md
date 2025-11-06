# Theme

Theme contains other style related config parameters to late you easily change it. For theme creation see theming page. Theme contains following config parameter types:

1. Separator
2. Sections
3. Permissions
4. Count
5. Tasks

# Separator

Separators are placed between components. Their colors are decided by these component's types. They can be configured as icon from [Nerd Fonts](https://www.nerdfonts.com/) or any length of string.

> e.g. Using icons (Default):
>
> ```lua
> section_separator = { open = "", close = "" },
> part_separator = { open = "", close = "" },
> inverse_separator = { open = "", close = "" },
> ```
>
> ![separator_as_icon](https://github.com/imsi32/yatline.yazi/assets/81227251/1239d8de-717f-4e2d-a87e-44864d7f67b6)

> e.g. Using string:
>
> ```lua
> section_separator = { open = "", close = "" },
> part_separator = { open = "<In>", close = "<Out>" },
> inverse_separator = { open = "tab", close = "TAB" },
> ```
>
> ![separator_as_string](https://github.com/imsi32/yatline.yazi/assets/81227251/cef82843-6338-4bd4-ade4-15688f5c2ada)

# Sections

Each side of either header-line or status-line contains 3 sections. For each section you can set its background and foreground colors in config and in the [‎set_component_style‎](https://github.com/imsi32/yatline.yazi/blob/973d762dd67d49094ad290522d142b6e0223be82/init.lua#L133) function you can use method of [Style](https://yazi-rs.github.io/docs/plugins/layout#style). Moreover, section-a will change its color according to the active tab's mode.

> e.g. (Default):
>
> ```lua
> style_a = {
> 	fg = "black",
> 	bg_mode = {
> 		normal = "white",
> 		select = "brightyellow",
> 		un_set = "brightred"
> 	}
> },
> style_b = { bg = "brightblack", fg = "brightwhite" },
> style_c = { bg = "black", fg = "brightwhite" },
> ```

> e.g. Sections style:
>
> ```lua
> style_a = {
> 	fg = "black",
> 	bg_mode = {
> 		normal = "#a89984",
> 		select = "#d79921",
> 		un_set = "#d65d0e"
> 	}
> },
> style_b = { bg = "#665c54", fg = "#ebdbb2" },
> style_c = { bg = "#3c3836", fg = "#a89984" },
> ```
>
> ![sections_normal](https://github.com/imsi32/yatline.yazi/assets/81227251/70adcf33-61a6-466b-9b13-4c1c704dbdb7)
> ![sections_select](https://github.com/imsi32/yatline.yazi/assets/81227251/08523d20-f388-437a-884f-c1424bf661dd)
> ![sections_un_set](https://github.com/imsi32/yatline.yazi/assets/81227251/4ff11bf5-d37f-478b-9822-4cbdcf024a20)

# Permissions

These colors are used in the permission component.

> e.g. Permission foreground colors (default):
>
> ```lua
> permissions_t_fg = "green",
> permissions_r_fg = "yellow",
> permissions_w_fg = "red",
> permissions_x_fg = "cyan",
> permissions_s_fg = "white",
> ```
>
> ![permissions](https://github.com/imsi32/yatline.yazi/assets/81227251/aa0bab73-daaf-41ca-93b3-99b77eca55e8)

# Tabs Width

Tab's width can be changed in config. If the tab width is small, there will be no text which will be shown. Otherwise, name of tab's current directory's name will be shown.

> e.g. With name (default):
>
> ```lua
> tab_width = 20,
> ```
>
> ![tabs_normal](https://github.com/imsi32/yatline.yazi/assets/81227251/e0db9ce6-bcaf-4a3d-9f45-e661d70f33f0)

> e.g. With zero width:
>
> ```lua
> tab_width = 0,
> ```
>
> ![tabs_zero_width](https://github.com/imsi32/yatline.yazi/assets/81227251/8d09c454-6697-49d5-b81f-2beb5de6a3ba)

# Count

These icons from [Nerd Fonts](https://www.nerdfonts.com/) (or any length of string) and foreground colors are used in the count component.

> e.g. Count configuration (default):
>
> ``` lua
> selected = { icon = "󰻭", fg = "yellow" },
> copied = { icon = "", fg = "green" },
> cut = { icon = "", fg = "red" },
> ```
>
> ![count_selected_and_copied](https://github.com/imsi32/yatline.yazi/assets/81227251/de1c437d-3e47-43a7-874a-f45a7deb2c6c)  
> ![count_selected_and_cut](https://github.com/imsi32/yatline.yazi/assets/81227251/368408dd-f7ed-4a3e-8c9f-835b3c17323b)

# Tasks

These icons from [Nerd Fonts](https://www.nerdfonts.com/) (or any length of string) and foreground colors are used in the task related components.

> e.g. Tasks configuration (default):
>
> ``` lua
> total = { icon = "󰮍", fg = "yellow" },
> succ = { icon = "", fg = "green" },
> fail = { icon = "", fg = "red" },
> found = { icon = "󰮕", fg = "blue" },
> processed = { icon = "󰐍", fg = "green" },
> ```
>
> ![task_states](https://github.com/imsi32/yatline.yazi/assets/81227251/592e38b0-6035-4e2b-a71b-c86ef4489b22)  
> ![task_workload](https://github.com/imsi32/yatline.yazi/assets/81227251/30306058-4672-4e1e-be3d-b4844718fec9)

# Background

Makes the background color of both header-line and status-line same with section-c.

> e.g.
>
> ```lua
> show_background = false,
> ```
>
> ![show_background_false](https://github.com/imsi32/yatline.yazi/assets/81227251/7103a05a-62e3-4ce3-a6cc-7f7444ca686e)

> e.g. (default)
>
> ```lua
> show_background = true,
> ```
>
> ![show_background_true](https://github.com/imsi32/yatline.yazi/assets/81227251/7e24e60b-ce01-47ec-95c4-51c4fd580407)

# Display

If either header-line or status-line want to removed completely, these values can be set to false.

> e.g. (default)
>
> ```lua
> display_header_line = true,
> display_status_line = true,
> ```

> e.g. Removing both header-line and status-line:
>
> ```lua
> display_header_line = false,
> display_status_line = false,
> ```

# Component Positions

Move header-line, status-line and tab to your desired place.

> e.g. (default)
>
> ```lua
> component_positions = { "header", "tab", "status" },
> ```

> e.g. Moving status-line to top of the window:
>
> ```lua
> component_positions = { "status", "header", "tab" },
> ```
>
![status-line_at_the_top](https://github.com/user-attachments/assets/d1453346-0f7b-42e3-9b87-e57bf3378489)


# Lines

There is two line: header-line and status-line. For each line there two side to be considered: left and right. For each side there are three section: a, b and c. For each section any number of components can be added. If there is no component in line, Yazi's equivalent line will be used instead of that line (Default).

> e.g. Lines configuration:
>
> ``` lua
> header_line = {
> 	left = {
> 		section_a = {
>         		{type = "string", custom = true, name = "a"},
> 		},
> 		section_b = {
>         		{type = "string", custom = true, name = "b"},
>         		{type = "string", custom = true, name = "left"},
> 		},
> 		section_c = {
>         		{type = "string", custom = true, name = "c"},
>         		{type = "string", custom = true, name = "left"},
>         		{type = "string", custom = true, name = "header"},
> 		}
> 	},
> 	right = {
> 		section_a = {
>         		{type = "string", custom = true, name = "a"},
> 		},
> 		section_b = {
>         		{type = "string", custom = true, name = "b"},
>         		{type = "string", custom = true, name = "right"},
> 		},
> 		section_c = {
>         		{type = "string", custom = true, name = "c"},
>         		{type = "string", custom = true, name = "right"},
>         		{type = "string", custom = true, name = "header"},
> 		}
> 	}
> },
>
> status_line = {
> 	left = {
> 		section_a = {
>         		{type = "string", custom = true, name = "status"},
>         		{type = "string", custom = true, name = "left"},
>         		{type = "string", custom = true, name = "a"},
> 		},
> 		section_b = {
>         		{type = "string", custom = true, name = "left"},
>         		{type = "string", custom = true, name = "b"},
> 		},
> 		section_c = {
>         		{type = "string", custom = true, name = "c"},
> 		}
> 	},
> 	right = {
> 		section_a = {
>         		{type = "string", custom = true, name = "status"},
>         		{type = "string", custom = true, name = "right"},
>         		{type = "string", custom = true, name = "a"},
> 		},
> 		section_b = {
>         		{type = "string", custom = true, name = "right"},
>         		{type = "string", custom = true, name = "b"},
> 		},
> 		section_c = {
>         		{type = "string", custom = true, name = "c"},
> 		}
> 	}
> },
> ```
>
> ![header_line](https://github.com/imsi32/yatline.yazi/assets/81227251/db4a3d34-338a-4a49-88e7-6a2298d25fd6)  
> ![status_line](https://github.com/imsi32/yatline.yazi/assets/81227251/fbb0b983-a184-4b23-8540-236a73130d3d)
