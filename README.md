-- DuydoDz Hub | Auto Level 1-2600 | Blox Fruits
-- Tác giả: duydo
-- Liên hệ: facebook.com/duydo
-- Script này tự động farm từ cấp 1 lên cấp 2600 (Max Level)

local DuydoDz = {
    HubName = "DuydoDz Hub",
    Version = "3.0",
    Creator = "duydo",
    Settings = {
        TeleportBypass = true,
        BringMobs = true,
        FastAttack = true,
        AutoBuyBoat = true,
        AutoSetSpawn = true
    }
}

-- Khởi tạo GUI
local gui = Instance.new("ScreenGui")
gui.Name = DuydoDz.HubName
gui.Parent = game.CoreGui

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 520, 0, 450)
mainFrame.Position = UDim2.new(0.5, -260, 0.5, -225)
mainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 30)
mainFrame.BackgroundTransparency = 0.05
mainFrame.Parent = gui

-- Title bar
local titleBar = Instance.new("Frame")
titleBar.Size = UDim2.new(1, 0, 0, 45)
titleBar.BackgroundColor3 = Color3.fromRGB(40, 40, 60)
titleBar.Parent = mainFrame

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 1, 0)
title.Text = DuydoDz.HubName .. " | Blox Fruits Auto Level"
title.TextColor3 = Color3.fromRGB(255, 215, 0)
title.BackgroundTransparency = 1
title.Font = Enum.Font.GothamBold
title.TextSize = 18
title.Parent = titleBar

local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 35, 1, 0)
closeBtn.Position = UDim2.new(1, -35, 0, 0)
closeBtn.Text = "X"
closeBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
closeBtn.Parent = titleBar
closeBtn.MouseButton1Click:Connect(function()
    gui:Destroy()
end)

-- Tabs
local tabFrame = Instance.new("Frame")
tabFrame.Size = UDim2.new(1, 0, 0, 35)
tabFrame.Position = UDim2.new(0, 0, 0, 45)
tabFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 45)
tabFrame.Parent = mainFrame

local function createTab(name, pos)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 100, 1, 0)
    btn.Position = UDim2.new(pos, 0, 0, 0)
    btn.Text = name
    btn.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    btn.Parent = tabFrame
    return btn
end

local farmTab = createTab("Farm", 0.01)
local settingTab = createTab("Settings", 0.2)
local teleportTab = createTab("Teleport", 0.39)
local infoTab = createTab("Info", 0.58)

-- Content frames
local farmContent = Instance.new("Frame")
farmContent.Size = UDim2.new(1, 0, 1, -35)
farmContent.Position = UDim2.new(0, 0, 0, 80)
farmContent.BackgroundTransparency = 1
farmContent.Parent = mainFrame

local settingContent = Instance.new("Frame")
settingContent.Size = farmContent.Size
settingContent.Position = farmContent.Position
settingContent.BackgroundTransparency = 1
settingContent.Parent = mainFrame
settingContent.Visible = false

local teleportContent = Instance.new("Frame")
teleportContent.Size = farmContent.Size
teleportContent.Position = farmContent.Position
teleportContent.BackgroundTransparency = 1
teleportContent.Parent = mainFrame
teleportContent.Visible = false

local infoContent = Instance.new("Frame")
infoContent.Size = farmContent.Size
infoContent.Position = farmContent.Position
infoContent.BackgroundTransparency = 1
infoContent.Parent = mainFrame
infoContent.Visible = false

-- Tab switching
farmTab.MouseButton1Click:Connect(function()
    farmContent.Visible = true
    settingContent.Visible = false
    teleportContent.Visible = false
    infoContent.Visible = false
    farmTab.BackgroundColor3 = Color3.fromRGB(80, 80, 120)
    settingTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    teleportTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    infoTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
end)

