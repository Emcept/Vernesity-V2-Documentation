# Vernesity UI Library
## Made by Emmy#4846

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
Library:EnableKeySystem(<Title>, <Subtitle>, <Note>, <List of keys>)
```


## Creating a Window
```Lua
local Window = Library:Window(<Title>, <Subtitle>, <Theme (optional)>)
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
Window:Notify(<Title>, <Description>, <Arguments Table>, <Duration>, <Func>)
```
### The arguments in the table should be 0-2 strings or 0-2 numbers (if you want to use images instead of regular buttons)



Note: Notifications with 2 buttons will always return 'Button1' when the first button is pressed, and 'Button2' when the second button is pressed



#### For example, this would create a notification with 2 Buttons
```Lua
Window:Notify("Question", "Do you like this UI Library?", {"Yes", "No"}, 5, function(Text)
	if Text == "Yes" then print("Thank you!") else print(":(") end
end)
```
#### And this would create a notification with 1 ImageButton (you need to enter a valid ImageID)
```Lua
Window:Notify("Notification", "Description", {1234567}, 10, function() print("Button pressed") end)
```
#### This would just create a notification with no buttons
```Lua
Window:Notify("Notification", "Description", {}, 3)
```


## Creating Tabs
```Lua
local Tab = Window:Tab(<Tab Name>, <ImageID (optional)>)
```


## Creating Sections
```Lua
local Section = Tab:Section(<Section Name>)
```


## Creating Buttons
```Lua
local Button = Section:Button(<Button Name>, <Button Description>, <Function>)
```


## Creating Labels
```Lua
local Label = Section:Label(<Label Name>)
```


## Creating TextBoxes
```Lua
local TextBox = Section:TextBox(<TextBox Name>, <TextBox Description>, <Default Text>, <Function>)
```


## Creating Paragraphs
```Lua
local Paragraph = Section:Paragraph(<Text 1>, <Text 2>)
```
<br />

## Creating Interactables
```Lua
local Interactable = Section:Interactable(<Interactable Name>, <Interactable Description>, <Button Text>, <Function>)
```


## Creating Dropdowns
```Lua
local Dropdown = Section:Dropdown(<Dropdown Name>, <Dropdown List>, <Default Option>, <Function>)
```
### Adding a button inside of a Dropdown
```Lua
local DropdownButton = Dropdown:Button(<Button Name>)
```

## Creating Switches
```Lua
local Switch = Section:Switch(<Switch Name>, <Switch Description>, <Enabled (true/false)>, <Function>)
```


## Creating Toggles
```Lua
local Toggle = Section:Toggle(<Toggle Name>, <Toggle Description>, <Enabled (true/false)>, <Function>)
```


## Creating Sliders
```Lua
local Slider = Section:Slider(<Slider Name>, <Slider Description>, <Minimum Value>, <Maximum Value>, <Default Value>, <Function>)
```


## Creating ColorPickers
```Lua
local ColorPicker = Section:ColorPicker(<ColorPicker Name>, <ColorPicker Description>, <Default Color>, <Function>)
```


## Creating PlayerLists
```Lua
local PlayerList = Section:PlayerList(<PlayerList Name>, <Function>)
```


## Creating Keybinds
```Lua
local Keybind = Section:Keybind(<Keybind Name>, <Keybind Description>, <Default Keybind>, <Function>)
```





## Other Functions
<br /><br />
### Getting the Window's current theme
```Lua
local theme = Window:GetTheme()
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
Window:ChangeTheme(<theme>)
```
#### or
```Lua
Window:Edit("Title", "Subtitle", <theme>)
```


## Toggling the UI:
```Lua
Window:ToggleUI()
```

## Editing UI Elements:
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
	settingsSection:ColorPicker(i, "Changes "..i.."'s theme", v, function(color3)
		theme = Window:GetTheme()
		theme[i] = color3
		Window:ChangeTheme(theme)
	end)
end
```



### Other Useless Functions: :OnClose(<Function>), :OnMinimize(<Function>) and :OnThemeChanged(<Function>)
```Lua
Window:OnClose(function()
	print('Closed')
end)
Window:OnMinimize(function(state)
	print('Minimized:', state)
end)
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
local Slider = Section:Slider('WalkSpeed', 'Desc', 0, 100, 16, function(speed)
	game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = speed
end)
local Keybind = Section:Keybind('Keybind', 'Desc', 'F', function()
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
```
