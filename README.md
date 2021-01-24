
# Jump to #

- [Install Chrome](#Install-Chrome)
- [System Preferences](#System-Preferences)
- [Setup Finder](#Setup-Finder)
- [Hammerspoon](#Hammerspoon)
- [BetterTouchTool](#BetterTouchTool)
- [Karabiner Elements](#Karabiner-Elements)
- [Iterm2](#Iterm2)
- [Sublime Text](#Sublime-Text)
- [Setup Binary Folder](#Setup-Binary-Folder)
- [SFDC Dev Tools](#SFDC-Dev-Tools)










# Install Chrome #
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




# System Preferences #

##### General >
- "Appearance": Dark
- "Show scroll bars": Always
- "Default web browser": Chrome
- "Recent items": 5

##### Dock >
- "Size": small-ish
- "Magnification": min-ish
- "Minimize windows into applicaiton icon"
- "Automatically hide and show the Dock"
- uncheck "Show recent applicaitons in Dock"

##### Keyboard >
- "Key Repeat": Fast
- "Delay Unil Repeat": Short
- "Modifier keys.." > swap command and option *for usb keyboard*

##### Mouse >
- "Tracking speed": Fast

##### Trackpad >
- "Tap to click"
- To Enable Three Finger Drag: Accessibility > Pointer Control > Trackpad Options... > Enable dragging > three finger drag





# Setup Finder #
##### General > 
- new finder window shows: Shabaz

##### Tags >
- unselect all

##### Sidebar >
check: 
- Applications
- Desktop
- Documents
- Downloads
- shabaz

uncheck:
- recents
- recent tags

##### Advanced >
- “show all filename extensions”

##### Reorder side bar as follows:
- shabaz
- Applications
- Downloads
- Desktop
- Documents
- AirDrop

##### View > Show Path Bar



# Hammerspoon #
1. Download and install
2. Open app and allow permissions
3. Click the taskbar icon and select "Preferences", and click "Enable Accessibility"
4. Click the taskbar icon and select "Open Config", add the following code:
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
5. Click the taskbar icon and select reload config
6. Click the taskbar icon and select "Preferences":
- deselect "Show Dock Icon"
- deselect "Show Menu Icon"
- select "Launch Hammerspoon at Login" if not already selected




# BetterTouchTool #
1. Download and install BetterTouchTool
1. Settings > Basic: select "Launch BetterTouchTool on startup"
2. Settings > User Interface: unselect "Show Menubar icon"
1. Setup keyboard shortcuts:
![alt text](https://github.com/shabazfarooq/personal-mac-setup/blob/master/BTT_KB2.png "")




# Karabiner Elements #
1. Download and install
2. Open Karabiner-Elements and go to Misc tab > (uncheck) Show icon in menu bar
3. (For External Keyboards) Swap command and option (use this if standard option to swap is not working):
![](https://github.com/shabazfarooq/personal-mac-setup/blob/master/Karabiner_Simple.png)
4. Create JSON file with code below to add arrow keys: .config/karabiner/assets/complex_modifications/arrows.json
5. Then go to "Complex Modifications" > Add Rule > select
- "Right Command + IJKL arrows"
- "Right Command + u/o to pageup/pagedown"
```
{
  "title": "Right Command + IJKL arrows",
  "rules": [
    {
      "description": "Right Command + IJKL arrows",
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
      "description": "Right Command + u/o to pageup/pagedown",
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
    },
    {
      "description": "Phone Style Numpad With Modifier 0",
      "manipulators": [
        {
          "from": {
            "key_code": "right_command",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "0"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 1",
      "manipulators": [
        {
          "from": {
            "key_code": "u",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "7"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 2",
      "manipulators": [
        {
          "from": {
            "key_code": "i",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "8"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 3",
      "manipulators": [
        {
          "from": {
            "key_code": "o",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "9"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 4",
      "manipulators": [
        {
          "from": {
            "key_code": "j",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "4"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 5",
      "manipulators": [
        {
          "from": {
            "key_code": "k",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "5"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 6",
      "manipulators": [
        {
          "from": {
            "key_code": "l",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "6"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 7",
      "manipulators": [
        {
          "from": {
            "key_code": "m",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "1"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 8",
      "manipulators": [
        {
          "from": {
            "key_code": "comma",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "2"
            }
          ],
          "type": "basic"
        }
      ]
    },
    {
      "description": "Phone Style Numpad With Modifier 9",
      "manipulators": [
        {
          "from": {
            "key_code": "period",
            "modifiers": {
              "mandatory": [
                "left_command", "left_option"
              ],
              "optional": [
                "any"
              ]
            }
          },
          "to": [
            {
              "key_code": "3"
            }
          ],
          "type": "basic"
        }
      ]
    }
  ]
}
```




# Iterm2 #
1. Download and install Iterm 2
2. Disable confirm quit: Preferences > General > Closing: uncheck all items
3. Open new tabs in same dir: Preferences > Profile > General: Working Directory: "Reuse previous sessions directory"
4. Set colors: Preferences > Profile > Colors: Set bg: 1e1f29 fg: bfbfbf
5. Set font: Preferences > Profile > Text: Set font size to 15
6. Setup move tabs shortcut: Preferences > Keys: Move Tab Right: CTRL+SHIFT+PAGE UP, Move Tab Left: CTRL+SHIFT+PAGE DOWN
7. Always show tab bar: Preferences > Apperance: select "Show tab bar even when there is only one tab"
8. Dont stretch tab bars: Preferences > Apperance: unselect "Stetch tabs to fill bar"
8. Edit/Create .zshrc (if it doesn't work, create .bashrc or .bash_profile)
```
export PS1="%n: %~ > "
export CLICOLOR=1
export LSCOLORS=ExFxCxDxBxegedabagacad
export PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ;} history -n"

# Sublime alias
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"
```




# Sublime Text #
1. Downoad and install Sublimetext3
2. Install [Package Control](https://packagecontrol.io/installation)
3. Setup preferences.sublime-settings
```
{
	"show_full_path": true,
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

##### Install Plugins: Package Control: Install Package >
1. "Agila theme"
Add to preferences:
```
	"theme": "Agila.sublime-theme",
  	"color_scheme": "Packages/Agila Theme/Agila Oceanic Next.tmTheme",
	"theme_agila_sidebar_small": true

```
2. "Clipboard Diff"
3. "Pretty JSON"
4. Install MoveTab, then Setup keyboard shortcuts, click "Sublime Text", "Preferences", "Key Bindings":
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









# Setup Binary Folder #
```
mkdir /usr/local/bin
sudo chown -R $(whoami) /usr/local/bin
```


# SFDC Dev Tools #


##### Install ant:
1. Install [Homebrew](https://brew.sh/)
2. Install ant: brew install ant
3. Download [Force Migration Tool](https://developer.salesforce.com/docs/atlas.en-us.daas.meta/daas/forcemigrationtool_install.htm)
4. Unzip Force Migration Tool and copy ant-salesforce.jar to: /opt/homebrew/Cellar/ant/1.10.9/libexec/lib



##### Install force-cli:
1. Install [force-cli](https://force-cli.herokuapp.com/)

##### Install fforce:
*************ADD GIT LINK HERE****************






1. git clone [Force-Actions](https://github.com/shabazfarooq/Force-Actions) to  ~/Library/Application Support/Sublime Text 3/Packages
2. SFDC Syntax Highlighting: git clone [SFDC-Syntax](https://github.com/shabazfarooq/SFDC-Syntax) to ~/Library/Application Support/Sublime Text 3/Packages/

##### Salesforce tools (not directly sublime related)
1. Install [create-force-login](https://github.com/shabazfarooq/force-login-setup) to /usr/local/bin
(this contains build.xml and package.xml, add them to the parent sfdc-directory)
2. Install [force-cli](http://force-cli.herokuapp.com/) to /usr/local/bin
(chmod +x the force file, copy it to force-original as well)


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









