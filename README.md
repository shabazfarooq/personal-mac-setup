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
5. Set font: Open Preferences, go to Profiles tab, select Text subtab, select "Change Font" and set to 15
6. Always show tab bar: Open Preferences, go to Apperance tab, select "Show tab bar even when there is only one tab"
7. Edit/Create .bash_profile (if it doesn't work, create .bashrc)
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
2. [Duplicate Tab Shortcut Key](https://chrome.google.com/webstore/detail/duplicate-tab-shortcut-ke/pfippblampohahkkdoomekekmfbjkimg?hl=en)
3. [Keyboard Shortcuts to Reorder Tabs](https://chrome.google.com/webstore/detail/keyboard-shortcuts-to-reo/moigagbiaanpboaflikhdhgdfiifdodd?hl=en)
4. [Salesforce API Fieldnames](https://chrome.google.com/webstore/detail/salesforce-api-fieldnames/oghajcjpbolpfoikoccffglngkphjgbo?hl=en)
5. [Tab to Window/Popup - Keyboard Shortcut](https://chrome.google.com/webstore/detail/tab-to-windowpopup-keyboa/adbkphmimfcaeonicpmamfddbbnphikh/related?hl=en)
6. Adblock Plus
7. StreetEasy, apartment to work


### Salesforce tools (not directly sublime related)
1. Install [create-force-login](https://github.com/shabazfarooq/force-login-setup) to /usr/local/bin
(this contains build.xml and package.xml, add them to the parent sfdc-directory)
2. Install [force-cli](https://developer.salesforce.com/tools/forcecli) to /usr/local/bin
(chmod +x the force file, copy it to force-original as well)

##### Install ant:
1. Install [Homebrew](https://brew.sh/)
2. Install ant: brew install ant
3. Download [Force Migration Tool](https://developer.salesforce.com/docs/atlas.en-us.daas.meta/daas/forcemigrationtool_install.htm)
4. Unzip Force Migration Tool and copy ant-salesforce.jar to: /usr/local/Cellar/ant/1.10.1/libexec/lib

### 8. Sublime Text
##### Setup preferences.sublime-settings
```
...
```
##### Plugins:
1. Install [Package Control](https://packagecontrol.io/installation)
2. Install "Clipboard Diff"
3. Install "Pretty JSON"
4. git clone [Force-Actions](https://github.com/shabazfarooq/Force-Actions) to  ~/Library/Application Support/Sublime Text 3/Packages
5. SFDC Syntax Highlighting: 1) Create folder: ~/Library/Application Support/Sublime Text 3/Packages/SFDC-Syntax 2) copy both files from [here](https://github.com/joshbirk/ForceDotBundle/tree/master/Syntaxes) to new folder. Files will auto use this no further setup necessarry.
6. Install MoveTab, then Setup keyboard shortcuts, click "Sublime Text", "Preferences", "Key Bindings":
```
[
  {
    "keys": [
      "ctrl+shift+pageup"
    ],
    "command": "move_tab",
    "args": {
      "position": "-1"
    }
  },
  {
    "keys": [
      "ctrl+shift+pagedown"
    ],
    "command": "move_tab",
    "args": {
      "position": "+1"
    }
  }
]
```


##### Setup SFDC save:
1. Install NPM: brew install npm
2. Install [Force-Faster-Save](https://github.com/shabazfarooq/Force-Faster-Save) to ~/node-workspace/ then npm install in folder
3. Create new build system in sublime for sfdc:
create file and add: ~/Library/Application Support/Sublime Text 3/Packages/User/Force-Faster-Save.sublime-build
Then for SFDC files set it to use this build system (tools>build..)
```
{
  "cmd": ["~/node-workspace/Force-Faster-Save/main.js ${file}"],
  "shell": true
}
```









