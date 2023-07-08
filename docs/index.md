# Vernesity UI Library
## Made by Emmy (Discord: emcept)

## Latest update: Added Command Bar

## Features:
 - Resizable
 - Minimizable
 - Many elements
 - Key system (don't expect it to be super secure though)
 - Search function
 - All elements are editable (except for Notifications)
 - Ability to change themes
 - Easy to use
 - Much, much more


## Getting Loadstring
```Lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Emcept/Vernesity-V2/main/source.lua"))()
```

## Adding Key System
```Lua
Library:EnableKeySystem(<Title (string)>, <Subtitle (string)>, <Note (string)>, <List of keys (table)>)
```


## Creating a Window
```Lua
local Window = Library:Window(<Title (string)>, <Subtitle (string)>, <Theme (optional)  (string/table)>)
```


### Themes:
> DarkTheme  
> GrayTheme  
> LightTheme  
> BlueTheme  
> PurpleTheme  
> RedTheme   



## Creating Notifications
```Lua
Window:Notify(<Title (string)>, <Description (string)>, <Arguments (table)>, <Duration (number)>, <Callback (function)>)
```
### The values in the table should be 0-2 strings or 0-2 numbers (if you want to use images instead of regular buttons)



Notifications with 2 image buttons will always return 'Button1' when the first button is pressed, and 'Button2' when the second button is pressed



#### For example, this would create a notification with 2 Buttons
```Lua
Window:Notify("Question", "Do you like this UI Library?", {"Yes", "No"}, 5, function(Text)
	if Text == "Yes" then
		print("Thank you!")
	else
		print(":(")
	end
end)
```
#### And this would create a notification with 1 ImageButton (you need to enter a valid ImageID)
```Lua
Window:Notify("Notification", "Description", {1234567}, 10, function()
	print("Button pressed")
end)
```
#### This would just create a notification with no buttons
```Lua
Window:Notify("Notification", "Description", {}, 3)
```


## Creating Tabs
```Lua
local Tab = Window:Tab(<Tab Name (string)>, <ImageID (optional) (number)>)
```


## Creating Sections
```Lua
local Section = Tab:Section(<Section Name (string)>)
```


## Creating Buttons
```Lua
local Button = Section:Button(<Button Name (string)>, <Button Description (string)>, <Function (function)>)
```


## Creating Labels
```Lua
local Label = Section:Label(<Label Name (string)>)
```


## Creating TextBoxes
```Lua
local TextBox = Section:TextBox(<TextBox Name (string)>, <TextBox Description (string)>, <Default Text (string)>, <Function (function)>)
```
### Getting the TextBox's current text
```Lua
print(TextBox:GetText())
```

## Creating Paragraphs
```Lua
local Paragraph = Section:Paragraph(<Text 1 (string)>, <Text 2 (string)>)
```


## Creating Interactables
```Lua
local Interactable = Section:Interactable(<Interactable Name (string)>, <Interactable Description (string)>, <Button Text (string)>, <Function (function)>)
```


## Creating Dropdowns
```Lua
local Dropdown = Section:Dropdown(<Dropdown Name (string)>, <Dropdown List (table)>, <Default Option (string)>, <Function (function)>)
```
### Adding a button inside of a Dropdown
```Lua
local DropdownButton = Dropdown:Button(<Button Name (string)>)
```

## Creating Switches
```Lua
local Switch = Section:Switch(<Switch Name (string)>, <Switch Description (string)>, <Enabled (true/false)>, <Function (function)>)
```
### Checking if a switch is toggled (returns true if it's turned on)
```Lua
print(tostring(Switch:IsToggled()))
```

## Creating Toggles
```Lua
local Toggle = Section:Toggle(<Toggle Name (string)>, <Toggle Description (string)>, <Enabled (true/false)>, <Function (function)>)
```
### Checking if a toggled is toggled (returns true if it's turned on)
```Lua
print(tostring(Toggle:IsToggled()))
```

## Creating Sliders
```Lua
local Slider = Section:Slider(<Slider Name (string)>, <Slider Description (string)>, <Minimum Value (number)>, <Maximum Value (number)>, <Default Value (number)>, <Function (function)>)
```
### Getting a slider's current value
```Lua
print(Slider:GetValue())
```

## Creating ColorPickers
```Lua
local ColorPicker = Section:ColorPicker(<ColorPicker Name (string)>, <ColorPicker Description (string)>, <Default Color (Color3)>, <Function (function)>)
```


## Creating PlayerLists
```Lua
local PlayerList = Section:PlayerList(<PlayerList Name (string)>, <Function (function)>)
```


## Creating Keybinds
```Lua
local Keybind = Section:Keybind(<Keybind Name (string)>, <Keybind Description (string)>, <Default Keybind (string)>, <Function (function)>)
```


## Adding CommandBar
```Lua
local CommandBar = Window:CommandBar(<CommandBar Name (string)>, <Default Prefix (string)>)
```
### Getting all commands
```Lua
local Commands = CommandBar:GetCommands()
```
### Getting the current prefix
```Lua
local Prefix = CommandBar:GetPrefix()
```
### Changing the prefix
```Lua
CommandBar:ChangePrefix("-")
```
### Adding commands
```Lua
local Command1 = CommandBar:AddCommand(<Names (table)>, <Arguments (table)>, <Description (string)>, <Function (function)>)
```




## Other Functions

### Getting the Window's current theme
```Lua
local theme = Window:GetTheme()
```

### Minimizing/Unminimizing a Window/CommandBar
```Lua
Window:Minimize()
Window:Unminimize()
CommandBar:Minimize()
CommandBar:Unminimize()
```


### Adding themes
#### There are 2 ways to add themes:
```Lua
local Window = Library:Window("Title", "Subtitle", {
	TextColor = Color3.fromRGB(240, 240, 240),
	WindowColor = Color3.fromRGB(48, 75, 45),
	TabColor = Color3.fromRGB(56, 88, 53),
	ElementColor = Color3.fromRGB(69, 107, 65),
	SecondaryElementColor = Color3.fromRGB(96, 175, 87)
})
```
#### or
```Lua
Library:AddTheme("GreenTheme", {{
	TextColor = Color3.fromRGB(240, 240, 240),
	WindowColor = Color3.fromRGB(48, 75, 45),
	TabColor = Color3.fromRGB(56, 88, 53),
	ElementColor = Color3.fromRGB(69, 107, 65),
	SecondaryElementColor = Color3.fromRGB(96, 175, 87)
})
local Window = Library:Window("Title", "Subtitle", "GreenTheme")
```

### If you want to change the theme, there are also 2 ways to do it:
```Lua
Window:ChangeTheme(<Theme (string/table)>)
```
#### or
```Lua
Window:Edit("Title", "Subtitle", <Theme (string/table)>)
```


## Toggling the Window/CommandBar UI:
```Lua
Window:ToggleUI()
CommandBar:ToggleUI()
```

## Editing UI Elements: (you can edit any UI element, except for notifications)
```Lua
<Element>:Edit(<New Arguments>)
```
### Example:
```Lua
local Window = Library:Window("Title", "Subtitle", "DarkTheme")
Window:Edit("New Title", "New Subtitle", "PurpleTheme")
```



## Removing UI Elements:
```Lua
<Element>:Remove()
```
### Example:
```Lua
local Window = Library:Window("Title", "Subtitle", "DarkTheme")
Window:Remove()
```




### And here's the code which will help you add a fully customizable UI
```Lua
local theme = Window:GetTheme()
for i, v in pairs(theme) do
	local ThemeColorPicker = SettingsSection:ColorPicker(i, "Changes "..i.."'s Theme", v, function(color3)
		theme = Window:GetTheme()
		theme[i] = color3
		Window:ChangeTheme(theme)
	end)
	Window:OnThemeChanged(function()
		theme = Window:GetTheme()
		ThemeColorPicker:Edit(i, "Changes "..i.."'s Theme", theme[i], function(color3)
			theme[i] = color3
			Window:ChangeTheme(theme)
		end)
	end)
end
```



### Other Useless Functions: :OnClose(<Function>), :OnMinimize(<Function>), :OnThemeChanged(<Function>) and <Element>:GetElement()
```Lua
Window:OnClose(function()
	print('Window closed')
end)
Window:OnMinimize(function(state)
	print('Window minimized:', state)
end)
CommandBar:OnClose(function()
	print('CommandBar closed')
end)
CommandBar:OnMinimize(function(state)
	print('CommandBar minimized:', state)
end)
Window:OnThemeChanged(function()
	print("The theme had been changed.")
end)
print(Window:GetElement().Name)
```

	
	
	
## EXAMPLE CODE:
```Lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Emcept/Vernesity-V2/main/source.lua"))()
Library:EnableKeySystem('Title', 'Key System', 'Note here', {'1234'})
local Window = Library:Window('Vernesity', 'Game Name', 'DarkTheme')
local Tab = Window:Tab('Tab 1')
local Tab2 = Window:Tab('Tab 2', 12856048393)
local Section = Tab:Section('Main')
local Button = Section:Button('Button', 'Desc', function()
	print('Clicked')
end)
local Label = Section:Label('Label')
local Paragraph = Section:Paragraph('Text 1', 'Text 2')
local TextBox = Section:TextBox('TextBox', 'Desc', 'Type here...', function(text)
	print('You typed:', text)
end)
local Interactable = Section:Interactable('Interactable', 'Desc', 'Click Me!', function()
	print('Clicked!')
end)
local Dropdown = Section:Dropdown('Dropdown', {'Option 1', 'Option 2'}, 'Select...', function(selectedOption)
	print(selectedOption)
end)
local Switch = Section:Switch('Switch', 'Desc', true, function(state)
	if state then
		print('On')
	else
		print('Off')
	end
end)
local Toggle = Section:Toggle('Toggle', 'Desc', true, function(state)
	if state then
		print('On')
	else
		print('Off')
	end
end)
local Slider = Section:Slider('WalkSpeed Slider', 'Desc', 0, 100, 16, function(speed)
	game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = speed
end)
local Keybind = Section:Keybind('Keybind - Toggle UI', 'Desc', 'F', function()
	Window:ToggleUI()
end)

Window:Notify('Question', 'Do you like this UI Library?', {'Yes', 'No'}, 5, function(Text)
	if Text == 'Yes' then
		print('Yay! :D')
	else
		print('Not yay :(')
	end
end)

local SettingsSection = Tab2:Section('Settings')

local theme = Window:GetTheme()
for i, v in pairs(theme) do
	local ThemeColorPicker = SettingsSection:ColorPicker(i, "Changes "..i.."'s Theme", v, function(color3)
		theme = Window:GetTheme()
		theme[i] = color3
		Window:ChangeTheme(theme)
	end)
	Window:OnThemeChanged(function()
		theme = Window:GetTheme()
		ThemeColorPicker:Edit(i, "Changes "..i.."'s Theme", theme[i], function(color3)
			theme[i] = color3
			Window:ChangeTheme(theme)
		end)
	end)
end

Window:OnClose(function()
	print('Closed')
end)
Window:OnMinimize(function(state)
	print('Minimized:', state)
end)
Window:OnThemeChanged(function()
	print("The theme had been changed.")
end)
local PlayerList = Section:PlayerList('PlayerList', function(plr)
	print("Selected player:", plr)
end)

local CommandBarUI = Window:CommandBar('Name here', ';')
CommandBarUI:AddCommand({'print'}, {'string'}, 'Prints a string.', function(str)
	print(str)
end)
CommandBarUI:AddCommand({'addnumbers'}, {'numbers'}, 'Adds numbers together.', function(numbers)
	local totalSum = 0
	for number in numbers:gmatch("%d+") do
		totalSum = totalSum + tonumber(number)
	end
	print(totalSum)
end)
```
