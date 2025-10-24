# ✨ Samp UI Library 

## 📌 About
- this is a short-term project, If it gets any attention I'll do fixes and keep updating it
---

## ⁉️ Usage

### Loading the Library
```lua
local SampUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/obsyhub/Samp/refs/heads/main/UI"))()
```

### Creating a Window
```lua
local Window = SampUI:CreateWindow({
  Name = "Samp UI",
  Subtitle = "Modern UI Library",
  ToggleKey = Enum.KeyCode.RightShift,
  ToggleIcon = "rbxassetid://10723434711"
})
```

#### Window Configuration
- **Name** - Main title of the window (string)
- **Subtitle** - Subtitle text below the title (string, optional)
- **ToggleKey** - Keybind to toggle the UI visibility (KeyCode, default: RightShift)
- **ToggleIcon** - Icon for the minimized toggle button (string, optional)

---

## 📑 Window Methods

### Window Properties & Functions
```lua
-- Change window text
Window:SetTitle("New Title")
Window:SetSubtitle("New Subtitle")

-- Create a new tab
Window:CreateTab({ Name = "Tab Name", Icon = "rbxassetid://icon" })

-- Create notifications
Window:CreateNotification({
  Title = "Notification",
  Content = "This is a notification!",
  Duration = 3
})

-- Create dialogues
Window:CreateDialogue({
  Title = "Confirm Action",
  Content = "Are you sure you want to continue?",
  Buttons = {
    { Text = "Yes", Callback = function() print("Confirmed") end },
    { Text = "No", Callback = function() print("Cancelled") end }
  }
})
```

---

## 📂 Creating Tabs

### Basic Tab Creation
```lua
local Tab = Window:CreateTab({
  Name = "Main",
  Icon = "rbxassetid://10723434711"
})
```

### Available Icons
The library includes built-in Lucide icons:
- `Home` - rbxassetid://10723434711
- `Settings` - rbxassetid://10734950309
- `User` - rbxassetid://10747374131
- `Shield` - rbxassetid://10723407389
- `Zap` - rbxassetid://10747384394
- `Globe` - rbxassetid://10723386633
- `Star` - rbxassetid://10723424505
- `Box` - rbxassetid://10723346959

 you can also add some (luicide icons) by changing Icon = "rbxassetid://yourtextureid"

---

## 🎨 Tab Elements

### Section
```lua
Tab:AddParagraph({
  Title = "Section Title",
  Content = "This is some descriptive text that explains what this section does."
})
```

### Button
```lua
Tab:AddButton({
  Text = "Click Me",
  Callback = function()
    print("Button clicked!")
  end
})
```

### Toggle
```lua
Tab:AddToggle({
  Text = "Enable Feature",
  Default = false,
  Callback = function(Value)
    print("Toggle state:", Value)
  end
})
```

### Slider
```lua
Tab:AddSlider({
  Text = "Speed",
  Min = 0,
  Max = 100,
  Default = 50,
  Increment = 1,
  Callback = function(Value)
    print("Slider value:", Value)
  end
})
```

### Text Field
```lua
Tab:AddTextField({
  Text = "Username",
  Default = "",
  Callback = function(Value)
    print("Input:", Value)
  end
})
```

### Dropdown
```lua
Tab:AddDropdown({
  Text = "Select Option",
  Options = {"Option 1", "Option 2", "Option 3"},
  Default = "Option 1",
  Callback = function(Value)
    print("Selected:", Value)
  end
})
```

### Multi-Select Dropdown
```lua
Tab:AddMultiDropdown({
  Text = "Select Multiple",
  Options = {"Red", "Green", "Blue", "Yellow"},
  Default = {"Red", "Blue"},
  Callback = function(Selected)
    print("Selected items:", table.concat(Selected, ", "))
  end
})
```

### Color Picker
```lua
Tab:AddColorPicker({
  Text = "Pick Color",
  Default = Color3.fromRGB(255, 255, 255),
  Callback = function(Color)
    print("Selected color:", Color)
  end
})
```

---

## 🔔 Notifications

### Creating a Notification
```lua
Window:CreateNotification({
  Title = "Success!",
  Content = "Your action was completed successfully.",
  Duration = 5
})
```

#### Notification Configuration
- **Title** - Main heading (string)
- **Content** - Message content (string)
- **Duration** - How long to show in seconds (number, default: 3)

---

## 💬 Dialogues

### Creating a Dialogue
```lua
Window:CreateDialogue({
  Title = "Warning",
  Content = "This action cannot be undone. Continue?",
  Buttons = {
    {
      Text = "Confirm",
      Callback = function()
        print("Action confirmed")
      end
    },
    {
      Text = "Cancel",
      Callback = function()
        print("Action cancelled")
      end
    }
  }
})
```

#### Dialogue Configuration
- **Title** - Dialogue heading (string)
- **Content** - Main message (string)
- **Buttons** - Array of button configurations
  - **Text** - Button label (string)
  - **Callback** - Function to execute (function, optional)

---

## 🎯 Complete Example

```lua
local SampUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/obsyhub/Samp/refs/heads/main/UI"))()

-- Create Window
local Window = SampUI:CreateWindow({
  Name = "My Script Hub",
  Subtitle = "Version 1.0",
  ToggleKey = Enum.KeyCode.RightControl
})

-- Create Main Tab
local MainTab = Window:CreateTab({
  Name = "Main",
  Icon = "rbxassetid://10723434711"
})

-- Add Section
MainTab:AddParagraph({
  Title = "Welcome!",
  Content = "Thanks for using this script. Configure your settings below."
})

-- Add Toggle
local FlyToggle = MainTab:AddToggle({
  Text = "Enable Flight",
  Default = false,
  Callback = function(Value)
    if Value then
      print("Flight enabled")
    else
      print("Flight disabled")
    end
  end
})

-- Add Slider
MainTab:AddSlider({
  Text = "Flight Speed",
  Min = 1,
  Max = 10,
  Default = 5,
  Increment = 0.5,
  Callback = function(Value)
    print("Speed set to:", Value)
  end
})

-- Add Button
MainTab:AddButton({
  Text = "Reset Character",
  Callback = function()
    game.Players.LocalPlayer.Character.Humanoid.Health = 0
  end
})

-- Create Settings Tab
local SettingsTab = Window:CreateTab({
  Name = "Settings",
  Icon = "rbxassetid://10734950309"
})

-- Add Dropdown
SettingsTab:AddDropdown({
  Text = "Theme",
  Options = {"Dark", "Light", "Blue", "Purple"},
  Default = "Dark",
  Callback = function(Value)
    print("Theme changed to:", Value)
  end
})

-- Add Color Picker
SettingsTab:AddColorPicker({
  Text = "Accent Color",
  Default = Color3.fromRGB(100, 150, 255),
  Callback = function(Color)
    print("Accent color changed")
  end
})

-- Show a notification
Window:CreateNotification({
  Title = "Script Loaded",
  Content = "All features are ready to use!",
  Duration = 5
})
```

---


## 🐛 Known Issues

skidding , insisting on not using your brain , being a dumbass


---

## 🔗 Links

- Repository: [this one lol]
- Documentation: [none atm]
- Support: [@real_obsy discord]

---

** Used chatgpt to create the readme **
