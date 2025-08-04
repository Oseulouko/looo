local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local StarterGui = game:GetService("StarterGui")

local raridades = {"Raro", "Lendário", "Mítico", "Cósmico", "Especial"}

local ativado = false

local function checarRaridade(name)
    for _, r in ipairs(raridades) do
        if name:find(r) then
            return true
        end
    end
    return false
end

local function autoSteal()
    for _, pl in ipairs(Players:GetPlayers()) do
        if pl ~= LocalPlayer and pl.Character then
            for _, item in ipairs(pl.Character:GetChildren()) do
                if item:IsA("Tool") and checarRaridade(item.Name) then
                    local handle = item:FindFirstChild("Handle")
                    if handle and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                        LocalPlayer.Character:PivotTo(CFrame.new(handle.Position + Vector3.new(0, 2, 0)))
                        firetouchinterest(LocalPlayer.Character.HumanoidRootPart, handle, 0)
                        firetouchinterest(LocalPlayer.Character.HumanoidRootPart, handle, 1)
                        task.wait(0.5)
                    end
                end
            end
        end
    end
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "AutoStealGui"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = game:GetService("CoreGui")

local ToggleButton = Instance.new("TextButton")
ToggleButton.Size = UDim2.new(0, 140, 0, 50)
ToggleButton.Position = UDim2.new(0.5, -70, 1, -160)
ToggleButton.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
ToggleButton.TextColor3 = Color3.new(1, 1, 1)
ToggleButton.Font = Enum.Font.SourceSansBold
ToggleButton.TextSize = 20
ToggleButton.Text = "Auto Steal: OFF"
ToggleButton.Parent = ScreenGui

ToggleButton.MouseButton1Click:Connect(function()
    ativado = not ativado
    ToggleButton.Text = "Auto Steal: " .. (ativado and "ON" or "OFF")
end)

while true do
    if ativado then
        pcall(autoSteal)
    end
    task.wait(2)
end
