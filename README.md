#### 1. Enable Three Finger Drag
1. System Preferences -> Accessibility -> Trackpad -> ..



#### 2. Setup Finder:
1. new finder window shows: Shabaz
2. tags: none
3. setup sidebar favs
4. advanced: “show all filename extensions”



#### 3. BetterTouchTool
1. Setup keyboard shortcuts:
![alt text](https://github.com/shabazfarooq/personal-mac-setup/blob/master/BetterTouchToolKB.png "")



#### 4. Karabiner Elements
1. Create JSON file to add Pok3r keys: .config/karabiner/assets/complex_modifications/arrows.json
```
{
  "title": "Right Command + IJKL arrows",
  "rules": [
    {
      "description": "Right Command + i/j/k/l to arrows",
      "manipulators": [
        {
          "from": {
            "key_code": "i",
            "modifiers": {
              "mandatory": [
                "right_command"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "up_arrow"
            }
          ],
          "type": "basic"
        },
        {
          "from": {
            "key_code": "j",
            "modifiers": {
              "mandatory": [
                "right_command"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "left_arrow"
            }
          ],
          "type": "basic"
        },
        {
          "from": {
            "key_code": "k",
            "modifiers": {
              "mandatory": [
                "right_command"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "down_arrow"
            }
          ],
          "type": "basic"
        },
        {
          "from": {
            "key_code": "l",
            "modifiers": {
              "mandatory": [
                "right_command"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "right_arrow"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Right command + u/o to pageup/pagedown",
      "manipulators": [
        {
          "from": {
            "key_code": "u",
            "modifiers": {
              "mandatory": [
                "right_command"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "page_up"
            }
          ],
          "type": "basic"
        },
        {
          "from": {
            "key_code": "o",
            "modifiers": {
              "mandatory": [
                "right_command"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "page_down"
            }
          ],
          "type": "basic"
        }
      ]
    }
  ]
}
```



#### 5. Hammer spoon
1. Open Preferences, deselect "Show Dock Icon"
2. After installing, click the taskbar icon and select "open config", add the following code:
```
-- HANDLE SCROLLING
local oldmousepos = {}
local scrollmult = -4	-- negative multiplier makes mouse work like traditional scrollwheel

mousetap = hs.eventtap.new({5}, function(e)
	oldmousepos = hs.mouse.getAbsolutePosition()
	local mods = hs.eventtap.checkKeyboardModifiers()
	if mods['ctrl'] and mods['cmd'] then
		-- print ("will scroll")
		local dx = e:getProperty(hs.eventtap.event.properties['mouseEventDeltaX'])
		local dy = e:getProperty(hs.eventtap.event.properties['mouseEventDeltaY'])
		local scroll = hs.eventtap.event.newScrollEvent({dx * scrollmult, dy * scrollmult},{},'pixel')
		scroll:post()
		
		-- put the mouse back
		hs.mouse.setAbsolutePosition(oldmousepos)
		
		-- return true, {scroll}
		return true
	else
		return false, {}
	end
	-- print ("Mouse moved!")
	-- print (dx)
	-- print (dy)
end)
mousetap:start()
```



### 6. Iterm2
1. Disable confirm quit: Open Preferences, under "Closing" uncheck all items
2. Open new tabs in same dir: Open Preferences, Go to Profiles Tab, under "Working Directory" select "Reuse previous sessions directory"
3. Set colors: Open Preferences, Go to Profiles tab, Select Colors subtab, Set "Foreground" to black, and "Background" to white.
4. Setup move tabs shortcut: Open preferences, go to Keys tab, set: Move Tab Right: CTRL+SHIFT+PAGE UP, Move Tab Left: CTRL+SHIFT+PAGE DOWN
1. Edit/Create .bash_profile (if it doesn't work, create .bashrc)
```
export PS1="\u: \w > "
export CLICOLOR=1
export LSCOLORS=ExFxCxDxBxegedabagacad
export PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ;} history -n"

# Sublime alias
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"
```

### 7. Chrome
Install extensions:
1. [SFDC Chrome Shortcuts](https://github.com/shabazfarooq/SFDC-Shortcuts-Chrome)
2. 


Apps:
Chrome
Sublime Text






