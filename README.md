local Players = game:GetService("Players")
local VirtualInputManager = game:GetService("VirtualInputManager")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local lp = Players.LocalPlayer

local BG_MAIN = Color3.fromRGB(5, 0, 8)
local ACCENT = Color3.fromRGB(255, 20, 40)

getgenv().AbuseActive = false
getgenv().SelectedSlot = Enum.KeyCode.Three

-- ========== GUI PRINCIPAL CON PESTAÑAS ==========
local ScreenGui = Instance.new("ScreenGui", game.CoreGui)
ScreenGui.Name = "WhiteDevilHub"

local MainFrame = Instance.new("Frame", ScreenGui)
MainFrame.Size = UDim2.new(0, 450, 0, 550)
MainFrame.Position = UDim2.new(0.5, -225, 0.5, -275)
MainFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
MainFrame.BackgroundTransparency = 0.1
MainFrame.BorderSizePixel = 0
Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 12)

local GlowBorder = Instance.new("Frame", MainFrame)
GlowBorder.Size = UDim2.new(1, 0, 1, 0)
GlowBorder.BackgroundTransparency = 1
GlowBorder.BorderSizePixel = 3
GlowBorder.BorderColor3 = ACCENT

local TitleBar = Instance.new("Frame", MainFrame)
TitleBar.Size = UDim2.new(1, 0, 0, 48)
TitleBar.BackgroundColor3 = Color3.fromRGB(20, 0, 10)
TitleBar.BackgroundTransparency = 0.5
TitleBar.BorderSizePixel = 0
Instance.new("UICorner", TitleBar).CornerRadius = UDim.new(0, 12)

local Title = Instance.new("TextLabel", TitleBar)
Title.Size = UDim2.new(1, -40, 1, 0)
Title.Position = UDim2.new(0, 12, 0, 0)
Title.Text = "☠ 改 白魔 HUB ☠"
Title.TextColor3 = ACCENT
Title.Font = Enum.Font.GothamBold
Title.TextSize = 18
Title.BackgroundTransparency = 1
Title.TextXAlignment = Enum.TextXAlignment.Left

local Subtitle = Instance.new("TextLabel", MainFrame)
Subtitle.Size = UDim2.new(1, 0, 0, 18)
Subtitle.Position = UDim2.new(0, 0, 0, 48)
Subtitle.Text = "⛧ MULTI-FUNCIONES ⛧"
Subtitle.TextColor3 = Color3.fromRGB(180, 20, 30)
Subtitle.Font = Enum.Font.Gotham
Subtitle.TextSize = 10
Subtitle.BackgroundTransparency = 1

local MinBtn = Instance.new("TextButton", TitleBar)
MinBtn.Size = UDim2.new(0, 32, 0, 32)
MinBtn.Position = UDim2.new(1, -42, 0, 8)
MinBtn.BackgroundColor3 = Color3.fromRGB(100, 0, 0)
MinBtn.Text = "🗕"
MinBtn.TextColor3 = Color3.new(1, 1, 1)
MinBtn.Font = Enum.Font.GothamBold
MinBtn.TextSize = 18
Instance.new("UICorner", MinBtn).CornerRadius = UDim.new(1, 0)

-- Panel de pestañas principales
local MainTabBar = Instance.new("Frame", MainFrame)
MainTabBar.Size = UDim2.new(1, 0, 0, 36)
MainTabBar.Position = UDim2.new(0, 0, 0, 66)
MainTabBar.BackgroundColor3 = Color3.fromRGB(10, 0, 5)
MainTabBar.BackgroundTransparency = 0.3
MainTabBar.BorderSizePixel = 0

local MainContentContainer = Instance.new("Frame", MainFrame)
MainContentContainer.Size = UDim2.new(1, 0, 1, -106)
MainContentContainer.Position = UDim2.new(0, 0, 0, 102)
MainContentContainer.BackgroundTransparency = 1

-- Pestañas principales
local TabAbusos = Instance.new("TextButton", MainTabBar)
TabAbusos.Size = UDim2.new(0, 130, 1, 0)
TabAbusos.Position = UDim2.new(0, 5, 0, 0)
TabAbusos.BackgroundColor3 = ACCENT
TabAbusos.Text = "🔥 ABUSOS"
TabAbusos.TextColor3 = Color3.new(1, 1, 1)
TabAbusos.Font = Enum.Font.GothamBold
TabAbusos.TextSize = 12
Instance.new("UICorner", TabAbusos).CornerRadius = UDim.new(0, 6)

