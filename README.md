xdg-menu-to-awesome-wm
======================

Converts a xdg-menu like gnome menu to awesome wm format

How To
======================
```bash
$ python awesome-xdg-menu.py > ~/.config/awesome/menu.lua
```

After you have to add "menu.lua" in your "rc.lua", mine look like this:

```lua
-- {{{ Menu
-- Create a laucher widget and a main menu

myawesomemenu = {
   { "manual", terminal .. " -e man awesome" },
   { "fluxbox", "/bin/bash /home/valens_a/bin/reflux" },
   { "edit config", editor_cmd .. " " .. awful.util.getdir("config") .. "/rc.lua" },
   { "restart", awesome.restart },
   { "quit", awesome.quit }
}

-- Our generated menu is returned from the lua file
-- require("applications") add the file "applications.lua"
local applications_menu = require("applications")
mymainmenu = awful.menu({ items = { { "awesome", myawesomemenu, beautiful.awesome_icon },
-- The next line add our menu (applications_menu)
	        	  	    { "app", applications_menu, beautiful.awesome_icon },
                                    { "open terminal", terminal }
                                  }
                        })

mylauncher = awful.widget.launcher({ image = image(beautiful.awesome_icon),
                                     menu = mymainmenu })


-- }}}
```
