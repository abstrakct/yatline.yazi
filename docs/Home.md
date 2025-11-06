# Welcome to the yatline.yazi wiki

Yatline is a plugin for Yazi, a terminal file manager. It customize both header-line and status-line according to your config.

# Requirements

1) Yazi: <https://github.com/sxyazi/yazi>
2) Nerd Fonts (optional): <https://www.nerdfonts.com/>

# Installation

## Recommended

1) Install the plugin through following command:

``` bash
ya pack -a imsi32/yatline
```

2) Inside of Yazi config file, add one of the following configurations given below.

## General

1) Download the repository.
2) If the directory is downloaded as zip file, extract it.
3) Rename the directory as `yatline.yazi`
4) Open the config directory of Yazi.
5) Copy this directory into `plugins` directory.
6) Create `init.lua` file in the main Yazi config directory.
7) Open this file and copy one of the configs to that file.

## Linux

```
git clone https://github.com/imsi32/yatline.yazi.git ~/.config/yazi/plugins/yatline.yazi
```

# Default Configs

Default configuration for each config parameters can be seen in configuration page of this wiki. Following configs shows example config parameters for newcomers.

## Minimal Config

![minimal config](https://github.com/user-attachments/assets/6a8052cc-fbc8-45be-a8ff-e8ea18e7442c)

``` lua
require("yatline"):setup({
	show_background = false,

	header_line = {
		left = {
			section_a = {
        			{type = "line", custom = false, name = "tabs", params = {"left"}},
			},
			section_b = {
			},
			section_c = {
			}
		},
		right = {
			section_a = {
        			{type = "string", custom = false, name = "date", params = {"%A, %d %B %Y"}},
			},
			section_b = {
        			{type = "string", custom = false, name = "date", params = {"%X"}},
			},
			section_c = {
			}
		}
	},

	status_line = {
		left = {
			section_a = {
        			{type = "string", custom = false, name = "tab_mode"},
			},
			section_b = {
        			{type = "string", custom = false, name = "hovered_size"},
			},
			section_c = {
        			{type = "string", custom = false, name = "hovered_path"},
        			{type = "coloreds", custom = false, name = "count"},
			}
		},
		right = {
			section_a = {
        			{type = "string", custom = false, name = "cursor_position"},
			},
			section_b = {
        			{type = "string", custom = false, name = "cursor_percentage"},
			},
			section_c = {
        			{type = "string", custom = false, name = "hovered_file_extension", params = {true}},
        			{type = "coloreds", custom = false, name = "permissions"},
			}
		}
	},
})

```

## Config With Default Configuration Parameters

![Default-Config](https://github.com/user-attachments/assets/e27b270f-04ed-4968-9661-2f2476f0db10)

``` lua
require("yatline"):setup({
	--theme = my_theme,
	section_separator = { open = "", close = "" },
	part_separator = { open = "", close = "" },
	inverse_separator = { open = "", close = "" },

	style_a = {
		fg = "black",
		bg_mode = {
			normal = "white",
			select = "brightyellow",
			un_set = "brightred"
		}
	},
	style_b = { bg = "brightblack", fg = "brightwhite" },
	style_c = { bg = "black", fg = "brightwhite" },

	permissions_t_fg = "green",
	permissions_r_fg = "yellow",
	permissions_w_fg = "red",
	permissions_x_fg = "cyan",
	permissions_s_fg = "white",

	tab_width = 20,
	tab_use_inverse = false,

	selected = { icon = "󰻭", fg = "yellow" },
	copied = { icon = "", fg = "green" },
	cut = { icon = "", fg = "red" },

	total = { icon = "󰮍", fg = "yellow" },
	succ = { icon = "", fg = "green" },
	fail = { icon = "", fg = "red" },
	found = { icon = "󰮕", fg = "blue" },
	processed = { icon = "󰐍", fg = "green" },

	show_background = true,

	display_header_line = true,
	display_status_line = true,

	component_positions = { "header", "tab", "status" },

	header_line = {
		left = {
			section_a = {
        			{type = "line", custom = false, name = "tabs", params = {"left"}},
			},
			section_b = {
			},
			section_c = {
			}
		},
		right = {
			section_a = {
        			{type = "string", custom = false, name = "date", params = {"%A, %d %B %Y"}},
			},
			section_b = {
        			{type = "string", custom = false, name = "date", params = {"%X"}},
			},
			section_c = {
			}
		}
	},

	status_line = {
		left = {
			section_a = {
        			{type = "string", custom = false, name = "tab_mode"},
			},
			section_b = {
        			{type = "string", custom = false, name = "hovered_size"},
			},
			section_c = {
        			{type = "string", custom = false, name = "hovered_path"},
        			{type = "coloreds", custom = false, name = "count"},
			}
		},
		right = {
			section_a = {
        			{type = "string", custom = false, name = "cursor_position"},
			},
			section_b = {
        			{type = "string", custom = false, name = "cursor_percentage"},
			},
			section_c = {
        			{type = "string", custom = false, name = "hovered_file_extension", params = {true}},
        			{type = "coloreds", custom = false, name = "permissions"},
			}
		}
	},
})
```

## Only Header-line Config

![Only-Header-Line-Config](https://github.com/user-attachments/assets/53f11e80-5407-4fa2-a76a-9850cea235cf)


```lua
require("yatline"):setup({
	show_background = true,

	header_line = {
		left = {
			section_a = {
        			{type = "line", custom = false, name = "tabs", params = {"left"}},
			},
			section_b = {
			},
			section_c = {
			}
		},
		right = {
			section_a = {
        			{type = "coloreds", custom = true, name = {{" 󰇥 ", "#3c3836"}}},
			},
			section_b = {
			},
			section_c = {
        			{type = "coloreds", custom = false, name = "count"},
			}
		}
	},

	status_line = {
		left = {
			section_a = {
			},
			section_b = {
			},
			section_c = {
			}
		},
		right = {
			section_a = {
			},
			section_b = {
			},
			section_c = {
			}
		}
	},
})
```

## Only Status-line Config

![Only-Status-Line-Config](https://github.com/user-attachments/assets/b58fa8a8-f4e1-4929-bea3-dc5c98da7014)


```lua
require("yatline"):setup({
	show_background = true,

	header_line = {
		left = {
			section_a = {
			},
			section_b = {
			},
			section_c = {
			}
		},
		right = {
			section_a = {
			},
			section_b = {
			},
			section_c = {
			}
		}
	},
	status_line = {
		left = {
			section_a = {
        			{type = "string", custom = false, name = "tab_mode"},
			},
			section_b = {
        			{type = "string", custom = false, name = "hovered_size"},
			},
			section_c = {
        			{type = "string", custom = false, name = "hovered_name"},
			}
		},
		right = {
			section_a = {
        			{type = "string", custom = false, name = "cursor_position"},
			},
			section_b = {
        			{type = "string", custom = false, name = "cursor_percentage"},
			},
			section_c = {
        			{type = "coloreds", custom = false, name = "permissions"},
			}
		}
	},
})
```
