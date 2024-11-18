# Health Pickup Demo
This project mainly focuses health pickup in Roblox game.<br>
There is also asid rain feature in the project to demo deduct the player's health to be heal by the Health Pickups.

# How to use it
Download the file and open in Roblox Studio

# Script for health pickup healing
```
local max_health = 100
local enabled_transparency = 0.4
local disabled_transparency = 0.9
local cooldown = 20

local healthPickupsFolder = workspace:WaitForChild("HealthPickups")
local healthPickups = healthPickupsFolder:GetChildren()

local function onTouchHealthPickup(otherPart, healthPickup)
	if healthPickup:GetAttribute("Enabled") then
		local character = otherPart.Parent
		local humanoid = character:FindFirstChildWhichIsA("Humanoid")
		if humanoid then
			humanoid.Health = max_health
			healthPickup.Transparency = disabled_transparency
			healthPickup:SetAttribute("Enabled", false)
			wait(cooldown)
			healthPickup.Transparency = enabled_transparency
			healthPickup:SetAttribute("Enabled", true)
		end
	end
end

for _, healthPickup in ipairs(healthPickups) do
	healthPickup:SetAttribute("Enabled", true)
	healthPickup.Touched:Connect(function(otherPart)
		onTouchHealthPickup(otherPart, healthPickup)
	end)
end
```
This **script** is stored in the **ServerScriptService** while the pre-created **Health Pickups** are stored in a folder in the **Workspace**