local TabRedz = Instance.new("TextButton", MainTabBar)
TabRedz.Size = UDim2.new(0, 150, 1, 0)
TabRedz.Position = UDim2.new(0, 140, 0, 0)
TabRedz.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
TabRedz.Text = "🌀 REDZ HUB"
TabRedz.TextColor3 = Color3.new(1, 1, 1)
TabRedz.Font = Enum.Font.GothamBold
TabRedz.TextSize = 12
Instance.new("UICorner", TabRedz).CornerRadius = UDim.new(0, 6)

local TabInfo = Instance.new("TextButton", MainTabBar)
TabInfo.Size = UDim2.new(0, 110, 1, 0)
TabInfo.Position = UDim2.new(0, 295, 0, 0)
TabInfo.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
TabInfo.Text = "ℹ INFO"
TabInfo.TextColor3 = Color3.new(1, 1, 1)
TabInfo.Font = Enum.Font.GothamBold
TabInfo.TextSize = 12
Instance.new("UICorner", TabInfo).CornerRadius = UDim.new(0, 6)

local AbusosContent = Instance.new("ScrollingFrame", MainContentContainer)
AbusosContent.Size = UDim2.new(1, 0, 1, 0)
AbusosContent.BackgroundTransparency = 1
AbusosContent.BorderSizePixel = 0
AbusosContent.CanvasSize = UDim2.new(0, 0, 0, 350)
AbusosContent.ScrollBarThickness = 4
AbusosContent.Visible = true

local RedzContent = Instance.new("Frame", MainContentContainer)
RedzContent.Size = UDim2.new(1, 0, 1, 0)
RedzContent.BackgroundTransparency = 1
RedzContent.Visible = false

local InfoContent = Instance.new("Frame", MainContentContainer)
InfoContent.Size = UDim2.new(1, 0, 1, 0)
InfoContent.BackgroundTransparency = 1
InfoContent.Visible = false

-- Subpestañas REDZ HUB
local SubTabBar = Instance.new("Frame", RedzContent)
SubTabBar.Size = UDim2.new(1, 0, 0, 32)
SubTabBar.Position = UDim2.new(0, 0, 0, 0)
SubTabBar.BackgroundColor3 = Color3.fromRGB(15, 0, 8)
SubTabBar.BackgroundTransparency = 0.2
SubTabBar.BorderSizePixel = 0

local SubContentContainer = Instance.new("Frame", RedzContent)
SubContentContainer.Size = UDim2.new(1, 0, 1, -36)
SubContentContainer.Position = UDim2.new(0, 0, 0, 36)
SubContentContainer.BackgroundTransparency = 1

-- Función para crear botones en subpestañas
local function CreateButton(parent, text, yPos, bgColor, callback)
    local btn = Instance.new("TextButton", parent)
    btn.Size = UDim2.new(0.9, 0, 0, 36)
    btn.Position = UDim2.new(0.05, 0, 0, yPos)
    btn.BackgroundColor3 = bgColor
    btn.Text = text
    btn.TextColor3 = Color3.new(1, 1, 1)
    btn.Font = Enum.Font.GothamBold
    btn.TextSize = 12
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 6)
    btn.MouseButton1Click:Connect(callback)
    return btn
end

local function CreateSection(parent, title, yPos)
    local section = Instance.new("TextLabel", parent)
    section.Size = UDim2.new(0.95, 0, 0, 24)
    section.Position = UDim2.new(0.025, 0, 0, yPos)
    section.BackgroundColor3 = Color3.fromRGB(30, 0, 15)
    section.Text = "▸ " .. title .. " ◂"
    section.TextColor3 = ACCENT
    section.Font = Enum.Font.GothamBold
    section.TextSize = 13
    Instance.new("UICorner", section).CornerRadius = UDim.new(0, 4)
    return section
end

-- Crear subpestañas
local subTabs = {
    "FARMING", "QUESTS", "TRIALS", "RAIDS", "FISHING", "TELEPORT", "SHOP", "SETTINGS"
}

local subButtons = {}
local subFrames = {}

