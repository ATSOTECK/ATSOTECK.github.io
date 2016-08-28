Distribution date 28 - August - 2016

--------------------------------------------------------------------------------
WARNING: VERY BROKEN PRE-ALPHA USE AT YOUR OWN RISK
--------------------------------------------------------------------------------

Don't use this for anything important, unless you like to live life on the edge.
Currently there is no error handling/reporting. Good luck.

Note that in this version open doesn't actually do anything.
If you bind cmd_load_test you can open the test.cpp file.
eg bind(cmd_loat_test, vk_t, vk_control, vk_shift)
control + shift + t will open test.cpp

--------------------------------------------------------------------------------
Instructions
--------------------------------------------------------------------------------

File Stuff:
control + s : save
control + o : open file
control + shift + o : reload the open document
control + shift + n : clear the document

Navigation:
mouse click : move the cursor
arrow keys : move the cursor
home : move the cursor to the begining of the line
end : move the cursor to the end of the line
control + home : move the cursor to the begining of the document
control + end : move the cursor to the end of the document
control + up : move the cursor up to the first blank line
control + down :  move the cursor down to the first blank line
control + space : set mark
control + m : swap the mark and the cursor
alt + m : move the cursor to the mark

Editing:
backspace/delete: what you would expect
return/enter : also what you would expect
tab : either a tab character or a configurable number of spaces (default is 4)
shift + delete : clear the line

Misc:
control + ~ : open the config file
control + alt + t : open the current theme
control + shift + r : reload the config file
control + ? : open this ReadMe.txt

--------------------------------------------------------------------------------
Customizing Qark
--------------------------------------------------------------------------------

Quark is configurable via lua.
The default location of the config file is "C:\Users\USER\Documents\_quark\quark_config.lua".
This can be changed by using setConfigDir(string dir), eg you could put the actual config file in dropbox and have it on many computers that way.
The default location for themes is "C:\Users\USER\Documents\_quark\themes".
The themes folder must be in whatever folder the config dir is set to.
Themes are lua files just like the main config file is. The themes have acces to all the same functions that the main config file has acces too.
It is recommended that you only use theme related functions though.
If there is an update function in the theme file it will not be called every update, unlike the main config file.

Built in globals:

--Modality
mode_edit
mode_command

--Keyboard
vk_a
vk_b
vk_c
vk_d
vk_e
vk_f
vk_g
vk_h
vk_i
vk_j
vk_k
vk_l
vk_m
vk_n
vk_o
vk_p
vk_q
vk_r
vk_s
vk_t
vk_u
vk_v
vk_w
vk_x
vk_y
vk_z
vk_0
vk_1
vk_2
vk_3
vk_4
vk_5
vk_6
vk_7
vk_8
vk_9
vk_escape
vk_LControl
vk_LShift
vk_LAlt
vk_LSystem --Left System key (eg windows key, command key)
vk_RControl
vk_RShift
vk_RAlt
vk_RSystem --Right System key (eg windows key, command key)
vk_menu
vk_LBracket
vk_RBracket
vk_semicolon
vk_comma
vk_period
vk_quote
vk_slash
vk_backslash
vk_tilde
vk_equal
vk_dash
vk_space
vk_return --Enter
vk_backspace
vk_tab
vk_pageUp
vk_pageDown
vk_end
vk_home
vk_insert
vk_delete
vk_add      -- '+' on the numpad
vk_subtract -- '-' on the numpad
vk_multiply -- '*' on the numpad
vk_divide   -- '/' on the numpad
vk_left
vk_right
vk_up
vk_down
vk_num0
vk_num1
vk_num2
vk_num3
vk_num4
vk_num5
vk_num6
vk_num7
vk_num8
vk_num9
vk_f1
vk_f2
vk_f3
vk_f4
vk_f5
vk_f6
vk_f7
vk_f8
vk_f9
vk_f10
vk_f11
vk_f12
vk_f13
vk_f14
vk_f15
vk_pause
KeyCount

vk_control --LControl or RControl
vk_shift   --LShift or RShift
vk_alt     --LAlt or RAlt

--Mouse
mb_left
mb_right
mb_middle
mb_x1
mb_x2
ButtonCount

--Bindable commands
cmd_print_foo --Prints "Foo" to the console

cmd_quit --Quits Quark

cmd_save --save file
cmd_load --open file
cmd_reload_open_document

cmd_seek_whitespace_up
cmd_seek_whitespace_down
cmd_seek_document_begin
cmd_seek_document_end
cmd_seek_line_begin
cmd_seek_line_end

cmd_set_mark
cmd_swap_cursor_and_mark
cmd_move_cursor_to_mark
cmd_toggle_mark_visibility

cmd_backspace
cmd_delete
cmd_clear_line
cmd_clear_document
cmd_tab
cmd_newline --Return/Enter

cmd_open_config   --Opens your config file
cmd_open_theme    --Open whatever the currently active theme is
cmd_reload_config --Will also reload the theme
cmd_load_help     --Opens this file

--Cursor
cursor_block
cursor_outline
cursor_underscore
cursor_line

