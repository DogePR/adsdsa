local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

OrionLib:MakeNotification({
	Name = "Delux#6666 Menu",
	Content = "Welcome To Skids! Have Fun!",
	Image = "rbxassetid://4483345998",
	Time = 5
})


local Window = OrionLib:MakeWindow({Name = "Delux#6666 Hub", HidePremium = false, SaveConfig = true, ConfigFolder = "Delux#6666"})

--Player Tab--


local PlayerTab = Window:MakeTab({
	Name = "Player",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local PlayerSection = PlayerTab:AddSection({
	Name = "Auto Farm Devil Fruit Started"
})


local PlayerSection = PlayerTab:AddSection({
	Name = "Discord: https://discord.gg/BPyJRUbPM3"
})


--Player Tab End--

--Settings Tab--

local SettingsTab = Window:MakeTab({
	Name = "Settings",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local SettingsSection = SettingsTab:AddSection({
	Name = "Settings"
})

SettingsSection:AddButton({
	Name = "Destroy UI",
	Callback = function()
        OrionLib:Destroy()
  	end    
})


OrionLib:Init() --UI Lib End