for i, tabName in ipairs(subTabs) do
    local btn = Instance.new("TextButton", SubTabBar)
    btn.Size = UDim2.new(0, 112, 1, 0)
    btn.Position = UDim2.new(0, (i-1) * 112 + 2, 0, 0)
    btn.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
    btn.Text = tabName
    btn.TextColor3 = Color3.new(1, 1, 1)
    btn.Font = Enum.Font.GothamBold
    btn.TextSize = 10
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 4)
    subButtons[tabName] = btn
    
    local frame = Instance.new("ScrollingFrame", SubContentContainer)
    frame.Size = UDim2.new(1, 0, 1, 0)
    frame.BackgroundTransparency = 1
    frame.BorderSizePixel = 0
    frame.CanvasSize = UDim2.new(0, 0, 0, 600)
    frame.ScrollBarThickness = 4
    frame.Visible = (i == 1)
    subFrames[tabName] = frame
    
    btn.MouseButton1Click:Connect(function()
        for _, f in pairs(subFrames) do f.Visible = false end
        for _, b in pairs(subButtons) do b.BackgroundColor3 = Color3.fromRGB(40, 0, 20) end
        frame.Visible = true
        btn.BackgroundColor3 = ACCENT
    end)
end

-- ==================== PESTAÑA FARMING ====================
local farmFrame = subFrames["FARMING"]
local yOff = 5

CreateSection(farmFrame, "AUTO FARM", yOff); yOff = yOff + 28
CreateButton(farmFrame, "▶ Auto Farm Level", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoFarm = not getgenv().AutoFarm
    if getgenv().AutoFarm then
        task.spawn(function()
            while getgenv().AutoFarm and game.Players.LocalPlayer.Character do
                pcall(function()
                    local level = game.Players.LocalPlayer.Data.Level.Value
                    -- Lógica de farm por nivel
                    task.wait(0.1)
                end)
                task.wait()
            end
        end)
    end
end); yOff = yOff + 42
CreateButton(farmFrame, "▶ Auto Farm Material", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoFarmMaterial = not getgenv().AutoFarmMaterial
end); yOff = yOff + 42
CreateButton(farmFrame, "▶ Auto Farm Bone", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().FarmBone = not getgenv().FarmBone
end); yOff = yOff + 42
CreateButton(farmFrame, "▶ Auto Farm Chest", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().FarmChest = not getgenv().FarmChest
end); yOff = yOff + 42
CreateButton(farmFrame, "▶ Auto Farm Boss", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoBoss = not getgenv().AutoBoss
end); yOff = yOff + 42
CreateButton(farmFrame, "▶ Auto Farm Elite Hunter", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoElitehunter = not getgenv().AutoElitehunter
end); yOff = yOff + 50

CreateSection(farmFrame, "MATERIALS", yOff); yOff = yOff + 28
local materials = {"Radioactive", "Mystic Droplet", "Magma Ore", "Angel Wings", "Leather", "Ectoplasm", "Scrap Metal", "Conjured Cocoa"}
for _, mat in ipairs(materials) do
    CreateButton(farmFrame, "Farm " .. mat, yOff, Color3.fromRGB(30, 0, 20), function()
        getgenv().SelectMaterial = mat
        getgenv().AutoFarmMaterial = true
    end); yOff = yOff + 38
end

-- ==================== PESTAÑA QUESTS ====================
local questFrame = subFrames["QUESTS"]
yOff = 5

CreateSection(questFrame, "QUESTS SEA 1-2-3", yOff); yOff = yOff + 28
CreateButton(questFrame, "▶ Auto Quest Sea 2", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoSecondSea = not getgenv().AutoSecondSea
end); yOff = yOff + 42
CreateButton(questFrame, "▶ Auto Quest Sea 3", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().ThirdSea = not getgenv().ThirdSea
end); yOff = yOff + 42
CreateButton(questFrame, "▶ Auto Quest Bartilo", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoBartilo = not getgenv().AutoBartilo
end); yOff = yOff + 50

