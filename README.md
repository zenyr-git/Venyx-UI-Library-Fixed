# Venyx-UI-Library-Fixed

![Roblox UI Library](https://img.shields.io/badge/Roblox-UI%20Library-brightgreen) ![Lua](https://img.shields.io/badge/Language-Lua-blue)

A fixed version of the original Venyx UI library for Roblox.

## Installation

1. **Load the Library**:
   ```lua
   local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/zenyr-git/Venyx-UI-Library-Fixed/refs/heads/main/source.lua"))()
   ```

2. **Create Library Instance**:
   ```lua
   local lib = library.new("My GUI Title")
   ```

## Usage Examples

### Adding Pages
```lua
local page1 = lib:addPage("Page 1", 5012539403) -- Icon ID is optional
```

### Adding Sections
```lua
local section1 = page1:addSection("Section 1")
```

### UI Components

#### Button
```lua
section1:addButton("Click Me", function(update)
    print("Button clicked")
    -- Dynamically update button text
    update("New Button Text")
end)
```

#### Toggle
```lua
section1:addToggle("Toggle Me", true, function(value, update)
    print("Toggle state:", value)
    -- Update toggle title and state
    update("Updated Toggle", false)
end)
```

#### Textbox
```lua
section1:addTextbox("Enter Text", "Default Value", function(text, enterPressed, update)
    print("Text input:", text, "Enter pressed:", enterPressed)
    -- Update textbox title and default value
    update("New Title", "New Default")
end)
```

#### Keybind
```lua
section1:addKeybind("Bind Key", Enum.KeyCode.E, function(update)
    print("Key pressed")
    -- Update keybind title
    update("New Keybind Title")
end, function(key, update)
    print("Key changed to:", key.KeyCode.Name)
end)
```

#### Color Picker
```lua
section1:addColorPicker("Pick Color", Color3.fromRGB(255, 0, 0), function(color, update)
    print("Selected color:", color)
    -- Update color picker title and color
    update("New Color Picker", Color3.fromRGB(0, 255, 0))
end)
```

#### Slider
```lua
section1:addSlider("Slide Me", 50, 0, 100, function(value, update)
    print("Slider value:", value)
    -- Update slider title and value
    update("Updated Slider", 75)
end)
```

#### Dropdown
```lua
section1:addDropdown("Select Option", {"Option1", "Option2", "Option3"}, function(selected, update)
    print("Selected option:", selected)
    -- Update dropdown title and options
    update("Updated Dropdown", {"NewOpt1", "NewOpt2", "NewOpt3"})
end)
```

### Notifications
```lua
lib:Notify("Notification Title", "This is a message", function(accepted)
    print("User accepted:", accepted)
end)
```

### Themes
```lua
-- Set custom theme colors
lib:setTheme("Background", Color3.fromRGB(30, 30, 30))
lib:setTheme("Accent", Color3.fromRGB(0, 162, 255))
```

### GUI Controls
```lua
-- Toggle GUI visibility
lib:toggle()

-- Destroy the library (cleanup)
lib:destroy()
```

## API Reference

### Library Methods
- `library.new(title)` - Creates a new library instance
- `lib:addPage(name, iconId?)` - Adds a new page (iconId optional)
- `lib:Notify(title, message, callback?)` - Shows notification
- `lib:setTheme(element, color)` - Sets theme color for UI element
- `lib:toggle()` - Toggles GUI visibility
- `lib:destroy()` - Cleans up and destroys the library

### Page Methods
- `page:addSection(name)` - Adds a section to the page

### Section Methods
- `section:addButton(text, callback)` - Adds clickable button
- `section:addToggle(text, default, callback)` - Adds toggle switch
- `section:addTextbox(text, default, callback)` - Adds text input
- `section:addKeybind(text, defaultKey, pressCallback, changeCallback)` - Adds keybind
- `section:addColorPicker(text, defaultColor, callback)` - Adds color picker
- `section:addSlider(text, default, min, max, callback)` - Adds slider
- `section:addDropdown(text, options, callback)` - Adds dropdown menu

### Update Functions
All component callbacks receive an `update` function as a parameter:
- `update(newTitle, newValue?)` - Updates component properties dynamically
