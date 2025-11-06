# Git Repository Status Component

A comprehensive Git repository status component for yatline that displays branch information, commits ahead/behind, and file change statistics.

## Features

- **Branch Information**: Shows current branch name or commit hash (for detached HEAD)
- **Upstream Tracking**: Displays commits ahead/behind upstream
- **Repository State**: Visual indicator for clean/dirty state
- **File Changes**: Detailed breakdown of:
  - Staged files
  - Added files
  - Modified files
  - Deleted files
  - Renamed files
  - Untracked files
- **Stash Count**: Optional display of stashed changes
- **Customizable Icons**: Use any UTF-8 characters/Nerd Font icons
- **Configurable Colors**: Customize colors for each state

## Installation

1. Copy `git-repo-status.lua` to your yatline plugin directory:

   ```bash
   cp git-repo-status.lua ~/.config/yazi/plugins/yatline.yazi/
   ```

2. Require it in your Yazi `init.lua` after yatline initialization

## Usage

### Basic Usage

Add the component to your yatline configuration:

```lua
require("yatline"):setup({
	-- ... other yatline config ...
	
	status_line = {
		left = {
			section_a = {},
			section_b = {},
			section_c = {
				-- Add git status component
				{
					type = "coloreds",
					custom = false,
					name = "git_repo_status"
				},
			}
		},
		-- ... rest of config ...
	}
})

-- Initialize the git component (auto-registers with Yatline)
require("yatline.git-repo-status"):setup()
```

### Custom Configuration

Customize icons, colors, and display options:

```lua
require("yatline.git-repo-status"):setup({
	-- Customize icons
	icons = {
		branch = "󰘬",      -- Branch icon
		ahead = "⇡",       -- Commits ahead
		behind = "⇣",      -- Commits behind
		clean = "✓",       -- Clean repository
		dirty = "✗",       -- Dirty repository
		added = "+",       -- Added files
		deleted = "-",     -- Deleted files
		modified = "~",    -- Modified files
		renamed = "»",     -- Renamed files
		untracked = "?",   -- Untracked files
		staged = "●",      -- Staged files
	},
	
	-- Customize colors
	colors = {
		branch = "blue",
		ahead = "green",
		behind = "red",
		clean = "green",
		dirty = "yellow",
		added = "green",
		deleted = "red",
		modified = "yellow",
		renamed = "blue",
		untracked = "magenta",
		staged = "cyan",
	},
	
	-- Display options
	show_branch = true,         -- Show branch name
	show_ahead_behind = true,   -- Show ahead/behind counts
	show_stashes = false,       -- Show stash count
	show_clean = true,          -- Show indicator when repo is clean
	compact = false,            -- Compact mode (fewer details)
})
```

### Compact Mode

For a more minimal display, enable compact mode:

```lua
git_status.setup({
	compact = true,
	show_clean = false,  -- Don't show clean indicator in compact mode
})
```

This will show:

- Branch name
- Ahead/behind counts
- Total number of changes (without breakdown)

## Configuration Options

### Icons

| Option | Default | Description |
|--------|---------|-------------|
| `branch` | `` | Branch icon |
| `ahead` | `⇡` | Commits ahead of upstream |
| `behind` | `⇣` | Commits behind upstream |
| `clean` | `✓` | Repository is clean |
| `dirty` | `✗` | Repository has changes |
| `added` | `+` | Added files |
| `deleted` | `-` | Deleted files |
| `modified` | `~` | Modified files |
| `renamed` | `»` | Renamed files |
| `untracked` | `?` | Untracked files |
| `staged` | `●` | Staged files |

### Colors

All color options support standard terminal colors:

- `black`, `red`, `green`, `yellow`, `blue`, `magenta`, `cyan`, `white`
- `brightblack`, `brightred`, `brightgreen`, `brightyellow`, `brightblue`, `brightmagenta`, `brightcyan`, `brightwhite`
- Hex colors: `#RRGGBB`

