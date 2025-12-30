> What are they?

Add-ons are Yazi plugins that have support for yatline.yazi.

> Why use them?

They provide extended ways to customize and get new features for yatline.yazi.

> Where can they be found?

You can check [add-ons](https://github.com/imsi32/yatline-addons).

# Creation

Yazi has three types of default components group: string, coloreds and line.  
These component groups can be extended easily by following their common structure:


``` lua

Yatline.TYPE = {}
Yatline.TYPE.get = {}
Yatline.TYPE.has_separator = true
Yatline.TYPE.create(TYPE, component_type)

```

However, in most cases it will not be necessary to create a new component type group.  
You can use default component type groups by renaming `your_function()` to relevant option:
- If it returns string: `Yatline.string.get.your_function()`  
- If it returns coloreds: `Yatline.coloreds.get.your_function()`  
- If it returns ui.Line(): `Yatline.line.get.your_function()`  

You can get more information about component's type from [components](https://github.com/imsi32/yatline.yazi/wiki/Components) page.

# Usage

> [!IMPORTANT]
> You need to initialize add-on after yatline's initialization.

You can then use your component like this:

``` lua
{type = "TYPE", custom = false, name = "your_function", params = {IF_ANY}},

```