CreateSection(questFrame, "SWORD QUESTS", yOff); yOff = yOff + 28
local swords = {"Saber", "Pole", "Saw", "Wardens", "Trident", "Longsword", "Gravity Blade", "Flail", "Rengoku", "Dragon Trident", "Twin Hooks", "Canvander", "Buddy", "Yama", "Tushita", "CDK"}
for _, sword in ipairs(swords) do
    CreateButton(questFrame, "Get " .. sword, yOff, Color3.fromRGB(30, 0, 20), function()
        getgenv()["Auto" .. sword:gsub(" ", "")] = not getgenv()["Auto" .. sword:gsub(" ", "")]
    end); yOff = yOff + 38
    if yOff > 500 then break end
end

-- ==================== PESTAÑA TRIALS ====================
local trialsFrame = subFrames["TRIALS"]
yOff = 5

CreateSection(trialsFrame, "RACE V4 TRIALS", yOff); yOff = yOff + 28
CreateButton(trialsFrame, "▶ Teleport To Top GreatTree", yOff, Color3.fromRGB(50, 0, 30), function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3030.39453125, 2280.6171875, -7320.18359375)
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Teleport To Temple Of Time", yOff, Color3.fromRGB(50, 0, 30), function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(28286.35546875, 14895.3017578125, 102.62469482421875)
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Teleport Lever Pull", yOff, Color3.fromRGB(50, 0, 30), function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(28575.181640625, 14936.6279296875, 72.31636810302734)
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Auto Race Door", yOff, Color3.fromRGB(50, 0, 30), function()
    local race = game.Players.LocalPlayer.Data.Race.Value
    local positions = {
        Human = CFrame.new(29221.822265625, 14890.9755859375, -205.99114990234375),
        Skypiea = CFrame.new(28960.158203125, 14919.6240234375, 235.03948974609375),
        Fishman = CFrame.new(28231.17578125, 14890.9755859375, -211.64173889160156),
        Cyborg = CFrame.new(28502.681640625, 14895.9755859375, -423.7279357910156),
        Ghoul = CFrame.new(28674.244140625, 14890.6767578125, 445.4310607910156),
        Mink = CFrame.new(29012.341796875, 14890.9755859375, -380.1492614746094)
    }
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = positions[race] or positions.Human
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Auto Trial V4", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoQuestRace = not getgenv().AutoQuestRace
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Auto Kill Trial Players", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoKillV4 = not getgenv().AutoKillV4
end); yOff = yOff + 50

CreateSection(trialsFrame, "HALLOW SCYTHE", yOff); yOff = yOff + 28
CreateButton(trialsFrame, "▶ Auto Hallow Scythe", yOff, Color3.fromRGB(30, 0, 20), function()
    getgenv().Hallow = not getgenv().Hallow
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Auto Pray", yOff, Color3.fromRGB(30, 0, 20), function()
    getgenv().Pray = not getgenv().Pray
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Auto Try Luck", yOff, Color3.fromRGB(30, 0, 20), function()
    getgenv().Trylux = not getgenv().Trylux
end); yOff = yOff + 50

CreateSection(trialsFrame, "KATAKURI", yOff); yOff = yOff + 28
CreateButton(trialsFrame, "▶ Farm Katakuri V1", yOff, Color3.fromRGB(30, 0, 20), function()
    getgenv().FarmCake = not getgenv().FarmCake
end); yOff = yOff + 42
CreateButton(trialsFrame, "▶ Farm Katakuri V2 (Dough King)", yOff, Color3.fromRGB(30, 0, 20), function()
    getgenv().Fullykatakuri = not getgenv().Fullykatakuri
end); yOff = yOff + 42

-- ==================== PESTAÑA RAIDS ====================
local raidsFrame = subFrames["RAIDS"]
yOff = 5

CreateSection(raidsFrame, "FRUIT RAIDS", yOff); yOff = yOff + 28
CreateButton(raidsFrame, "▶ Auto Buy Chip", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoBuyChip = not getgenv().AutoBuyChip
end); yOff = yOff + 42
CreateButton(raidsFrame, "▶ Auto Start Raid", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().StartRaid = not getgenv().StartRaid
end); yOff = yOff + 42
CreateButton(raidsFrame, "▶ Auto Farm Raid", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().Dungeon = not getgenv().Dungeon
end); yOff = yOff + 50

