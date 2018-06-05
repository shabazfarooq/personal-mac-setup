## Install Chrome
Download and install Chrome.
Sign in, all extensions available from the chrome app store will automatically install.While non-app store extensions will need to be installed manually

Install extensions:
1. [SFDC Chrome Shortcuts](https://github.com/shabazfarooq/SFDC-Shortcuts-Chrome)
2. StreetEasy, apartment to work

Extensions that will transfer over:
1. [Duplicate Tab Shortcut Key](https://chrome.google.com/webstore/detail/duplicate-tab-shortcut-ke/pfippblampohahkkdoomekekmfbjkimg?hl=en)
2. [Keyboard Shortcuts to Reorder Tabs](https://chrome.google.com/webstore/detail/keyboard-shortcuts-to-reo/moigagbiaanpboaflikhdhgdfiifdodd?hl=en)
3. [Salesforce API Fieldnames](https://chrome.google.com/webstore/detail/salesforce-api-fieldnames/oghajcjpbolpfoikoccffglngkphjgbo?hl=en)
4. [Tab to Window/Popup - Keyboard Shortcut](https://chrome.google.com/webstore/detail/tab-to-windowpopup-keyboa/adbkphmimfcaeonicpmamfddbbnphikh/related?hl=en)
5. Adblock Plus

## System Preferences

##### General >
"Use dark menu bar and Dock"

"Default web browser": Chrome

"Recent items": 5

##### Dock >
"Size": small
"Automatically hide and show the Dock"
"Minimize windows into applicaiton icon"

##### Keyboard >
"Key Repeat": Fast
"Delay Unil Repeat": Short
"Modifier keys.." > swap command and option *for usb keyboard*

##### Mouse >
"Tracking speed": Fast

##### Trackpad >
"Tap to click"
To Enable Three Finger Drag: Accessibility > Mouse & Trackpad > Trackpad Options... > Enable dragging > three finger drag



#### Key Repeat
System Preferences > Keyboard > "Key Repeat" max right and "Delay Until Repeat" max right

#### 2. Setup Finder:
1. new finder window shows: Shabaz
2. tags: none
3. setup sidebar favs
4. advanced: “show all filename extensions”



#### 3. BetterTouchTool
1. In advanced settings, select "Launch BetterTouchTool on startup"
2. In advanced settings, unselect "Show Menubar icon"
1. Setup keyboard shortcuts:
![alt text](https://github.com/shabazfarooq/personal-mac-setup/blob/master/BTT_KB.png "")



#### 4. Karabiner Elements
1. Swap command and option (use this if standard option to swap is not working):
![](https://github.com/shabazfarooq/personal-mac-setup/blob/master/Karabiner_Simple.png)
2. Create JSON file to add Pok3r keys: .config/karabiner/assets/complex_modifications/arrows.json
```
{
  "title": "Pok3r arrow and pageup/down keys",
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
1. After installing, click the taskbar icon and select "open config", add the following code:
```
-- HANDLE SCROLLING
local oldmousepos = {}
-- positive multiplier (== natural scrolling) makes mouse work like traditional scrollwheel
local scrollmult = 4 

-- The were all events logged, when using `{"all"}`
mousetap = hs.eventtap.new({0,3,5,14,25,26,27}, function(e)
  oldmousepos = hs.mouse.getAbsolutePosition()
  local mods = hs.eventtap.checkKeyboardModifiers()
  local pressedMouseButton = e:getProperty(hs.eventtap.event.properties['mouseEventButtonNumber'])
  -- If OSX button 4 is pressed, allow scrolling
  local shouldScroll = 3 == pressedMouseButton

  if shouldScroll then
    local dx = e:getProperty(hs.eventtap.event.properties['mouseEventDeltaX'])
    local dy = e:getProperty(hs.eventtap.event.properties['mouseEventDeltaY'])
    local scroll = hs.eventtap.event.newScrollEvent({dx * scrollmult, dy * scrollmult},{},'pixel')
    scroll:post()

    -- put the mouse back
    hs.mouse.setAbsolutePosition(oldmousepos)

    return true, {scroll}
  else
    return false, {}
  end
    -- print ("Mouse moved!")
    -- print (dx)
    -- print (dy)
end)

mousetap:start()
```
2. Open Preferences, deselect "Show Dock Icon", deselect "Show Toolbar Icon", and select "startup at login" if not already selected




### 6. Iterm2
1. Disable confirm quit: Open Preferences, under "Closing" uncheck all items
2. Open new tabs in same dir: Open Preferences, Go to Profiles Tab, under "Working Directory" select "Reuse previous sessions directory"
3. Set colors: Open Preferences, Go to Profiles tab, Select Colors subtab, Set "Foreground" to black, and "Background" to white.
dark theme: bg: 1e1f29 fg: bfbfbf
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
##### Install Agila theme
Add to preferences:
```
	"theme": "Agila.sublime-theme",
  	"color_scheme": "Packages/Agila Theme/Agila Oceanic Next.tmTheme",
	"theme_agila_sidebar_small": true

```

##### Setup preferences.sublime-settings
```
{
	"auto_close_tags": false,
	"auto_match_enabled": false,
	"caret_extra_bottom": 3,
	"caret_extra_top": 3,
	"caret_extra_width": 2,
	"draw_white_space": "all",
	"file_exclude_patterns":
	[
		"*meta.xml",
		"*sublime*"
	],
	"folder_exclude_patterns":
	[
		".svn"
	],
	"font_size": 16,
	"highlight_modified_tabs": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"ignored_words":
	[
		"Accessor",
		"callout",
		"picklist"
	],
	"indent_guide_options":
	[
		"draw_normal",
		"draw_active"
	],
	"preview_on_click": false,
	"rulers":
	[
		80,
		100
	],
	"spell_check": true,
	"tab_size": 2,
	"translate_tabs_to_spaces": true
}

```
##### Plugins:
1. Install [Package Control](https://packagecontrol.io/installation)
2. Install "Clipboard Diff"
3. Install "Pretty JSON"
4. git clone [Force-Actions](https://github.com/shabazfarooq/Force-Actions) to  ~/Library/Application Support/Sublime Text 3/Packages
5. SFDC Syntax Highlighting: git clone [SFDC-Syntax](https://github.com/shabazfarooq/SFDC-Syntax) to ~/Library/Application Support/Sublime Text 3/Packages/
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









