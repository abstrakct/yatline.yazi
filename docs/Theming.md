> [!NOTE]
You do not have to use theme if you want to use your own theme in your config. Theme is implemented because it makes downloading theme from different sources much more easier.

> [!NOTE]
> To find themes that already created see [yatline-themes](https://github.com/imsi32/yatline-themes).

To create your own theme follow these steps:  

1. Create a Yazi plugin for example `my-theme.yazi`. See <https://yazi-rs.github.io/docs/plugins/overview> for more information.  
2. Inside of the `init.lua` file. Create a theme variable such as:

``` lua
local theme = {
	section_separator = { open = "", close = "" },
	part_separator = { open = "", close = "" },
	inverse_separator = { open = "", close = "" },

	style_a = {
		fg = "black",
		bg_mode = {
			normal = "#a89984",
			select = "#d79921",
			un_set = "#d65d0e"
		}
	},
	style_b = { bg = "#665c54", fg = "#ebdbb2" },
	style_c = { bg = "#3c3836", fg = "#a89984" },

	permissions_t_fg = "green",
	permissions_r_fg = "yellow",
	permissions_w_fg = "red",
	permissions_x_fg = "cyan",
	permissions_s_fg = "white",

	selected = { icon = "󰻭", fg = "yellow" },
	copied = { icon = "", fg = "green" },
	cut = { icon = "", fg = "red" },
	files = { icon = "", fg = "blue" },
	filtereds = { icon = "", fg = "magenta" },

	total = { icon = "󰮍", fg = "yellow" },
	succ = { icon = "", fg = "green" },
	fail = { icon = "", fg = "red" },
	found = { icon = "󰮕", fg = "blue" },
	processed = { icon = "󰐍", fg = "green" },
}
```

3. Return the value to be able to use in our config by doing:

``` lua
return { setup = function() return theme end }
```

4. In `yazi's init.lua` file. Add your plugin and get the theme variable with:

``` lua
local my_theme = require("my-theme"):setup()
```

5. Use the variable in your Yatline's config.

``` lua
theme = my_theme,
```
