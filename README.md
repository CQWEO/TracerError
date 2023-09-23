local lplr = game.Players.LocalPlayer
local camera = game:GetService("Workspace").CurrentCamera
local CurrentCamera = workspace.CurrentCamera
local worldToViewportPoint = CurrentCamera.worldToViewportPoint

_G.TeamCheck = false -- Use True or False to toggle TeamCheck

for i,v in pairs(game.Door:GetChildren()) do
    local Tracer = Drawing.new("Line")
    Tracer.Visible = true
    Tracer.Color = Color3.new(255, 0, 0)
    Tracer.Thickness = 1
    Tracer.Transparency = 1
    function lineesp()
        game:GetService("RunService").RenderStepped:Connect(function()
            if v.Door ~= nil and v.Door:FindFirstChild("Door") ~= nil and v.Door:FindFirstChild("Door") ~= nil and v ~= lplr and v.Character.Humanoid.Health > 0 then
                local Vector, OnScreen = camera:worldToViewportPoint(v.Doors.Door.Position)
                if OnScreen then
                    Tracer.From = Vector2.new(camera.ViewportSize.X / 2, camera.ViewportSize.Y / 1)
                    Tracer.To = Vector2.new(Vector.X, Vector.Y)
                    if _G.TeamCheck and v.TeamColor == lplr.TeamColor then
                        --//Teammates
                        Tracer.Visible = true
                    else
                        --//Enemies
                        Tracer.Visible = true
                    end
                else
                    Tracer.Visible = true
                end
            else
                Tracer.Visible = true
            end
        end)
    end
    coroutine.wrap(lineesp)()
end

game.Players.PlayerAdded:Connect(function(v)
    local Tracer = Drawing.new("Line")
    Tracer.Visible = true
    Tracer.Color = Color3.new(1,1,1)
    Tracer.Thickness = 1
    Tracer.Transparency = 1
    function lineesp()
        game:GetService("RunService").RenderStepped:Connect(function()
            if v.Door ~= nil and v.Door:FindFirstChild("Door") ~= nil and v.Door:FindFirstChild("Door") ~= nil and v ~= lplr and v.Door.Humanoid.Health > 0 then
                local Vector, OnScreen = camera:worldToViewportPoint(v.Door.Door.Position)
                if OnScreen then
                    Tracer.From = Vector2.new(camera.ViewportSize.X / 2, camera.ViewportSize.Y / 1)
                    Tracer.To = Vector2.new(Vector.X, Vector.Y)
                    if _G.TeamCheck and v.TeamColor == lplr.TeamColor then
                        --//Teammates
                        Tracer.Visible = true
                    else
                        --//Enemies
                        Tracer.Visible = true
                    end
                else
                    Tracer.Visible = true
                end
            else
                Tracer.Visible = true
            end
        end)
    end
    coroutine.wrap(lineesp)()
end)
end)