CreateSection(raidsFrame, "LAW RAID", yOff); yOff = yOff + 28
CreateButton(raidsFrame, "▶ Auto Buy Chip Law", yOff, Color3.fromRGB(30, 0, 20), function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward", "Microchip", "2")
end); yOff = yOff + 42
CreateButton(raidsFrame, "▶ Auto Start Law Raid", yOff, Color3.fromRGB(30, 0, 20), function()
    fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon.Button.Main.ClickDetector)
end); yOff = yOff + 42
CreateButton(raidsFrame, "▶ Auto Farm Law Raid", yOff, Color3.fromRGB(30, 0, 20), function()
    getgenv().AutoLawRaid = not getgenv().AutoLawRaid
end); yOff = yOff + 50

CreateSection(raidsFrame, "FRUIT STORE", yOff); yOff = yOff + 28
CreateButton(raidsFrame, "▶ Auto Store Fruits", yOff, Color3.fromRGB(30, 0, 20), function()
    getgenv().AutoStoreFruit = not getgenv().AutoStoreFruit
end); yOff = yOff + 42

-- ==================== PESTAÑA FISHING ====================
local fishingFrame = subFrames["FISHING"]
yOff = 5

CreateSection(fishingFrame, "AUTO FISHING", yOff); yOff = yOff + 28
CreateButton(fishingFrame, "▶ Auto Fishing", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoFishing = not getgenv().AutoFishing
    if getgenv().AutoFishing then
        task.spawn(function()
            while getgenv().AutoFishing do
                pcall(function()
                    local rod = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool")
                    if rod and rod:GetAttribute("ServerState") == "Biting" then
                        game:GetService("ReplicatedStorage").FishReplicated.FishingRequest:InvokeServer("Catching", true)
                        task.wait(0.1)
                        game:GetService("ReplicatedStorage").FishReplicated.FishingRequest:InvokeServer("Catch", 1)
                    end
                end)
                task.wait(0.5)
            end
        end)
    end
end); yOff = yOff + 50

CreateSection(fishingFrame, "RODS & BAITS", yOff); yOff = yOff + 28
local rods = {"Fishing Rod", "Gold Rod", "Shark Rod", "Shell Rod", "Treasure Rod"}
for _, rod in ipairs(rods) do
    CreateButton(fishingFrame, "Select " .. rod, yOff, Color3.fromRGB(30, 0, 20), function()
        getgenv().SelectedRod = rod
    end); yOff = yOff + 38
end

-- ==================== PESTAÑA TELEPORT ====================
local teleportFrame = subFrames["TELEPORT"]
yOff = 5

CreateSection(teleportFrame, "SEA TELEPORT", yOff); yOff = yOff + 28
CreateButton(teleportFrame, "▶ Teleport Sea 1", yOff, Color3.fromRGB(50, 0, 30), function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
end); yOff = yOff + 42
CreateButton(teleportFrame, "▶ Teleport Sea 2", yOff, Color3.fromRGB(50, 0, 30), function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
end); yOff = yOff + 42
CreateButton(teleportFrame, "▶ Teleport Sea 3", yOff, Color3.fromRGB(50, 0, 30), function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
end); yOff = yOff + 50

CreateSection(teleportFrame, "ISLAND TELEPORT", yOff); yOff = yOff + 28
local islands = {
    {"Pirate Village", CFrame.new(-1181.309, 4.751, 3803.546)},
    {"Desert", CFrame.new(944.158, 20.92, 4373.3)},
    {"Sky Island", CFrame.new(-4869.103, 733.461, -2667.018)},
    {"Hydra Island", CFrame.new(5291.249, 1005.443, 393.762)},
    {"Castle On Sea", CFrame.new(-5083.26, 314.606, -3175.673)},
    {"Great Tree", CFrame.new(2681.274, 1682.809, -7190.985)},
    {"Dragon Dojo", CFrame.new(5743.319, 1206.91, 936.011)}
}
for _, island in ipairs(islands) do
    CreateButton(teleportFrame, "Teleport " .. island[1], yOff, Color3.fromRGB(30, 0, 20), function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = island[2]
    end); yOff = yOff + 38
end

-- ==================== PESTAÑA SHOP ====================
local shopFrame = subFrames["SHOP"]
yOff = 5

