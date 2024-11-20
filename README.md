# Health Pickup Demo
This project mainly focuses on health pickup in Roblox game.<br>
There is also an acid rain feature in the project to demo deduct the player's health to be healed by the Health Pickups.

# How to use it
Download the file and open it in Roblox Studio

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

- Healing script in ServerScriptService<br>
![image](https://github.com/user-attachments/assets/14f35dbd-b886-4f56-8640-9de35ed86211)

- Health Pickups folder with Health Pickups in Workspace<br>
![image](https://github.com/user-attachments/assets/75f3a6e6-c3e3-4feb-bb9d-b1c0c786f631)

# Object Model
HealthPickup:<br>
![image](https://github.com/user-attachments/assets/4edf0d3a-d3e7-42dd-92f2-4ea082203d89)







