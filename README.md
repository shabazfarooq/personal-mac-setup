1. Enable three finger drag
	a) System Preferences -> Accessibility -> Trackpad -> ..

3. Setup finder:  a) new finder window shows: Shabaz b) tags: none c) setup sidebar favs d) advanced: “show all filename extensions”


2. Better touch tool a) take screenshot of all settings

3. Karabiner elements: a) add right command key + arrow keys b) get JSON file and note location: .config/karabiner/assets/complex_modifications/something.json

4. Hammer spoon a) instal it b) on the icon near clock click it, and select “open config” c) add the following code: down below


5. Iterm2: a)  



Apps:
Chrome
Sublime Text





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