CreateSection(shopFrame, "MELEE", yOff); yOff = yOff + 28
local melees = {"Black Leg ($150k)", "Electro ($550k)", "Water Kung Fu ($750k)", "Superhuman ($3M)", "Death Step ($5M)", "Sharkman Karate", "Electric Claw", "Dragon Talon", "God Human"}
for _, melee in ipairs(melees) do
    CreateButton(shopFrame, "Buy " .. melee, yOff, Color3.fromRGB(30, 0, 20), function()
        local command = melee:gsub(" .*", ""):gsub("%(", ""):gsub("%)", ""):gsub(" ", "")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buy" .. command)
    end); yOff = yOff + 38
    if yOff > 400 then break end
end

-- ==================== PESTAÑA SETTINGS ====================
local settingsFrame = subFrames["SETTINGS"]
yOff = 5

CreateSection(settingsFrame, "CHARACTER SETTINGS", yOff); yOff = yOff + 28
CreateButton(settingsFrame, "▶ Auto Haki", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoHaki = not getgenv().AutoHaki
    if getgenv().AutoHaki then
        task.spawn(function()
            while getgenv().AutoHaki do
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
                task.wait(5)
            end
        end)
    end
end); yOff = yOff + 42
CreateButton(settingsFrame, "▶ Auto Active Race V3", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoRaceV3 = not getgenv().AutoRaceV3
    if getgenv().AutoRaceV3 then
        task.spawn(function()
            while getgenv().AutoRaceV3 do
                game:GetService("ReplicatedStorage").Remotes.CommE:FireServer("ActivateAbility")
                task.wait(1)
            end
        end)
    end
end); yOff = yOff + 42
CreateButton(settingsFrame, "▶ Auto Active Race V4", yOff, Color3.fromRGB(50, 0, 30), function()
    getgenv().AutoRaceV4 = not getgenv().AutoRaceV4
    if getgenv().AutoRaceV4 then
        task.spawn(function()
            while getgenv().AutoRaceV4 do
                VirtualInputManager:SendKeyEvent(true, "Y", false, game)
                task.wait(0.1)
                VirtualInputManager:SendKeyEvent(false, "Y", false, game)
                task.wait(5)
            end
        end)
    end
end); yOff = yOff + 50

CreateSection(settingsFrame, "SERVER", yOff); yOff = yOff + 28
CreateButton(settingsFrame, "▶ Rejoin Server", yOff, Color3.fromRGB(30, 0, 20), function()
    game:GetService("TeleportService"):Teleport(game.PlaceId, game.Players.LocalPlayer)
end); yOff = yOff + 42
CreateButton(settingsFrame, "▶ Redeem All Codes", yOff, Color3.fromRGB(30, 0, 20), function()
    local codes = {"NOEXPLOITER", "NOOB2ADMIN", "CODESLIDE", "ADMINHACKED", "SUB2GAMERROBOT_EXP1", "FUDD10", "FUDD10_V2", "BIGNEWS", "THEGREATACE", "SUB2NOOBMASTER123"}
    for _, code in ipairs(codes) do
        pcall(function()
            game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(code)
        end)
        task.wait(0.2)
    end
end); yOff = yOff + 42

-- ==================== FUNCIONES ABUSOS ====================
local function Press(key)
    VirtualInputManager:SendKeyEvent(true, key, false, game)
    task.wait(0.01)
    VirtualInputManager:SendKeyEvent(false, key, false, game)
end

local function ExecuteAbuse()
    if not getgenv().AbuseActive then return end
    local char = lp.Character or lp.CharacterAdded:Wait()
    local hrp = char:WaitForChild("HumanoidRootPart", 10)
    local hum = char:WaitForChild("Humanoid", 10)
    if hrp and hum and hum.Health > 0 then
        hrp.CFrame = hrp.CFrame * CFrame.new(0, 500, 0)
        Press(getgenv().SelectedSlot)
        task.wait(0.08)
        Press(Enum.KeyCode.J)
        local targetPos = CFrame.new(923.2, 3000000000000000000000, 32852.8)
        hrp.Anchored = true
        hrp.CFrame = targetPos
        workspace.CurrentCamera.CFrame = targetPos
        task.wait(0.05)
        Press(Enum.KeyCode.Z)
        task.spawn(function()
            task.wait(0.03)
            hum.Health = 0
        end)
        local s = tick()
        while tick() - s < 0.6 do RunService.Heartbeat:Wait() end
    end
end

