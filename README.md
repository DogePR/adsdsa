local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

OrionLib:MakeNotification({
	Name = "Delux#6666 Menu",
	Content = "Welcome Skids! Have Fun!",
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
PlayerSection:AddButton({
	Name = "Rejoin Server",
	Callback = function()
		local ts = game:GetService("TeleportService")

		local p = game:GetService("Players").LocalPlayer
		
		 
		
		ts:Teleport(game.PlaceId, p)
	  	end    
})

PlayerSection:AddButton({
	Name = "ServerHop (if u stuck)",
	Callback = function()
		OrionLib:MakeNotification({
			Name = "Delux#6666 Menu",
			Content = "Please, Wait 5 seconds",
			Image = "rbxassetid://4483345998",
			Time = 5
		})
		Time = 5 -- seconds
		repeat wait() until game:IsLoaded()
		wait(Time)
		local PlaceID = game.PlaceId
		local AllIDs = {}
		local foundAnything = ""
		local actualHour = os.date("!*t").hour
		local Deleted = false
		function TPReturner()
		   local Site;
		   if foundAnything == "" then
			   Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
		   else
			   Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
		   end
		   local ID = ""
		   if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
			   foundAnything = Site.nextPageCursor
		   end
		   local num = 0;
		   for i,v in pairs(Site.data) do
			   local Possible = true
			   ID = tostring(v.id)
			   if tonumber(v.maxPlayers) > tonumber(v.playing) then
				   for _,Existing in pairs(AllIDs) do
					   if num ~= 0 then
						   if ID == tostring(Existing) then
							   Possible = false
						   end
					   else
						   if tonumber(actualHour) ~= tonumber(Existing) then
							   local delFile = pcall(function()
								   delfile("NotSameServers.json")
								   AllIDs = {}
								   table.insert(AllIDs, actualHour)
							   end)
						   end
					   end
					   num = num + 1
				   end
				   if Possible == true then
					   table.insert(AllIDs, ID)
					   wait()
					   pcall(function()
						   writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
						   wait()
						   game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
					   end)
					   wait(4)
				   end
			   end
		   end
		end
		
		function Teleport()
		   while wait() do
			   pcall(function()
				   TPReturner()
				   if foundAnything ~= "" then
					   TPReturner()
				   end
			   end)
		   end
		end
		
		-- If you'd like to use a script before server hopping (Like a Automatic Chest collector you can put the Teleport() after it collected everything.
		Teleport()  	end    
})


PlayerSection:AddButton({
	Name = "Clear inv (Takes Like 1-3 min)",
	Callback = function()
		local args = {
			[1] = "LoadFruit",
			[2] = "Chop-Chop"
		}
		
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		wait(1)
		
		game.Players.LocalPlayer.Character.Humanoid.Health = 0
		
		wait(5)
		
		local args = {
			[1] = "LoadFruit",
			[2] = "Revive-Revive"
		}
		
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		wait(1)
		
		game.Players.LocalPlayer.Character.Humanoid.Health = 0
		
		wait(5)
		
		local args = {
			[1] = "LoadFruit",
			[2] = "Kilo-Kilo"
		}
		
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		wait(1)
		
		game.Players.LocalPlayer.Character.Humanoid.Health = 0
		
		wait(6)
		
		local args = {
			[1] = "LoadFruit",
			[2] = "Diamond-Diamond"
		}
		
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		wait(1)
		
		game.Players.LocalPlayer.Character.Humanoid.Health = 0
		
		wait(5)
		
		local args = {
			[1] = "LoadFruit",
			[2] = "Smoke-Smoke"
		}
		
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		wait(1)
		game.Players.LocalPlayer.Character.Humanoid.Health = 0
wait(2)
	  	end    
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

--Settings End--

OrionLib:Init() --UI Lib End
