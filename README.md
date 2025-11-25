# Roblox-worm-script
Script biến thành con sâu trong roblox
local Players = game:GetService("Players")

local function makePlayerWorm(player)
    local character = player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    
    humanoid.WalkSpeed = 35
    humanoid.JumpPower = 30
    humanoid.HipHeight = -2
    humanoid.BodyHeightScale = 0.3
    humanoid.BodyWidthScale = 1.5
    humanoid.BodyDepthScale = 3.0
    
    for _, part in pairs(character:GetChildren()) do
        if part:IsA("BasePart") then
            part.BrickColor = BrickColor.new("Bright green")
            part.Material = Enum.Material.SmoothPlastic
        end
    end
    
    humanoid.Died:Connect(function()
        wait(3)
        makePlayerWorm(player)
    end)
end

for _, player in pairs(Players:GetPlayers()) do
    makePlayerWorm(player)
end

Players.PlayerAdded:Connect(makePlayerWorm)
