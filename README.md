
# Jump to #

- [Install Chrome](#Install-Chrome)
- [System Preferences](#System-Preferences)
- [Setup Finder](#Setup-Finder)
- [Hammerspoon](#Hammerspoon)
- [Karabiner Elements](#Karabiner-Elements)
- [Iterm2](#Iterm2)
- [App Store Apps](#AppStoreApps)
- [MonitorControl](#MonitorControl)
- [Homebrew](#Homebrew)
- [Obsidian](#Obsidian)
- [Setup GIT](#Setup-Git)
- [QMK (Keyboard)](#QMK)
- [VS Code](#VS-Code)

---

- [BetterTouchTool](#BetterTouchTool)
- [Sublime Text](#Sublime-Text)
- [Setup Binary Folder](#Setup-Binary-Folder)
- [SFDC Dev Tools](#SFDC-Dev-Tools)







# Install Chrome #
Download and install Chrome.
Sign in, all extensions available from the chrome app store will automatically install.While non-app store extensions will need to be installed manually

Install extensions:
1. [SFDC Chrome Shortcuts](https://github.com/shabazfarooq/SFDC-Shortcuts-Chrome)

Extensions that will transfer over:
1. [Duplicate Tab Shortcut Key](https://chrome.google.com/webstore/detail/duplicate-tab-shortcut/klehggjefofgiajjfpoebdidnpjmljhb/related?hl=en)
(Remove the shortcut for "Popup")
2. [Tab to Window/Popup - Keyboard Shortcut](https://chrome.google.com/webstore/detail/tab-to-windowpopup-keyboa/adbkphmimfcaeonicpmamfddbbnphikh/related?hl=en)
4. Night Theme - Dark Mode





# System Preferences #

##### Appearance >
- "Appearance": Dark
- "Show scroll bars": Always

##### Desktop & Dock >
- "Default web browser": Chrome
- "Size": small-ish
- "Magnification": min-ish
- "Minimize windows into applicaiton icon"
- "Automatically hide and show the Dock"
- uncheck "Show recent applicaitons in Dock"

##### Keyboard >
- "Key Repeat": Fast
- "Delay Unil Repeat": Short

##### Mouse >
- "Tracking speed": adjust to preference

##### Trackpad >
- "Tap to click"
- To Enable Three Finger Drag: Accessibility > Pointer Control > Trackpad Options... > Enable "User trackpad for dragging" > three finger drag





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








# Karabiner Elements #
1. Download and install
2. Open Karabiner-Elements and go to UI tab > (uncheck) Show icon in menu bar
3. Noridic Mouse Swap:
	- Devices tab > enable (Note: Mouse icon) 2.4G Wireless receiver (Nordic)
	- Simple Modifications > (Note: Mouse icon) 2.4G Wireless receiver (Nordic):
 	- mouse button2 to mouse button4
	- mouse button4 to mouse button2
6. Create JSON file with code below to add arrow keys: .config/karabiner/assets/complex_modifications/arrows.json
7. Then go to "Complex Modifications" > Add predfined rule > select
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
2. Settings:
	- General > Closing >
 		- (Disable confirm quit) uncheck all items
	- Profile > Default > General >
 		- (Open new tabs in same dir) Working Directory: "Reuse previous sessions directory"
	- Keys > Key Bindings >
 		- Move Tab Right: CTRL+SHIFT+PAGE UP
   		- Move Tab Left: CTRL+SHIFT+PAGE DOWN
		- Previous Tab: CMD+OPTION+LEFT
  		- Next Tab: CMD+OPTION+RIGHT
 	- Apperance > Tabs >
 		- (Always show tab bar) select "Show tab bar even when there is only one tab"
		- (Dont stretch tab bars) unselect "Stetch tabs to fill bar"
3. Edit/Create .zshrc (if it doesn't work, create .bashrc or .bash_profile)
```
export PS1="%n: %~ > "
export CLICOLOR=1
export LSCOLORS=ExFxCxDxBxegedabagacad
export PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ;} history -n"

# Sublime alias
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"
```



# AppStoreApps #

App Store > (Bottom Left) click Shabaz Farooq >

1.  Capslocker
	- Dock Icon > Preferences:
	- check: Start at Login
	- uncheck: Use colored CapsLock status icon
	- check: reverse colors
2. Magnet
	- Dock Icon > Preferences:
 	- check: Synchronize settings via iCloud
  	- check: Add Mgnet to login items
   	- Commands >
   	- Left: ^2
   	- Right: ^3
   	- Maximize: ^1
4. Xcode
5. Numbers
6. Pages
7. Keynote

# MonitorControl #
1. Install [MonitorControl](https://github.com/MonitorControl/MonitorControl/releases)
2. Open and enable permissions

# Homebrew #
1. Install [Homebrew](https://brew.sh/)

# Obsidian #
1. Install Obsidian

2. Create file with the following: ./Documents/Obsidian Vault/.obsidian/snippets/snippet1.css
```
:root {
  --green2: #37b6b4;
  --blue2: #61afee;
  --red2: #f17171;
  --yellow2: #ffc64c;
  --orange2: #fe8545;
  --purple2: #9d8dff;

  --active-file-color: #008cff;
}

body {
  --nav-item-color: #A0A0A0 !important;
  --nav-item-color: #DDD !important;
  --nav-item-background-active: #00000021 !important;
  --nav-item-padding: 5px;
  --nav-item-color-active: var(--active-file-color) !important;

  --inline-title-color: var(--active-file-color);
  --tab-text-color-focused-active-current: var(--active-file-color) !important;

  --inline-title-size: 23px;

  --h1-color: var(--red2);
  --h2-color: var(--red2);
  --h3-color: var(--red2);
  --h4-color: var(--red2);
  --h5-color: var(--red2);
  --h6-color: var(--red2);

  --h1-weight: 500;
  --h2-weight: 500;
  --h3-weight: 500;
  --h4-weight: 500;
  --h5-weight: 500;
  --h6-weight: 500;

  --bold-weight: 500;
  --bold-color: var(--purple2);
  --list-spacing: 5px;

  --nav-collapse-icon-color: #999;
  --nav-item-size: 14px;
}


/* Heading styling */
.mod-cm6 .cm-editor .HyperMD-header, 
.markdown-reading-view .markdown-preview-section :is(h1,h2,h3,h4,h5,h6) {
  padding-top: 30px !important;
}


/* Nav Vault Title */
.nav-folder-title-content:first-of-type {
  color: #555;
  padding-bottom: 5px;
  margin-bottom: 5px;
  text-transform: uppercase;
  
  display: block;
  width: 100%;
  border-bottom: 1px dotted #FFFFFF20;
}


/* Nav Folder Colors */
.nav-folder-title-content {
  font-weight: 500;
}


/* Table Styling */
th, td {
  padding: 17px !important;
}

th {  
  color: var(--green2) !important;
  background-color: #00000033 !important;
}

tr:nth-child(even) {
  background-color: Lightgreen !important;
  background-color: #FFFFFF09 !important;
}

```

3. Configure settings:

**Editor**
- *Disable* readable line length
- *Enable* Spellcheck
- Tab indent size = 2

**File Links**
- Default location for new notes: same folder as current file

**Appearance**
- accent color: #4C79CD
- theme: Atom (install)
- enable snippet1
- disable Show title bar

**Install community plugins:**
- Quick Switcher++
- Pane Relief
- Code Editor Shortcuts
- File Color
- Advanced New File
- Open In New Tab
- Sequence Hotkeys
- Chorded Hotkeys

**Set Hotkeys**
- Toggle checkbox status: blank
- Code Editor Shortcuts: Join Lines: blank
- Set as heading 5: cmd+shift+b
- Quick Switcher++: Open in standard mode: cmd+p
- Move line up: cmd+ctrl+up
- Move line down: cmd+ctrl+down
- Insert markdown link: blank
- Graph view: Open graph view: blank
- Delete paragraph: blank
- Delete current file: cmd+shift+backspace
- Command palette: Open command palette: cmd+shift+p
- Advanced new file: Create note in new tab: cmd+option+n


**Chorded hotkeys**
add cord: 
```
---

```

**Sequence Hotkeys**
- Toggle left sidebar: cmd+k cmd+j


**File Color**
- Blue: 92/124/255
- Folder Default: 221/221/221
- Green: 55/182/180
- Red: 248/84/84
- Yellow: 255/198/76
- Orange: 254/133/69
- Purple: 157/141/255
- Black: 84/84/84


# Setup GIT #
Note: using google authenticator app

1. Run commands:
```
git config --global user.name "Your Name"
git config --global user.email you@example.com
```
2. Go to github.com → Settings → Developer Settings → Personal Access Token → Tokens (classic) → Generate New Token → Fill out form → Generate Token → Copy the generated token
3. Open Keychain on mac > find github.com > change password from password to the token
4. Do a test commit of anything, and use the token instead of password


# QMK # 
1. Go to [personal qmk repo](https://github.com/shabazfarooq/qmk_firmware)
	- hit "Sync Fork"
 	- clone to home folder
2. Install [QMK](https://docs.qmk.fm/newbs_getting_started)
3. Install [QMK Toolbox](https://github.com/qmk/qmk_toolbox) (install from "Installer" not brew)
4. To make changes/flash the keymap:
	- Open qmk_firmware/personal_notes.txt for more details


# VS Code #
1. Install VS Code
2. Setup terminal command
  - Open VS Code > CMD + Shift + P > Shell Command: install 'code command in PATH
3.

---
# Changing below #
# Changing below #
# Changing below #
# Changing below #
# Changing below #
# Changing below #
# Changing below #
---


# BetterTouchTool #
1. Download and install BetterTouchTool
1. Settings > Basic: select "Launch BetterTouchTool on startup"
2. Settings > User Interface: unselect "Show Menubar icon"
1. Setup keyboard shortcuts:
![alt text](https://github.com/shabazfarooq/personal-mac-setup/blob/master/BTT_KB2.png "")









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
1. Install [force-cli](http://force-cli.herokuapp.com/) to /usr/local/bin
(chmod +x the force file)

##### Install fforce:
1. git clone [fforce](https://github.com/shabazfarooq/fforce-go) to /usr/local/bin
2. Sublime Text > Tools > Build System > New Build System (Save file as "fforce")
```
{
  "cmd": ["fforce build $folder $file $file_extension"],
  "shell": true
}
```
##### Sublime SFDC Syntax Highlighting:
1. git clone [SFDC-Syntax](https://github.com/shabazfarooq/SFDC-Syntax) to ~/Library/Application Support/Sublime Text 3/Packages/
2. Open a .cls and .pages file in Sublime, and on the bottom right select syntax, then select "Open all with current selection as..." and select SFDC-Syntax > Apex/VisualForce