--Line Highlight
highlight_line_number_area
highlight_code_area
highlight_both

--Misc
globalsCount   --The number of registered globals
functionsCount --The number of registered functions
commandsCount  --The number of bindable cammands

Built in functions:

debug(string str) Prints the given string to the console.
debugln(string str) Same as above but adds a "\n" to string.

--Input
isKeyDown(number key) Returns true if the key is down.
isKeyPressed(number key) Returns true when the key is pressed.
isKeyReleased(number key) Return true when the key is released.
isKeyTapped(number key, number time = 100) Returns true if the key is held for less than time. Time is in milliseconds.

isButtonDown(number button) Returns true if the mouse button "button" is down.

--Bindings
bind(number command, number key, number modifier_keys ...)
clearBindings() Clears all the keyboard bindings, even the default ones. Use this for a clean slate and no suprises.
setDefaultBindings() Sets the default bindings.

--Preferences
resetPreferences() Resets all preferences to their default settings.
reloadConfig() Reloads the config file.

setConfigDir(string dir) 

setFont(string fontName) Do not include the extension in the name.
setFontSize(number size)

useTabs(bool use) Use tabs, "\t", or spaces ' '.
setTabWidth(number width) How many spaces are in a tab.

showLineNumbers(bool show) Whether or not line numbers are shown.

setShowClock(bool show) Whether or not the time is shown in the bar.
setUseMilitaryTime(bool use) Whether or not to use military time.

setCursorType(number type) Valid types: cursor_line, cursor_block, cursor_outline, cursor_underscore. Defaults to cursor_line on invalid option.
setBlinkCursor(bool blink) Whether or not the cursor blinks.

setShowMark(bool show) Whether or not the mark is show. It is still used if set to false, just not drawn.
setShowFrame(bool show) Whether or not the frame around the code editor is shown. Defaults to true.
setShowLineHighlight(bool show) Whether or not the current line is highlighted.
setLineHighlightType(number type) Valid types highlight_line_number_area, highligh_code_area, highlight_both. Defaults to highlight_both on invalid option.

setUseMouseClick(bool use) Whether or not clicking the mouse button moves the cursor. Default is true.

setScrollSpeed(number speed) Sets the speed at which things scroll. The default is 100.

setWindowOpacity(number opacity) Min 0, max 255. This controls how opaque, or transparent, the window is. Default value is 255.
setFrameRateLimit(number fps)

setStartingWindowSize(number width, number height) Sets the size of the window at start. If either width or height are
    0 then they will be set to the default: width = 1024 and height = 600 and it will be maximized.
    Note that currently the window will NOT resize if you change this and reload. You will have to restart. The reason this was disabled is it was
    causing issues with reloading the preferences. When this issue is fixed the window will be able to resize on reload.

setStartMaximized(bool startMaximized) If true it will ignoret the starting size and maximize. If the window is restored down
    it will be set to the starting size.

--Theme related
For all r, g, and b: min 0, max 255
setTheme(string theme) The name only, do not include the extension.
setClearColor(number r, number g, number b)
setFrameColor(number r, number g, number b)
setBarColor(number r, number g, number b)
setBarTextColor(number r, number g, number b)
setTextColor(number r, number g, number b)
setCursorColor(number r, number g, number b)
setMarkColor(number r, number g, number b)
setCurrentCharColor(number r, number g, number b)
setLineNumberAreaColor(number r, number g, number b)
setLineNumberTextColor(number r, number g, number b)
setLineHighlightColor(number r, number g, number b)
setLineHighlightTextColor(number r, number g, number b)

--------------------------------------------------------------------------------
Binding
--------------------------------------------------------------------------------

Use the "bind" function.
bind(cmd_name, key, modifiers)

If cmd_name already has a binding it will be replaced.
If cmd_name and cmd_foo have the same keybinding the one that is first in the array will be called.

Likewise if cmd_foo binding is a subset of cmd_bar binding and is in front, the cmd_bar binding will never be executed.
Example:
bind(cmd_delete, vk_delete)
bind(cmd_clear_line, vk_delete, vk_control)
The second bind in the above example will never be executed. This will eventually be fixed.

You can also have an update function in the config to do custom stuff.

--------------------------------------------------------------------------------
Example config file
--------------------------------------------------------------------------------

useTabs(false)
setTabWidth(4)
showLineNumbers(true)

setShowClock(true)

setCursorType(cursor_line)
setBlinkCursor(true)

setWindowOpacity(240)
setFrameRateLimit(60)

setTheme("morning_joe")

bind(cmd_print_foo, vk_a, vk_control, vk_z)
bind(cmd_reload_config, vk_r, vk_control)

function dateSixMonthsFromNow()
    --imagine code here
end

function update()
    control = isKeyDown(vk_control)
    shift = isKeyDown(vk_shift)
    
    if control and shift then
        if isKeyPressed(vk_p) then
            resetPreferences()
            reloadConfig()
        end
    else if control then
        if isKeyDown(vk_h) then
            debugln("Hello World!")
        else if isKeyPressed(vk_m) then
            dateSixMonthsFromNow()
        end
    end
    
    --imagine more clever code here
    
end
