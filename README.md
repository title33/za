shoo = 1-999

if not boostActive then
    local LocalPlayer = game:GetService("Players").LocalPlayer
    local Humanoid = workspace.CurrentCamera.CameraSubject

    vehicleloopspeed = game:GetService("RunService").Stepped:Connect(function()
        if Humanoid:IsA("Humanoid") then
            local seatPart = Humanoid.SeatPart
            if seatPart then
                -- Apply impulse in the forward direction relative to the seat
                seatPart:ApplyImpulse(seatPart.CFrame.LookVector * Vector3.new(0, 0, shoo))
            end
        elseif Humanoid:IsA("BasePart") then
            -- Apply impulse in the forward direction relative to the car
            Humanoid:ApplyImpulse(Humanoid.CFrame.LookVector * Vector3.new(0, 0, shoo))
        end
    end)
    boostActive = true
end