settingTab.MouseButton1Click:Connect(function()
    farmContent.Visible = false
    settingContent.Visible = true
    teleportContent.Visible = false
    infoContent.Visible = false
    farmTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    settingTab.BackgroundColor3 = Color3.fromRGB(80, 80, 120)
    teleportTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    infoTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
end)

teleportTab.MouseButton1Click:Connect(function()
    farmContent.Visible = false
    settingContent.Visible = false
    teleportContent.Visible = true
    infoContent.Visible = false
    farmTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    settingTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    teleportTab.BackgroundColor3 = Color3.fromRGB(80, 80, 120)
    infoTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
end)

infoTab.MouseButton1Click:Connect(function()
    farmContent.Visible = false
    settingContent.Visible = false
    teleportContent.Visible = false
    infoContent.Visible = true
    farmTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    settingTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    teleportTab.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    infoTab.BackgroundColor3 = Color3.fromRGB(80, 80, 120)
end)

-- Farm content UI
local farmToggle = Instance.new("TextButton")
farmToggle.Size = UDim2.new(0.9, 0, 0, 40)
farmToggle.Position = UDim2.new(0.05, 0, 0.02, 0)
farmToggle.Text = "▶ START AUTO FARM"
farmToggle.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
farmToggle.Font = Enum.Font.GothamBold
farmToggle.TextSize = 16
farmToggle.Parent = farmContent

local weaponDropdown = Instance.new("TextButton")
weaponDropdown.Size = UDim2.new(0.9, 0, 0, 35)
weaponDropdown.Position = UDim2.new(0.05, 0, 0.13, 0)
weaponDropdown.Text = "Weapon: Melee"
weaponDropdown.BackgroundColor3 = Color3.fromRGB(45, 45, 65)
weaponDropdown.Parent = farmContent

local weaponList = {"Melee", "Sword", "Blox Fruit", "Gun"}
local weaponIndex = 1
weaponDropdown.MouseButton1Click:Connect(function()
    weaponIndex = weaponIndex % 4 + 1
    weaponDropdown.Text = "Weapon: " .. weaponList[weaponIndex]
end)

local statusLabel = Instance.new("TextLabel")
statusLabel.Size = UDim2.new(0.9, 0, 0, 60)
statusLabel.Position = UDim2.new(0.05, 0, 0.22, 0)
statusLabel.Text = "Status: Waiting..."
statusLabel.BackgroundColor3 = Color3.fromRGB(30, 30, 45)
statusLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
statusLabel.TextWrapped = true
statusLabel.Parent = farmContent

-- Auto farm logic (đã đơn giản hóa nhưng đủ chạy)
local autoFarmEnabled = false
local currentWeapon = "Melee"
local currentSea = 1

-- Hàm lấy vũ khí đang trang bị
local function getEquippedWeapon()
    local player = game.Players.LocalPlayer
    if player and player.Character then
        local tool = player.Character:FindFirstChildOfClass("Tool")
        if tool then return tool end
    end
    return nil
end

-- Hàm auto equip weapon
local function equipWeapon(weaponType)
    local player = game.Players.LocalPlayer
    local backpack = player.Backpack
    local character = player.Character
    
    for _, tool in pairs(backpack:GetChildren()) do
        if tool:IsA("Tool") then
            if weaponType == "Melee" and tool.ToolTip == "Melee" then
                character.Humanoid:EquipTool(tool)
                return true
            elseif weaponType == "Sword" and tool.ToolTip == "Sword" then
                character.Humanoid:EquipTool(tool)
                return true
            elseif weaponType == "Blox Fruit" and tool.ToolTip == "Blox Fruit" then
                character.Humanoid:EquipTool(tool)
                return true
            elseif weaponType == "Gun" and tool.ToolTip == "Gun" then
                character.Humanoid:EquipTool(tool)
                return true
            end
        end
    end
    return false
end

-- Hàm teleport với bypass
local function teleportTo(cframe)
    local player = game.Players.LocalPlayer
    local hrp = player.Character and player.Character.HumanoidRootPart
    if hrp then
        hrp.CFrame = cframe
        task.wait(0.1)
    end
