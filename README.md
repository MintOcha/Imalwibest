local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Sword PVP", "DarkTheme")
local Tab = Window:NewTab("Main")
local Section = Tab:NewSection("Op")
local plr = game.Players.LocalPlayer

local oldmt 
oldmt = hookmetamethod(game, "__index", function(self, index)
    if index == ("WalkSpeed" or "JumpPower") then
        return 16
    end 
    return oldmt(self, index)
end)

local function getclosestplayer(range)
    local closest = nil 
    local maxdist = math.huge 
    for i,v in pairs(game.Players:GetPlayers()) do 
        if v ~= plr and v.Character and (not v.Character:FindFirstChild("ForceField")) and v.Character:FindFirstChild("HumanoidRootPart") and v.Character:FindFirstChild("Humanoid").Health > 0 then 
            local mag = (v.Character.HumanoidRootPart.Position - plr.Character.HumanoidRootPart.Position).Magnitude
            if mag < maxdist and mag < range then 
                maxdist = mag 
                closest = v 
            end 
        end 
    end 
    return closest 
end 

Section:NewToggle("Kill Aura", "", function(ori)
ora = ori 
end)

Section:NewSlider("Kill Aura Range", "", 25, 1, function(qrs)
qtr = qrs 
end)

game:GetService("RunService").RenderStepped:Connect(function()
if ora and plr.Character:FindFirstChildOfClass("Tool") then
for i,v in pairs(getclosestplayer(qtr).Character:GetChildren()) do 
if v:IsA("BasePart") then 
plr.Character:FindFirstChildOfClass("Tool"):Activate()
firetouchinterest(plr.Character:FindFirstChildOfClass("Tool").Handle, v, 0)
wait()
firetouchinterest(plr.Character:FindFirstChildOfClass("Tool").Handle, v, 1)
end 
end 
end 
end)

Section:NewToggle("Reach", "", function(oo)
oop = oo 
while oop and task.wait() do 
pcall(function()
if plr.Character:FindFirstChildOfClass("Tool") then 
for i,v in pairs(getclosestplayer(porn).Character:GetChildren()) do 
if v:IsA("BasePart") then 
firetouchinterest(plr.Character:FindFirstChildOfClass("Tool").Handle, v, 0)
wait()
firetouchinterest(plr.Character:FindFirstChildOfClass("Tool").Handle, v, 1)
end 
end
end 
end) 
end 
end) 

Section:NewSlider("Reach Range", "", 25, 1, function(qpor)
porn = qpor 
end)

Section:NewToggle("Hitbox Extender", "", function(c)
    d = c 
    while d and task.wait() do 
        pcall(function()
            for i,v in pairs(game.Players:GetPlayers()) do 
                if v ~= plr and v.Character and v.Character:FindFirstChild("HumanoidRootPart") then 
                v.Character.HumanoidRootPart.Size = Vector3.new(pir, pir, pir)
                v.Character.HumanoidRootPart.Transparency = .8
                end 
            end
        end) 
    end 
end)

PlrSection:NewSlider("Hitbox Size", "", 1, 25, function(pqor)
pir = pqor 
end)

Section:NewToggle("AFK Farm Kills", "", function(a)
    b = a 
    while b and task.wait() do 
        pcall(function()
        for i,v in pairs(plr.Character:GetDescendants()) do 
            if v:IsA("BasePart") and v.CanCollide then 
                v.CanCollide = false 
            end 
        end 
        plr.Character.HumanoidRootPart.Velocity = Vector3.new(0,0,0)
        plr.Character:FindFirstChildOfClass("Tool"):Activate()
        if getclosestplayer(99e99) == nil then 
        game:GetService("TweenService"):Create(plr.Character.HumanoidRootPart, TweenInfo.new(1, Enum.EasingStyle.Linear), {CFrame = CFrame.new(0, 4, -0)}):Play()
        else 
        game:GetService("TweenService"):Create(plr.Character.HumanoidRootPart, TweenInfo.new((getclosestplayer(99e99).Character.HumanoidRootPart.Position - plr.Character.HumanoidRootPart.Position).Magnitude / 50, Enum.EasingStyle.Linear), {CFrame = getclosestplayer(99e99).Character.HumanoidRootPart.CFrame + getclosestplayer(99e99).Character.HumanoidRootPart.CFrame.lookVector * -2}):Play()
        end
        end)
    end 
end)

Section:NewToggle("Auto Equip Random Sword", "", function(q)
    r = q 
    while r and task.wait() do 
        for i,v in pairs(plr.Character:GetChildren()) do 
            if v:IsA("Tool") and (not string.find(v.Name, "Sword")) then 
                for o,k in pairs(plr.Backpack:GetChildren()) do 
                    if string.find(k.Name, "Sword") then 
                        plr.Character.Humanoid:EquipTool(k)
                    end 
                end
            elseif (not plr.Character:FindFirstChildOfClass("Tool")) then 
                for o,k in pairs(plr.Backpack:GetChildren()) do 
                    if string.find(k.Name, "Sword") then 
                        plr.Character.Humanoid:EquipTool(k)
                    end 
                end
            end 
        end 
    end 
end)
local Tab = Window:NewTab("Auto Kill")
local Section = Tab:NewSection("Kill")
Section:NewButton("Sword Fight Bot", "ButtonInfo", function()
game.StarterGui:SetCore("SendNotification", {
    Title = "Sword Bot";
    Text = "Turn X to Off/On"; -- what the text says (ofc)
    Duration = 10;
})


loadstring(game:HttpGet('https://raw.githubusercontent.com/yeerma/1/main/bot'))()
end)

Section:NewButton("Keyboard Mobile", "m", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/advxzivhsjjdhxhsidifvsh/mobkeyboard/main/main.txt", true))()
end)

Section:NewButton("Sword Fight Kill aura", "?", function()
--// Setting \\--
local range = 15
 
--// Variable \\--
local player = game:GetService("Players").LocalPlayer
 
--// Script \\--
game:GetService("RunService").RenderStepped:Connect(function()
    local p = game.Players:GetPlayers()
    for i = 2, #p do local v = p[i].Character
        if v and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and v:FindFirstChild("HumanoidRootPart") and player:DistanceFromCharacter(v.HumanoidRootPart.Position) <= range then
            local tool = player.Character and player.Character:FindFirstChildOfClass("Tool")
            if tool and tool:FindFirstChild("Handle") then
                tool:Activate()
                for i,v in next, v:GetChildren() do
                    if v:IsA("BasePart") then
                        firetouchinterest(tool.Handle,v,0)
                        firetouchinterest(tool.Handle,v,1)
                    end
                end
            end
        end
    end
end)
end)

local Tab = Window:NewTab("Misc")
local Section = Tab:NewSection("Local Player")
Section:NewSlider("WalkSpeed", "", 500, 16, function(oirq)
plr.Character.Humanoid.WalkSpeed = oirq 
end)

Section:NewSlider("JumpPower", "", 500, 50, function(roe)
plr.Character.Humanoid.JumpPower = roe 
end)
game.StarterGui:SetCore("SendNotification", {
    Title = "Sword fight";
    Text = "This script Hass Made By alwi Hub!"; -- what the text says (ofc)
    Duration = 10;
})