local function VoidSkill()
    local char = lp.Character
    local hrp = char and char:FindFirstChild("HumanoidRootPart")
    if hrp then
        local oldPos = hrp.CFrame
        hrp.Anchored = true
        hrp.CFrame = CFrame.new(923.2, 3000000000000000000000, 32852.8)
        workspace.CurrentCamera.CFrame = hrp.CFrame
        task.wait(0.1)
        Press(Enum.KeyCode.Z)
        task.wait(0.8)
        hrp.CFrame = oldPos
        workspace.CurrentCamera.CameraSubject = char.Humanoid
        hrp.Anchored = false
    end
end

local function MakeAbuseButton(parent, text, yPos, bgColor, icon)
    local btn = Instance.new("TextButton", parent)
    btn.Size = UDim2.new(0.88, 0, 0, 42)
    btn.Position = UDim2.new(0.06, 0, 0, yPos)
    btn.BackgroundColor3 = bgColor
    btn.Text = icon .. " " .. text .. " " .. icon
    btn.TextColor3 = Color3.new(1, 1, 1)
    btn.Font = Enum.Font.GothamBold
    btn.TextSize = 13
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 8)
    return btn
end

local MasterToggleBtn = MakeAbuseButton(AbusosContent, "ACTIVAR TODO", 10, Color3.fromRGB(80, 0, 0), "◉")
local Abuse3Btn = MakeAbuseButton(AbusosContent, "ABUSE 3", 62, Color3.fromRGB(40, 0, 20), "⚡")
local Abuse1Btn = MakeAbuseButton(AbusosContent, "ABUSE 1", 114, Color3.fromRGB(40, 0, 20), "⚡")
local VoidBtn   = MakeAbuseButton(AbusosContent, "INF", 166, Color3.fromRGB(25, 0, 15), "🌀")
local FixBtn    = MakeAbuseButton(AbusosContent, "FIX CAMERA", 218, Color3.fromRGB(10, 0, 5), "🔧")
FixBtn.Size = UDim2.new(0.88, 0, 0, 32)

getgenv().GlobalEnabled = true

MasterToggleBtn.MouseButton1Click:Connect(function()
    getgenv().GlobalEnabled = not getgenv().GlobalEnabled
    if getgenv().GlobalEnabled then
        MasterToggleBtn.BackgroundColor3 = Color3.fromRGB(80, 0, 0)
        MasterToggleBtn.Text = "◉ ACTIVADO ◉"
        MasterToggleBtn.TextColor3 = Color3.fromRGB(0, 255, 0)
    else
        MasterToggleBtn.BackgroundColor3 = Color3.fromRGB(30, 0, 0)
        MasterToggleBtn.Text = "◉ DESACTIVADO ◉"
        MasterToggleBtn.TextColor3 = Color3.fromRGB(255, 80, 80)
        getgenv().AbuseActive = false
        Abuse3Btn.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
        Abuse1Btn.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
    end
end)

Abuse3Btn.MouseButton1Click:Connect(function()
    if not getgenv().GlobalEnabled then return end
    getgenv().SelectedSlot = Enum.KeyCode.Three
    getgenv().AbuseActive = not getgenv().AbuseActive
    Abuse3Btn.BackgroundColor3 = getgenv().AbuseActive and Color3.fromRGB(180, 0, 50) or Color3.fromRGB(40, 0, 20)
    if getgenv().AbuseActive then task.spawn(ExecuteAbuse) end
end)

Abuse1Btn.MouseButton1Click:Connect(function()
    if not getgenv().GlobalEnabled then return end
    getgenv().SelectedSlot = Enum.KeyCode.One
    getgenv().AbuseActive = not getgenv().AbuseActive
    Abuse1Btn.BackgroundColor3 = getgenv().AbuseActive and Color3.fromRGB(180, 0, 50) or Color3.fromRGB(40, 0, 20)
    if getgenv().AbuseActive then task.spawn(ExecuteAbuse) end
end)

VoidBtn.MouseButton1Click:Connect(VoidSkill)

FixBtn.MouseButton1Click:Connect(function()
    getgenv().AbuseActive = false
    if lp.Character then
        workspace.CurrentCamera.CameraSubject = lp.Character.Humanoid
        lp.Character.HumanoidRootPart.Anchored = false
    end
end)

