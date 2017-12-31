#### 1. Enable three finger drag
1. System Preferences -> Accessibility -> Trackpad -> ..


#### 2. Setup finder:
1. new finder window shows: Shabaz
2. tags: none
3. setup sidebar favs
4. advanced: “show all filename extensions”


#### 4. Better touch tool
1. Setup keyboard shortcuts:
![alt text](https://github.com/shabazfarooq/personal-mac-setup/blob/master/BetterTouchToolKB.png "")



#### 3. Karabiner elements:
1. Create JSON file to add arrows: .config/karabiner/assets/complex_modifications/arrows.json
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
    }
  ]
}
```


#### 4. Hammer spoon
1. After installing, click the taskbar icon and select "open config", add the following code:
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


5. Iterm2: a)  



Apps:
Chrome
Sublime Text