| Option | Default | Description |
|--------|---------|-------------|
| `branch` | `blue` | Branch name color |
| `ahead` | `green` | Ahead count color |
| `behind` | `red` | Behind count color |
| `clean` | `green` | Clean state color |
| `dirty` | `yellow` | Dirty state color |
| `added` | `green` | Added files color |
| `deleted` | `red` | Deleted files color |
| `modified` | `yellow` | Modified files color |
| `renamed` | `blue` | Renamed files color |
| `untracked` | `magenta` | Untracked files color |
| `staged` | `cyan` | Staged files color |

### Display Options

| Option | Default | Description |
|--------|---------|-------------|
| `show_branch` | `true` | Display branch name |
| `show_ahead_behind` | `true` | Display ahead/behind counts |
| `show_stashes` | `false` | Display stash count |
| `show_clean` | `true` | Show indicator when repo is clean |
| `compact` | `false` | Use compact mode (less detail) |

## Examples

### Full Configuration Example

```lua
require("yatline"):setup({
	status_line = {
		left = {
			section_a = {
				{ type = "string", custom = false, name = "tab_mode" },
			},
			section_b = {
				{ type = "string", custom = false, name = "hovered_size" },
			},
			section_c = {
				{ type = "string", custom = false, name = "hovered_path" },
				{ type = "coloreds", custom = false, name = "git_repo_status" },
			},
		},
		right = {
			section_a = {
				{ type = "string", custom = false, name = "cursor_position" },
			},
			section_b = {
				{ type = "coloreds", custom = false, name = "count" },
			},
			section_c = {
				{ type = "coloreds", custom = false, name = "permissions" },
			},
		},
	},
})

-- Initialize git status component
local git_status = require("yatline.git-repo-status")
git_status.setup({
	icons = {
		branch = "󰘬",
		clean = "",
		dirty = "",
	},
	colors = {
		branch = "#89b4fa",
		clean = "#a6e3a1",
		dirty = "#f9e2af",
	},
	show_stashes = true,
})

-- Register the component
require("yatline").coloreds.get.git_repo_status = function()
	return git_status.get_status()
end
```

### Minimal Example

```lua
require("yatline"):setup({
	-- ... your config ...
	status_line = {
		left = {
			section_c = {
				{ type = "coloreds", custom = false, name = "git_repo_status" },
			},
		},
	},
})

local git_status = require("yatline.git-repo-status")
git_status.setup({ compact = true, show_clean = false })

require("yatline").coloreds.get.git_repo_status = function()
	return git_status.get_status()
end
```

## Display Examples

### Clean Repository

```text
 main ✓
```

### Dirty Repository with Changes

```text
 main ✗ +2 ~3 -1 ?4
```

- `+2`: 2 added files
- `~3`: 3 modified files
- `-1`: 1 deleted file
- `?4`: 4 untracked files

### With Ahead/Behind

```text
 main ⇡3 ⇣1 ✗ ●2 ~1
```

- `⇡3`: 3 commits ahead
- `⇣1`: 1 commit behind
- `●2`: 2 staged files
- `~1`: 1 modified file

### Compact Mode

```text
 main ⇡2 (5)
```

- `⇡2`: 2 commits ahead
- `(5)`: 5 total changes

## Requirements

- Yazi file manager
- Git command-line tool
- yatline plugin

## Troubleshooting

### Component doesn't appear

Make sure:

1. The component is properly registered after yatline initialization
2. You're in a directory that is part of a git repository
3. Git is installed and accessible in your PATH

### Colors don't match theme

Adjust the `colors` configuration to match your terminal theme or use hex color codes.

### Performance issues in large repositories

The component runs git commands synchronously. In very large repositories, this might cause slight delays. Consider:

- Using `compact = true` for faster updates
- Disabling `show_stashes` if you don't use git stash

## Credits

Created for the yatline.yazi plugin ecosystem.
