local shoo = 1 - 600

if not boostActive then
    local LocalPlayer = game:GetService("Players").LocalPlayer
    local intens = shoo -- set speed boost
    local Humanoid = workspace.CurrentCamera.CameraSubject
    local boostActive = true

    vehicleloopspeed = game:GetService("RunService").Stepped:Connect(function()
        if Humanoid:IsA("Humanoid") then
            Humanoid.SeatPart:ApplyImpulse(Humanoid.SeatPart.CFrame.LookVector * Vector3.new(0, 0, intens))
        elseif Humanoid:IsA("BasePart") then
            Humanoid:ApplyImpulse(Humanoid.CFrame.LookVector * Vector3.new(0, 0, intens))
        end
    end)

    while boostActive do
        wait()
    end
end
