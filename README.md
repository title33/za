shoo = 999

if not boostActive then
    local LocalPlayer = game:GetService("Players").LocalPlayer
    local intens = shoo --set speed boost
    local Humanoid = workspace.CurrentCamera.CameraSubject
    local direction = Humanoid.SeatPart.CFrame.LookVector

    vehicleloopspeed = game:GetService("RunService").Stepped:Connect(function()
        if Humanoid:IsA("Humanoid") then
            if direction == Vector3.new(0, 0, 1) then
                Humanoid.SeatPart:ApplyImpulse(Humanoid.SeatPart.CFrame.LookVector * Vector3.new(intens, 0, 0))
            else
                Humanoid.SeatPart:ApplyImpulse(Humanoid.SeatPart.CFrame.LookVector * Vector3.new(0, 0, 0))
            end
        elseif Humanoid:IsA("BasePart") then
            if direction == Vector3.new(0, 0, 1) then
                Humanoid:ApplyImpulse(Humanoid.CFrame.LookVector * Vector3.new(intens, 0, 0))
            else
                Humanoid:ApplyImpulse(Humanoid.CFrame.LookVector * Vector3.new(0, 0, 0))
            end
        end
    end)
    boostActive = true
end
