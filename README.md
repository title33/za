local intens = 600 -- set speed boost
local boostActive = true

local function applyImpulseToHumanoid(Humanoid, intens)
    if Humanoid:IsA("Humanoid") and Humanoid.SeatPart then
        Humanoid.SeatPart:ApplyImpulse(Humanoid.SeatPart.CFrame.LookVector * Vector3.new(0, 0, intens))
    elseif Humanoid:IsA("BasePart") then
        Humanoid:ApplyImpulse(Humanoid.CFrame.LookVector * Vector3.new(0, 0, intens))
    end
end

local vehicleLoopSpeed = game:GetService("RunService").Stepped:Connect(function()
    local localPlayer = game:GetService("Players").LocalPlayer
    local humanoid = localPlayer.Character and localPlayer.Character:FindFirstChildOfClass("Humanoid")

    if humanoid then
        applyImpulseToHumanoid(humanoid, intens)
    end
end)

while boostActive do
    wait()
end

vehicleLoopSpeed:Disconnect()