task.wait(0.5)
getgenv().SelectedSlot = Enum.KeyCode.One
getgenv().AbuseActive = true
Abuse1Btn.BackgroundColor3 = Color3.fromRGB(180, 0, 50)
task.spawn(ExecuteAbuse)

lp.CharacterAdded:Connect(function()
    if getgenv().AbuseActive and getgenv().GlobalEnabled then
        task.wait(0.5)
        task.spawn(ExecuteAbuse)
    end
end)

-- ==================== INFO CONTENT ====================
local InfoText = Instance.new("TextLabel", InfoContent)
InfoText.Size = UDim2.new(0.9, 0, 0, 350)
InfoText.Position = UDim2.new(0.05, 0, 0.05, 0)
InfoText.BackgroundTransparency = 1
InfoText.Text = "⚡ 白色恶魔 HUB ☠\n\n" ..
"Versión: 4.0\n\n" ..
"━━━━━━━━━━━━━━━━━━━━\n" ..
"🔥 ABUSOS:\n" ..
"• Abuse 1 - Activo por defecto\n" ..
"• Abuse 3 - Bucle infinito\n" ..
"• INF - Teletransporte extremo\n" ..
"• FIX CAMERA - Restaura todo\n\n" ..
"🌀 REDZ HUB:\n" ..
"• FARMING - Auto farm, materiales\n" ..
"• QUESTS - Espadas, misiones\n" ..
"• TRIALS - Race V4, Katakuri\n" ..
"• RAIDS - Fruit/Law raids\n" ..
"• FISHING - Auto pesca\n" ..
"• TELEPORT - Islas/mares\n" ..
"• SHOP - Mejoras y habilidades\n" ..
"• SETTINGS - Haki, Race, códigos\n\n" ..
"━━━━━━━━━━━━━━━━━━━━\n" ..
"Discord: discord.gg/vggTR35SRh\n" ..
"Creado por: 白色恶魔"
InfoText.TextColor3 = Color3.fromRGB(200, 150, 255)
InfoText.Font = Enum.Font.Gotham
InfoText.TextSize = 12
InfoText.TextWrapped = true
InfoText.TextXAlignment = Enum.TextXAlignment.Center

-- Cambio de pestañas principales
TabAbusos.MouseButton1Click:Connect(function()
    AbusosContent.Visible = true
    RedzContent.Visible = false
    InfoContent.Visible = false
    TabAbusos.BackgroundColor3 = ACCENT
    TabRedz.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
    TabInfo.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
end)

TabRedz.MouseButton1Click:Connect(function()
    AbusosContent.Visible = false
    RedzContent.Visible = true
    InfoContent.Visible = false
    TabAbusos.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
    TabRedz.BackgroundColor3 = ACCENT
    TabInfo.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
end)

TabInfo.MouseButton1Click:Connect(function()
    AbusosContent.Visible = false
    RedzContent.Visible = false
    InfoContent.Visible = true
    TabAbusos.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
    TabRedz.BackgroundColor3 = Color3.fromRGB(40, 0, 20)
    TabInfo.BackgroundColor3 = ACCENT
end)

local minimized = false
MinBtn.MouseButton1Click:Connect(function()
    minimized = not minimized
    if minimized then
        MainFrame.Size = UDim2.new(0, 450, 0, 48)
        MainTabBar.Visible = false
        MainContentContainer.Visible = false
        Subtitle.Visible = false
        MinBtn.Text = "➕"
    else
        MainFrame.Size = UDim2.new(0, 450, 0, 550)
        MainTabBar.Visible = true
        MainContentContainer.Visible = true
        Subtitle.Visible = true
        MinBtn.Text = "🗕"
    end
end)

-- Movimiento de ventana
local dragStart, dragPos, startPos
TitleBar.InputBegan:Connect(function(i)
    if i.UserInputType == Enum.UserInputType.MouseButton1 then
        dragStart = true
        dragPos = i.Position
        startPos = MainFrame.Position
    end
end)
UserInputService.InputChanged:Connect(function(i)
    if dragStart and i.UserInputType == Enum.UserInputType.MouseMovement then
        local delta = i.Position - dragPos
        MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)
UserInputService.InputEnded:Connect(function(i)
    if i.UserInputType == Enum.UserInputType.MouseButton1 then dragStart = false end
end)