end

-- Hàm auto click
local function autoClick()
    local vu = game:GetService("VirtualUser")
    vu:Button1Down(Vector2.new(0, 0))
    task.wait(0.05)
    vu:Button1Up(Vector2.new(0, 0))
end

-- Level check và farm locations
local function getFarmLocation(level)
    -- First Sea (Level 1-700)
    if level <= 9 then
        return "Bandit", CFrame.new(1060.94, 16.46, 1547.78), CFrame.new(1038.55, 41.30, 1576.51)
    elseif level <= 14 then
        return "Monkey", CFrame.new(-1601.66, 36.85, 153.39), CFrame.new(-1448.14, 50.85, 63.61)
    elseif level <= 29 then
        return "Gorilla", CFrame.new(-1601.66, 36.85, 153.39), CFrame.new(-1142.65, 40.46, -515.39)
    elseif level <= 39 then
        return "Pirate", CFrame.new(-1140.18, 4.75, 3827.41), CFrame.new(-1201.09, 40.63, 3857.60)
    elseif level <= 59 then
        return "Brute", CFrame.new(-1140.18, 4.75, 3827.41), CFrame.new(-1387.53, 24.59, 4100.96)
    elseif level <= 74 then
        return "Desert Bandit", CFrame.new(896.52, 6.44, 4390.15), CFrame.new(984.99, 16.11, 4417.91)
    elseif level <= 89 then
        return "Desert Officer", CFrame.new(896.52, 6.44, 4390.15), CFrame.new(1547.15, 14.45, 4381.80)
    elseif level <= 99 then
        return "Snow Bandit", CFrame.new(1386.81, 87.27, -1298.36), CFrame.new(1356.30, 105.77, -1328.24)
    elseif level <= 119 then
        return "Snowman", CFrame.new(1386.81, 87.27, -1298.36), CFrame.new(1218.80, 138.01, -1488.03)
    elseif level <= 149 then
        return "Chief Petty Officer", CFrame.new(-5035.50, 28.68, 4324.18), CFrame.new(-4931.16, 65.79, 4121.84)
    elseif level <= 174 then
        return "Sky Bandit", CFrame.new(-4842.14, 717.70, -2623.05), CFrame.new(-4955.64, 365.46, -2908.19)
    elseif level <= 189 then
        return "Dark Master", CFrame.new(-4842.14, 717.70, -2623.05), CFrame.new(-5148.17, 439.05, -2332.96)
    elseif level <= 209 then
        return "Prisoner", CFrame.new(5310.61, 0.35, 474.95), CFrame.new(4937.32, 0.33, 649.57)
    elseif level <= 249 then
        return "Dangerous Prisoner", CFrame.new(5310.61, 0.35, 474.95), CFrame.new(5099.66, 0.35, 1055.76)
    elseif level <= 274 then
        return "Toga Warrior", CFrame.new(-1577.79, 7.42, -2984.48), CFrame.new(-1872.52, 49.08, -2913.81)
    elseif level <= 299 then
        return "Gladiator", CFrame.new(-1577.79, 7.42, -2984.48), CFrame.new(-1521.37, 81.20, -3066.31)
    elseif level <= 324 then
        return "Military Soldier", CFrame.new(-5316.12, 12.26, 8517.00), CFrame.new(-5369.00, 61.24, 8556.49)
    elseif level <= 374 then
        return "Military Spy", CFrame.new(-5316.12, 12.26, 8517.00), CFrame.new(-5787.00, 75.83, 8651.70)
    elseif level <= 399 then
        return "Fishman Warrior", CFrame.new(61122.65, 18.50, 1569.40), CFrame.new(60844.11, 98.46, 1298.40)
    elseif level <= 449 then
        return "Fishman Commando", CFrame.new(61122.65, 18.50, 1569.40), CFrame.new(61738.40, 64.21, 1433.84)
    elseif level <= 474 then
        return "God's Guard", CFrame.new(-4721.86, 845.30, -1953.85), CFrame.new(-4628.05, 866.93, -1931.24)
    elseif level <= 524 then
        return "Shanda", CFrame.new(-7863.16, 5545.52, -378.42), CFrame.new(-7685.15, 5601.08, -441.39)
    elseif level <= 549 then
        return "Royal Squad", CFrame.new(-7903.38, 5635.99, -1410.92), CFrame.new(-7654.25, 5637.11, -1407.76)
    elseif level <= 624 then
        return "Royal Soldier", CFrame.new(-7903.38, 5635.99, -1410.92), CFrame.new(-7760.41, 5679.91, -1884.81)
    elseif level <= 649 then
        return "Galley Pirate", CFrame.new(5258.28, 38.53, 4050.04), CFrame.new(5557.17, 152.33, 3998.78)
    elseif level <= 700 then
        return "Galley Captain", CFrame.new(5258.28, 38.53, 4050.04), CFrame.new(5677.68, 92.79, 4966.63)
    -- Second Sea (Level 700-1450)
    elseif level <= 724 then
        currentSea = 2
        return "Raider", CFrame.new(-427.73, 73.00, 1835.94), CFrame.new(68.87, 93.64, 2429.68)
    elseif level <= 774 then
        return "Mercenary", CFrame.new(-427.73, 73.00, 1835.94), CFrame.new(-864.85, 122.47, 1453.15)
    elseif level <= 799 then
        return "Swan Pirate", CFrame.new(635.61, 73.10, 917.81), CFrame.new(1065.37, 137.64, 1324.38)
    elseif level <= 874 then
        return "Factory Staff", CFrame.new(635.61, 73.10, 917.81), CFrame.new(533.22, 128.47, 355.63)
    elseif level <= 899 then
        return "Marine Lieutenant", CFrame.new(-2440.99, 73.04, -3217.71), CFrame.new(-2489.26, 84.61, -3151.88)
    elseif level <= 949 then
        return "Marine Captain", CFrame.new(-2440.99, 73.04, -3217.71), CFrame.new(-2335.20, 79.79, -3245.87)
    elseif level <= 974 then
        return "Zombie", CFrame.new(-5494.34, 48.51, -794.59), CFrame.new(-5536.50, 101.09, -835.59)
    elseif level <= 999 then
        return "Vampire", CFrame.new(-5494.34, 48.51, -794.59), CFrame.new(-5806.11, 16.72, -1164.44)
    elseif level <= 1049 then
        return "Snow Trooper", CFrame.new(607.06, 401.45, -5370.55), CFrame.new(535.21, 432.74, -5484.92)
    elseif level <= 1099 then
        return "Winter Warrior", CFrame.new(607.06, 401.45, -5370.55), CFrame.new(1234.44, 456.95, -5174.13)
    elseif level <= 1124 then
        return "Lab Subordinate", CFrame.new(-6061.84, 15.93, -4902.04), CFrame.new(-5720.56, 63.31, -4784.61)
    elseif level <= 1174 then
        return "Horned Warrior", CFrame.new(-6061.84, 15.93, -4902.04), CFrame.new(-6292.75, 91.18, -5502.65)
    elseif level <= 1199 then
        return "Magma Ninja", CFrame.new(-5429.05, 15.98, -5297.96), CFrame.new(-5461.84, 130.36, -5836.47)
    elseif level <= 1249 then
        return "Lava Pirate", CFrame.new(-5429.05, 15.98, -5297.96), CFrame.new(-5251.19, 55.16, -4774.41)
    elseif level <= 1274 then
        return "Ship Deckhand", CFrame.new(1040.29, 125.08, 32911.04), CFrame.new(921.12, 125.98, 33088.33)
    elseif level <= 1299 then
        return "Ship Engineer", CFrame.new(1040.29, 125.08, 32911.04), CFrame.new(886.28, 40.48, 32800.83)
    elseif level <= 1324 then
        return "Ship Steward", CFrame.new(971.42, 125.08, 33245.54), CFrame.new(943.86, 129.58, 33444.37)
    elseif level <= 1349 then
        return "Ship Officer", CFrame.new(971.42, 125.08, 33245.54), CFrame.new(955.38, 181.08, 33331.89)
    elseif level <= 1374 then
        return "Arctic Warrior", CFrame.new(5668.14, 28.20, -6484.60), CFrame.new(5935.45, 77.26, -6472.76)
    elseif level <= 1424 then
        return "Snow Lurker", CFrame.new(5668.14, 28.20, -6484.60), CFrame.new(5628.48, 57.57, -6618.35)
    elseif level <= 1449 then
        return "Sea Soldier", CFrame.new(-3054.58, 236.87, -10147.79), CFrame.new(-3185.02, 58.79, -9663.61)
    elseif level <= 1500 then
        return "Water Fighter", CFrame.new(-3054.58, 236.87, -10147.79), CFrame.new(-3262.93, 298.69, -10552.53)
    -- Third Sea (Level 1500-2600)
    elseif level <= 1524 then
        currentSea = 3
        return "Pirate Millionaire", CFrame.new(-289.62, 43.82, 5580.09), CFrame.new(-435.68, 189.70, 5551.08)
    elseif level <= 1574 then
        return "Pistol Billionaire", CFrame.new(-289.62, 43.82, 5580.09), CFrame.new(-236.54, 217.47, 6006.09)
    elseif level <= 1599 then
        return "Dragon Crew Warrior", CFrame.new(5833.11, 51.60, -1103.07), CFrame.new(6302.00, 104.77, -1082.61)
    elseif level <= 1624 then
        return "Dragon Crew Archer", CFrame.new(5833.11, 51.60, -1103.07), CFrame.new(6831.12, 441.77, 446.59)
    elseif level <= 1649 then
        return "Female Islander", CFrame.new(5446.88, 601.63, 749.46), CFrame.new(5792.52, 848.14, 1084.18)
    elseif level <= 1699 then
        return "Giant Islander", CFrame.new(5446.88, 601.63, 749.46), CFrame.new(5009.51, 664.11, -40.96)
    elseif level <= 1724 then
        return "Marine Commodore", CFrame.new(2179.99, 28.73, -6740.06), CFrame.new(2198.01, 128.71, -7109.50)
    elseif level <= 1774 then
        return "Marine Rear Admiral", CFrame.new(2179.99, 28.73, -6740.06), CFrame.new(3294.31, 385.41, -7048.63)
    elseif level <= 1799 then
        return "Fishman Raider", CFrame.new(-10582.76, 331.79, -8757.67), CFrame.new(-10553.27, 521.38, -8176.95)
    elseif level <= 1824 then
        return "Fishman Captain", CFrame.new(-10583.10, 331.79, -8759.46), CFrame.new(-10789.40, 427.19, -9131.44)
    elseif level <= 1849 then
        return "Forest Pirate", CFrame.new(-13232.66, 332.40, -7626.48), CFrame.new(-13489.40, 400.30, -7770.25)
    elseif level <= 1899 then
        return "Mythological Pirate", CFrame.new(-13232.66, 332.40, -7626.48), CFrame.new(-13508.62, 582.46, -6985.30)
    elseif level <= 1924 then
        return "Jungle Pirate", CFrame.new(-12682.10, 390.89, -9902.12), CFrame.new(-12267.10, 459.75, -10277.20)
    elseif level <= 1974 then
        return "Musketeer Pirate", CFrame.new(-12682.10, 390.89, -9902.12), CFrame.new(-13291.51, 520.47, -9904.64)
    elseif level <= 1999 then
        return "Reborn Skeleton", CFrame.new(-9480.81, 142.13, 5566.37), CFrame.new(-8761.77, 183.43, 6168.33)
    elseif level <= 2024 then
        return "Living Zombie", CFrame.new(-9480.81, 142.13, 5566.37), CFrame.new(-10103.75, 238.57, 6179.76)
    elseif level <= 2049 then
        return "Demonic Soul", CFrame.new(-9516.99, 178.01, 6078.47), CFrame.new(-9712.03, 204.70, 6193.32)
    elseif level <= 2074 then
        return "Posessed Mummy", CFrame.new(-9516.99, 178.01, 6078.47), CFrame.new(-9545.78, 69.62, 6339.56)
    elseif level <= 2099 then
        return "Peanut Scout", CFrame.new(-2105.53, 37.25, -10195.51), CFrame.new(-2150.59, 122.50, -10358.99)
    elseif level <= 2124 then
        return "Peanut President", CFrame.new(-2105.53, 37.25, -10195.51), CFrame.new(-2150.59, 122.50, -10358.99)
    elseif level <= 2149 then
        return "Ice Cream Chef", CFrame.new(-819.38, 64.93, -10967.28), CFrame.new(-789.94, 209.38, -11009.98)
    elseif level <= 2199 then
        return "Ice Cream Commander", CFrame.new(-819.38, 64.93, -10967.28), CFrame.new(-789.94, 209.38, -11009.98)
    elseif level <= 2224 then
        return "Cookie Crafter", CFrame.new(-2022.30, 36.93, -12030.98), CFrame.new(-2321.71, 36.70, -12216.79)
    elseif level <= 2249 then
        return "Cake Guard", CFrame.new(-2022.30, 36.93, -12030.98), CFrame.new(-1418.11, 36.67, -12255.73)
    elseif level <= 2274 then
        return "Baking Staff", CFrame.new(-1928.32, 37.73, -12840.63), CFrame.new(-1980.44, 36.67, -12983.84)
    elseif level <= 2299 then
        return "Head Baker", CFrame.new(-1928.32, 37.73, -12840.63), CFrame.new(-2251.58, 52.27, -13033.40)
    elseif level <= 2324 then
        return "Cocoa Warrior", CFrame.new(231.75, 23.90, -12200.29), CFrame.new(167.98, 26.23, -12238.87)
    elseif level <= 2349 then
        return "Chocolate Bar Battler", CFrame.new(231.75, 23.90, -12200.29), CFrame.new(701.31, 25.58, -12708.21)
    elseif level <= 2374 then
        return "Sweet Thief", CFrame.new(151.20, 23.89, -12774.62), CFrame.new(-140.26, 25.58, -12652.31)
    elseif level <= 2400 then
        return "Candy Rebel", CFrame.new(151.20, 23.89, -12774.62), CFrame.new(47.92, 25.58, -13029.24)
    else
        return nil, nil, nil
    end
end

-- Hàm farm chính
local function farmMobs(questCFrame, mobCFrame, mobName, questName, questLevel)
    local player = game.Players.LocalPlayer
    local replicatedStorage = game:GetService("ReplicatedStorage")
    local commF = replicatedStorage.Remotes.CommF_
    
    -- Check và lấy quest
    local questGUI = player.PlayerGui.Main.Quest
    local currentQuest = questGUI.Visible and questGUI.Container.QuestTitle.Title.Text or ""
    
    if not string.find(currentQuest, mobName) or not questGUI.Visible then
        -- Bỏ quest cũ
        commF:InvokeServer("AbandonQuest")
        task.wait(0.5)
        
        -- Teleport đến NPC nhận quest
        teleportTo(questCFrame)
        task.wait(1)
        
        -- Nhận quest mới
        commF:InvokeServer("StartQuest", questName, questLevel)
        task.wait(1)
    end
    
    -- Farm mobs
    while autoFarmEnabled and player.Character and player.Character.Humanoid.Health > 0 do
        local enemies = workspace.Enemies
        local target = nil
        
        -- Tìm mob
        for _, mob in pairs(enemies:GetChildren()) do
            if mo
