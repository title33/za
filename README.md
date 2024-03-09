shoo = 1-999

if not boostActive then
        local LocalPlayer = game:GetService("Players").LocalPlayer
        local intens = shoo --set speed boost
        local Humanoid = workspace.CurrentCamera.CameraSubject

        vehicleloopspeed = game:GetService("RunService").Stepped:Connect(function()
            if Humanoid:IsA("Humanoid") then
                Humanoid.SeatPart:ApplyImpulse(Humanoid.SeatPart.CFrame.LookVector * Vector3.new(intens, intens, intens))
            elseif Humanoid:IsA("BasePart") then
                Humanoid:ApplyImpulse(Humanoid.CFrame.LookVector * Vector3.new(intens, intens, intens))
            end
        end)
        boostActive = true
    end
