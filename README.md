local function applySafeBoost(humanoid, baseSpeed, maxSpeed)
  if not humanoid:IsA("Humanoid") then
    return -- Exit if not a Humanoid
  end

  local seatPart = humanoid.SeatPart
  local currentSpeed = humanoid.MoveDirection.Magnitude

  local targetSpeed = math.min(currentSpeed + baseSpeed, maxSpeed) -- Limit speed increase with maxSpeed

  if seatPart then
    seatPart:ApplyImpulse(seatPart.CFrame.LookVector * Vector3.new(0, 0, targetSpeed - currentSpeed))
  else
    humanoid:ApplyImpulse(humanoid.CFrame.LookVector * Vector3.new(0, 0, targetSpeed - currentSpeed))
  end
end

local baseSpeed = 600 -- Adjust base speed for desired boost intensity
local maxSpeed = 1000 -- Set the maximum achievable speed (consider physics and gameplay balance)

local humanoid = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid")

if humanoid then
  applySafeBoost(humanoid, baseSpeed, maxSpeed)
end
