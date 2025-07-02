    
	1.	local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
	2.	
	3.	local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
	4.	
	5.	 
	6.	 
	7.	local player = game:GetService("Players").LocalPlayer
	8.	
	9.	local shop = player.PlayerGui:FindFirstChild("Main") and player.PlayerGui.Main:FindFirstChild("CoinsShop")
	10.	
	11.	 
	12.	local Window = Fluent:CreateWindow({
	13.	
	14.	    Title = game:GetService("MarketplaceService"):GetProductInfo(109983668079237).Name .. " 〢 WASHEDZ ",
	15.	
	16.	    SubTitle = "WASHEDZ",
	17.	
	18.	    TabWidth = 160,
	19.	
	20.	    Size = UDim2.fromOffset(520, 400),
	21.	
	22.	    Acrylic = false,
	23.	
	24.	    Theme = "Darker",
	25.	
	26.	    MinimizeKey = Enum.KeyCode.LeftControl
	27.	
	28.	})
	29.	
	30.	 
	31.	local Tabs = {
	32.	
	33.	    Updates = Window:AddTab({ Title = "Home", Icon = "home" }),
	34.	
	35.	    Main = Window:AddTab({ Title = "Main", Icon = "rocket" }),
	36.	
	37.	    Server = Window:AddTab({ Title = "Server", Icon = "server" }),
	38.	
	39.	    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" }),
	40.	
	41.	}
	42.	
	43.	 
	44.	local plotName
	45.	
	46.	for _, plot in ipairs(workspace.Plots:GetChildren()) do
	47.	
	48.	    if plot:FindFirstChild("YourBase", true).Enabled then
	49.	
	50.	        plotName = plot.Name
	51.	
	52.	        break
	53.	
	54.	    end
	55.	
	56.	end
	57.	
	58.	 
	59.	local remainingTime = workspace.Plots[plotName].Purchases.PlotBlock.Main.BillboardGui.RemainingTime
	60.	
	61.	local rtp = Tabs.Main:AddParagraph({ Title = "Lock Time: " .. remainingTime.Text })
	62.	
	63.	 
	64.	task.spawn(function()
	65.	
	66.	    while true do
	67.	
	68.	        rtp:SetTitle("Lock Time: " .. remainingTime.Text)
	69.	
	70.	        task.wait(0.25)
	71.	
	72.	    end
	73.	
	74.	end)
	75.	
	76.	 
	77.	Tabs.Main:AddButton({
	78.	
	79.	    Title = "Steal",
	80.	
	81.	    Description = "Spam if not working (teleports you to middle)",
	82.	
	83.	    Callback = function()
	84.	
	85.	        local player = game.Players.LocalPlayer
	86.	
	87.	        local pos = CFrame.new(0, -500, 0)
	88.	
	89.	        local startT = os.clock()
	90.	
	91.	        while os.clock() - startT < 1 do
	92.	
	93.	            if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
	94.	
	95.	                player.Character.HumanoidRootPart.CFrame = pos
	96.	
	97.	            end
	98.	
	99.	            task.wait()
	100.	
	101.	        end
	102.	
	103.	    end
	104.	
	105.	})
	106.	
	107.	 
	108.	local SpeedSlider = Tabs.Main:AddSlider("Slider", {
	109.	
	110.	    Title = "Speed Boost",
	111.	
	112.	    Default = 0,
	113.	
	114.	    Min = 0,
	115.	
	116.	    Max = 6,
	117.	
	118.	    Rounding = 1,
	119.	
	120.	})
	121.	
	122.	 
	123.	Tabs.Main:AddParagraph({
	124.	
	125.	    Title = "Use Speed Coil/Invisibility Cloak For Higher Speed",
	126.	
	127.	})
	128.	
	129.	 
	130.	local currentSpeed = 0
	131.	
	132.	SpeedSlider:OnChanged(function(Value)
	133.	
	134.	    currentSpeed = tonumber(Value) or 0
	135.	
	136.	end)
	137.	
	138.	 
	139.	local function sSpeed(character)
	140.	
	141.	    local hum = character:WaitForChild("Humanoid")
	142.	
	143.	    local hb = game:GetService("RunService").Heartbeat
	144.	
	145.	 
	146.	    task.spawn(function()
	147.	
	148.	        while character and hum and hum.Parent do
	149.	
	150.	            if currentSpeed > 0 and hum.MoveDirection.Magnitude > 0 then
	151.	
	152.	                character:TranslateBy(hum.MoveDirection * currentSpeed * hb:Wait() * 10)
	153.	
	154.	            end
	155.	
	156.	            task.wait()
	157.	
	158.	        end
	159.	
	160.	    end)
	161.	
	162.	end
	163.	
	164.	 
	165.	local function onCharacterAdded(character)
	166.	
	167.	    sSpeed(character)
	168.	
	169.	end
	170.	
	171.	 
	172.	player.CharacterAdded:Connect(onCharacterAdded)
	173.	
	174.	 
	175.	if player.Character then
	176.	
	177.	    onCharacterAdded(player.Character)
	178.	
	179.	end
	180.	
	181.	 
	182.	 
	183.	Tabs.Main:AddButton({
	184.	
	185.	    Title = "Invisible",
	186.	
	187.	    Description = "Use Invisibility Cloak",
	188.	
	189.	    Callback = function()
	190.	
	191.	        local player = game.Players.LocalPlayer
	192.	
	193.	        local character = player.Character or player.CharacterAdded:Wait()
	194.	
	195.	        local cloak = character:FindFirstChild("Invisibility Cloak")
	196.	
	197.	        if cloak and cloak:GetAttribute("SpeedModifier") == 2 then
	198.	
	199.	            cloak.Parent = workspace
	200.	
	201.	        else
	202.	
	203.	            Fluent:Notify({ Title = "Stellar", Content = "Use Invisibility Cloak First", Duration = 2 })
	204.	
	205.	        end
	206.	
	207.	    end
	208.	
	209.	})
	210.	
	211.	 
	212.	 
	213.	-- ESP
	214.	
	215.	 
	216.	 
	217.	local Players = game:GetService("Players")
	218.	
	219.	local RunService = game:GetService("RunService")
	220.	
	221.	 
	222.	local espEnabled = false
	223.	
	224.	local espInstances = {}
	225.	
	226.	 
	227.	local function createESP(player)
	228.	
	229.	    if not espEnabled then return end
	230.	
	231.	    if player == Players.LocalPlayer then return end
	232.	
	233.	 
	234.	    local character = player.Character
	235.	
	236.	    if not character then return end
	237.	
	238.	 
	239.	    local humanoidRootPart = character:WaitForChild("HumanoidRootPart", 10)
	240.	
	241.	    if not humanoidRootPart then return end
	242.	
	243.	 
	244.	    local billboard = Instance.new("BillboardGui")
	245.	
	246.	    billboard.Name = "ESP_" .. player.Name
	247.	
	248.	    billboard.AlwaysOnTop = true
	249.	
	250.	    billboard.Size = UDim2.new(0, 200, 0, 30)
	251.	
	252.	    billboard.StudsOffset = Vector3.new(0, 3, 0)
	253.	
	254.	    billboard.Adornee = humanoidRootPart
	255.	
	256.	    billboard.Parent = humanoidRootPart
	257.	
	258.	 
	259.	    local textLabel = Instance.new("TextLabel")
	260.	
	261.	    textLabel.Name = "NameLabel"
	262.	
	263.	    textLabel.Size = UDim2.new(1, 0, 1, 0)
	264.	
	265.	    textLabel.BackgroundTransparency = 1
	266.	
	267.	    textLabel.Text = player.DisplayName
	268.	
	269.	    textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
	270.	
	271.	    textLabel.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
	272.	
	273.	    textLabel.TextStrokeTransparency = 0
	274.	
	275.	    textLabel.TextScaled = true
	276.	
	277.	    textLabel.Font = Enum.Font.GothamBold
	278.	
	279.	    textLabel.Parent = billboard
	280.	
	281.	 
	282.	    espInstances[player] = billboard
	283.	
	284.	 
	285.	    local function onCharacterAdded(newCharacter)
	286.	
	287.	        if billboard then billboard:Destroy() end
	288.	
	289.	 
	290.	        humanoidRootPart = newCharacter:WaitForChild("HumanoidRootPart", 10)
	291.	
	292.	        if humanoidRootPart and espEnabled then
	293.	
	294.	            billboard.Adornee = humanoidRootPart
	295.	
	296.	            billboard.Parent = humanoidRootPart
	297.	
	298.	        end
	299.	
	300.	    end
	301.	
	302.	 
	303.	    player.CharacterAdded:Connect(onCharacterAdded)
	304.	
	305.	end
	306.	
	307.	 
	308.	local function removeESP(player)
	309.	
	310.	    local espInstance = espInstances[player]
	311.	
	312.	    if espInstance then
	313.	
	314.	        espInstance:Destroy()
	315.	
	316.	        espInstances[player] = nil
	317.	
	318.	    end
	319.	
	320.	end
	321.	
	322.	 
	323.	local function toggleESP(enable)
	324.	
	325.	    espEnabled = enable
	326.	
	327.	    if enable then
	328.	
	329.	        for _, player in ipairs(Players:GetPlayers()) do
	330.	
	331.	            if player ~= Players.LocalPlayer then
	332.	
	333.	                coroutine.wrap(function()
	334.	
	335.	                    createESP(player)
	336.	
	337.	                end)()
	338.	
	339.	            end
	340.	
	341.	        end
	342.	
	343.	    else
	344.	
	345.	        for player, espInstance in pairs(espInstances) do
	346.	
	347.	            if espInstance then
	348.	
	349.	                espInstance:Destroy()
	350.	
	351.	            end
	352.	
	353.	        end
	354.	
	355.	        espInstances = {}
	356.	
	357.	    end
	358.	
	359.	end
	360.	
	361.	 
	362.	local function initPlayerConnections()
	363.	
	364.	    Players.PlayerAdded:Connect(function(player)
	365.	
	366.	        player.CharacterAdded:Connect(function(character)
	367.	
	368.	            if player ~= Players.LocalPlayer and espEnabled then
	369.	
	370.	                task.wait(1)
	371.	
	372.	                createESP(player)
	373.	
	374.	            end
	375.	
	376.	        end)
	377.	
	378.	    end)
	379.	
	380.	 
	381.	    Players.PlayerRemoving:Connect(removeESP)
	382.	
	383.	end
	384.	
	385.	 
	386.	initPlayerConnections()
	387.	
	388.	 
	389.	local RaritySettings = {
	390.	
	391.	    ["Legendary"] = {
	392.	
	393.	        Color = Color3.new(1, 1, 0),
	394.	
	395.	        Size = UDim2.new(0, 150, 0, 50)
	396.	
	397.	    },
	398.	
	399.	    ["Mythic"] = {
	400.	
	401.	        Color = Color3.new(1, 0, 0),
	402.	
	403.	        Size = UDim2.new(0, 150, 0, 50)
	404.	
	405.	    },
	406.	
	407.	    ["Brainrot God"] = {
	408.	
	409.	        Color = Color3.new(0.5, 0, 0.5),
	410.	
	411.	        Size = UDim2.new(0, 180, 0, 60)
	412.	
	413.	    },
	414.	
	415.	    ["Secret"] = {
	416.	
	417.	        Color = Color3.new(0, 0, 0),
	418.	
	419.	        Size = UDim2.new(0, 200, 0, 70)
	420.	
	421.	    }
	422.	
	423.	}
	424.	
	425.	 
	426.	local MutationSettings = {
	427.	
	428.	    ["Gold"] = {
	429.	
	430.	        Color = Color3.fromRGB(255, 215, 0),
	431.	
	432.	        Size = UDim2.new(0, 120, 0, 30)
	433.	
	434.	    },
	435.	
	436.	 
	437.	    ["Diamond"] = {
	438.	
	439.	        Color = Color3.fromRGB(0, 191, 255),
	440.	
	441.	        Size = UDim2.new(0, 120, 0, 30)
	442.	
	443.	    },
	444.	
	445.	 
	446.	    ["Rainbow"] = {
	447.	
	448.	        Color = Color3.fromRGB(255, 192, 203),
	449.	
	450.	        Size = UDim2.new(0, 120, 0, 30)
	451.	
	452.	    },
	453.	
	454.	 
	455.	    ["Bloodrot"] = {
	456.	
	457.	        Color = Color3.fromRGB(139, 0, 0),
	458.	
	459.	        Size = UDim2.new(0, 120, 0, 30)
	460.	
	461.	    }
	462.	
	463.	}
	464.	
	465.	 
	466.	local activeESP = {}
	467.	
	468.	local activeLockTimeEsp = false
	469.	
	470.	local lteInstances = {}
	471.	
	472.	 
	473.	local function updatelock()
	474.	
	475.	    if not activeLockTimeEsp then
	476.	
	477.	        for _, instance in pairs(lteInstances) do
	478.	
	479.	            if instance then
	480.	
	481.	                instance:Destroy()
	482.	
	483.	            end
	484.	
	485.	        end
	486.	
	487.	        lteInstances = {}
	488.	
	489.	        return
	490.	
	491.	    end
	492.	
	493.	 
	494.	    for _, plot in pairs(workspace.Plots:GetChildren()) do
	495.	
	496.	        local timeLabel = plot:FindFirstChild("Purchases", true) and 
	497.	
	498.	        plot.Purchases:FindFirstChild("PlotBlock", true) and
	499.	
	500.	        plot.Purchases.PlotBlock.Main:FindFirstChild("BillboardGui", true) and
	501.	
	502.	        plot.Purchases.PlotBlock.Main.BillboardGui:FindFirstChild("RemainingTime", true)
	503.	
	504.	 
	505.	        if timeLabel and timeLabel:IsA("TextLabel") then
	506.	
	507.	            local espName = "LockTimeESP_" .. plot.Name
	508.	
	509.	            local existingBillboard = plot:FindFirstChild(espName)
	510.	
	511.	 
	512.	            local isUnlocked = timeLabel.Text == "0s"
	513.	
	514.	            local displayText = isUnlocked and "Unlocked" or ("Lock: " .. timeLabel.Text)
	515.	
	516.	 
	517.	            local textColor
	518.	
	519.	            if plot.Name == plotName then
	520.	
	521.	                textColor = isUnlocked and Color3.fromRGB(0, 255, 0)
	522.	
	523.	                            or Color3.fromRGB(0, 255, 0)
	524.	
	525.	            else
	526.	
	527.	                textColor = isUnlocked and Color3.fromRGB(220, 20, 60)
	528.	
	529.	                            or Color3.fromRGB(255, 255, 0)
	530.	
	531.	            end
	532.	
	533.	 
	534.	            if not existingBillboard then
	535.	
	536.	                local billboard = Instance.new("BillboardGui")
	537.	
	538.	                billboard.Name = espName
	539.	
	540.	                billboard.Size = UDim2.new(0, 200, 0, 30)
	541.	
	542.	                billboard.StudsOffset = Vector3.new(0, 5, 0)
	543.	
	544.	                billboard.AlwaysOnTop = true
	545.	
	546.	                billboard.Adornee = plot.Purchases.PlotBlock.Main
	547.	
	548.	 
	549.	                local label = Instance.new("TextLabel")
	550.	
	551.	                label.Text = displayText
	552.	
	553.	                label.Size = UDim2.new(1, 0, 1, 0)
	554.	
	555.	                label.BackgroundTransparency = 1
	556.	
	557.	                label.TextScaled = true
	558.	
	559.	                label.TextColor3 = textColor
	560.	
	561.	                label.TextStrokeColor3 = Color3.new(0, 0, 0)
	562.	
	563.	                label.TextStrokeTransparency = 0
	564.	
	565.	                label.Font = Enum.Font.SourceSansBold
	566.	
	567.	                label.Parent = billboard
	568.	
	569.	 
	570.	                billboard.Parent = plot
	571.	
	572.	                lteInstances[plot.Name] = billboard
	573.	
	574.	            else
	575.	
	576.	                existingBillboard.TextLabel.Text = displayText
	577.	
	578.	                existingBillboard.TextLabel.TextColor3 = textColor
	579.	
	580.	            end
	581.	
	582.	        end
	583.	
	584.	    end
	585.	
	586.	end
	587.	
	588.	 
	589.	local function updateRESP()
	590.	
	591.	    for _, plot in pairs(workspace.Plots:GetChildren()) do
	592.	
	593.	        if plot.Name ~= plotName then
	594.	
	595.	            for _, child in pairs(plot:GetDescendants()) do
	596.	
	597.	                if child.Name == "Rarity" and child:IsA("TextLabel") and RaritySettings[child.Text] then
	598.	
	599.	                    local parentModel = child.Parent.Parent
	600.	
	601.	                    local espName = child.Text.."_ESP"
	602.	
	603.	                    local mutationEspName = "Mutation_ESP"
	604.	
	605.	                    local existingBillboard = parentModel:FindFirstChild(espName)
	606.	
	607.	                    local existingMutationBillboard = parentModel:FindFirstChild(mutationEspName)
	608.	
	609.	 
	610.	                    if activeESP[child.Text] then
	611.	
	612.	                        if not existingBillboard then
	613.	
	614.	                            local settings = RaritySettings[child.Text]
	615.	
	616.	 
	617.	                            local billboard = Instance.new("BillboardGui")
	618.	
	619.	                            billboard.Name = espName
	620.	
	621.	                            billboard.Size = settings.Size
	622.	
	623.	                            billboard.StudsOffset = Vector3.new(0, 3, 0)
	624.	
	625.	                            billboard.AlwaysOnTop = true
	626.	
	627.	 
	628.	                            local label = Instance.new("TextLabel")
	629.	
	630.	                            label.Text = child.Parent.DisplayName.Text
	631.	
	632.	                            label.Size = UDim2.new(1, 0, 1, 0)
	633.	
	634.	                            label.BackgroundTransparency = 1
	635.	
	636.	                            label.TextScaled = true
	637.	
	638.	                            label.TextColor3 = settings.Color
	639.	
	640.	                            label.TextStrokeColor3 = Color3.new(0, 0, 0)
	641.	
	642.	                            label.TextStrokeTransparency = 0
	643.	
	644.	                            label.Font = Enum.Font.SourceSansBold
	645.	
	646.	 
	647.	                            label.Parent = billboard
	648.	
	649.	                            billboard.Parent = parentModel
	650.	
	651.	                        end
	652.	
	653.	 
	654.	                        local mutation = child.Parent:FindFirstChild("Mutation")
	655.	
	656.	                        if mutation and mutation:IsA("TextLabel") and MutationSettings[mutation.Text] then
	657.	
	658.	                            local mutationSettings = MutationSettings[mutation.Text]
	659.	
	660.	 
	661.	                            if not existingMutationBillboard then
	662.	
	663.	                                local mutationBillboard = Instance.new("BillboardGui")
	664.	
	665.	                                mutationBillboard.Name = mutationEspName
	666.	
	667.	                                mutationBillboard.Size = mutationSettings.Size
	668.	
	669.	                                mutationBillboard.StudsOffset = Vector3.new(0, 6, 0)
	670.	
	671.	                                mutationBillboard.AlwaysOnTop = true
	672.	
	673.	 
	674.	                                local mutationLabel = Instance.new("TextLabel")
	675.	
	676.	                                mutationLabel.Text = mutation.Text
	677.	
	678.	                                mutationLabel.Size = UDim2.new(1, 0, 1, 0)
	679.	
	680.	                                mutationLabel.BackgroundTransparency = 1
	681.	
	682.	                                mutationLabel.TextScaled = true
	683.	
	684.	                                mutationLabel.TextColor3 = mutationSettings.Color
	685.	
	686.	                                mutationLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
	687.	
	688.	                                mutationLabel.TextStrokeTransparency = 0
	689.	
	690.	                                mutationLabel.Font = Enum.Font.SourceSansBold
	691.	
	692.	 
	693.	                                mutationLabel.Parent = mutationBillboard
	694.	
	695.	                                mutationBillboard.Parent = parentModel
	696.	
	697.	                            else
	698.	
	699.	                                existingMutationBillboard.TextLabel.Text = mutation.Text
	700.	
	701.	                                existingMutationBillboard.TextLabel.TextColor3 = mutationSettings.Color
	702.	
	703.	                            end
	704.	
	705.	                        elseif existingMutationBillboard then
	706.	
	707.	                            existingMutationBillboard:Destroy()
	708.	
	709.	                        end
	710.	
	711.	                    else
	712.	
	713.	                        if existingBillboard then
	714.	
	715.	                            existingBillboard:Destroy()
	716.	
	717.	                        end
	718.	
	719.	                        if existingMutationBillboard then
	720.	
	721.	                            existingMutationBillboard:Destroy()
	722.	
	723.	                        end
	724.	
	725.	                    end
	726.	
	727.	                end
	728.	
	729.	            end
	730.	
	731.	        end
	732.	
	733.	    end
	734.	
	735.	end
	736.	
	737.	 
	738.	local MultiDropdown = Tabs.Main:AddDropdown("MultiDropdown", {
	739.	
	740.	    Title = "Esp",
	741.	
	742.	    Values = {"Lock", "Players", "Legendary", "Mythic", "Brainrot God", "Secret",},
	743.	
	744.	    Multi = true,
	745.	
	746.	    Default = {},
	747.	
	748.	})
	749.	
	750.	 
	751.	MultiDropdown:OnChanged(function(Value)
	752.	
	753.	    if Value["Players"] then
	754.	
	755.	        toggleESP(true)
	756.	
	757.	    else
	758.	
	759.	        toggleESP(false)
	760.	
	761.	    end
	762.	
	763.	    activeESP["Legendary"] = Value["Legendary"] or false
	764.	
	765.	    activeESP["Mythic"] = Value["Mythic"] or false
	766.	
	767.	    activeESP["Brainrot God"] = Value["Brainrot God"] or false
	768.	
	769.	    activeESP["Secret"] = Value["Secret"] or false
	770.	
	771.	 
	772.	    activeLockTimeEsp = Value["Lock"] or false
	773.	
	774.	    updatelock()
	775.	
	776.	 
	777.	    updateRESP()
	778.	
	779.	 
	780.	end)
	781.	
	782.	 
	783.	task.spawn(function()
	784.	
	785.	    while true do
	786.	
	787.	        task.wait(0.25)
	788.	
	789.	        if activeLockTimeEsp then
	790.	
	791.	            updatelock()
	792.	
	793.	        end
	794.	
	795.	        if next(activeESP) ~= nil then
	796.	
	797.	            updateRESP()
	798.	
	799.	        end
	800.	
	801.	    end
	802.	
	803.	end)
	804.	
	805.	 
	806.	Tabs.Main:AddKeybind("Keybind", {
	807.	
	808.	    Title = "Steal Keybind",
	809.	
	810.	    Mode = "Toggle",
	811.	
	812.	    Default = "G",
	813.	
	814.	    Callback = function(Value)
	815.	
	816.	        local player = game.Players.LocalPlayer
	817.	
	818.	        local pos = CFrame.new(0, -500, 0)
	819.	
	820.	        local startT = os.clock()
	821.	
	822.	        while os.clock() - startT < 1 do
	823.	
	824.	            if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
	825.	
	826.	                player.Character.HumanoidRootPart.CFrame = pos
	827.	
	828.	            end
	829.	
	830.	            task.wait()
	831.	
	832.	        end
	833.	
	834.	    end,
	835.	
	836.	})
	837.	
	838.	 
	839.	Tabs.Main:AddKeybind("Keybind", {
	840.	
	841.	    Title = "Shop",
	842.	
	843.	    Mode = "Toggle",
	844.	
	845.	    Default = "F",
	846.	
	847.	    Description = "Opens/Closes shop",
	848.	
	849.	    Callback = function(Value)
	850.	
	851.	        shop.Visible = Value
	852.	
	853.	        shop.Position = Value and UDim2.new(0.5, 0, 0.5, 0) or UDim2.new(0.5, 0, 1.5, 0)
	854.	
	855.	    end,
	856.	
	857.	})
	858.	
	859.	 
	860.	 
	861.	 
	862.	-- SERVER
	863.	
	864.	 
	865.	local petModels = game:GetService("ReplicatedStorage").Models.Animals:GetChildren()
	866.	
	867.	 
	868.	local petNames = {}
	869.	
	870.	for _, pet in ipairs(petModels) do
	871.	
	872.	    table.insert(petNames, pet.Name)
	873.	
	874.	end
	875.	
	876.	 
	877.	local MultiDropdown = Tabs.Server:AddDropdown("MultiDropdown", {
	878.	
	879.	    Title = "Pet Finder",
	880.	
	881.	    Values = petNames,
	882.	
	883.	    Multi = true,
	884.	
	885.	    Default = {},
	886.	
	887.	})
	888.	
	889.	 
	890.	local function getOwner(plot)
	891.	
	892.	    local text = plot:FindFirstChild("PlotSign") and 
	893.	
	894.	    plot.PlotSign:FindFirstChild("SurfaceGui") and 
	895.	
	896.	    plot.PlotSign.SurfaceGui.Frame.TextLabel.Text or "Unknown"
	897.	
	898.	    return text:match("^(.-)'s Base") or text
	899.	
	900.	end
	901.	
	902.	 
	903.	local myPlotName
	904.	
	905.	for _, plot in ipairs(workspace.Plots:GetChildren()) do
	906.	
	907.	    if plot:FindFirstChild("YourBase", true).Enabled then
	908.	
	909.	        myPlotName = plot.Name
	910.	
	911.	        break
	912.	
	913.	    end
	914.	
	915.	end
	916.	
	917.	 
	918.	local Rparagraph = Tabs.Server:AddParagraph({
	919.	
	920.	    Title = "No pets selected",
	921.	
	922.	})
	923.	
	924.	 
	925.	local SelectedPets = {}
	926.	
	927.	local isRunning = false
	928.	
	929.	local lnt = 0
	930.	
	931.	local nc = 5
	932.	
	933.	 
	934.	MultiDropdown:OnChanged(function(SelectedPetss)
	935.	
	936.	    SelectedPets = {}
	937.	
	938.	    for petName, isSelected in pairs(SelectedPetss) do
	939.	
	940.	        if isSelected then
	941.	
	942.	            table.insert(SelectedPets, petName)
	943.	
	944.	        end
	945.	
	946.	    end
	947.	
	948.	 
	949.	    if not isRunning and #SelectedPets > 0 then
	950.	
	951.	        isRunning = true
	952.	
	953.	        task.spawn(function()
	954.	
	955.	            local lastResults = {}
	956.	
	957.	 
	958.	            while #SelectedPets > 0 do
	959.	
	960.	                local counts = {}
	961.	
	962.	                local found = false
	963.	
	964.	                local newPetsFound = false
	965.	
	966.	 
	967.	                for _, plot in pairs(workspace.Plots:GetChildren()) do
	968.	
	969.	                    if plot.Name ~= myPlotName then
	970.	
	971.	                        local owner = getOwner(plot)
	972.	
	973.	                        for _, v in pairs(plot:GetDescendants()) do
	974.	
	975.	                            if v.Name == "DisplayName" and table.find(SelectedPets, v.Text) then
	976.	
	977.	                                counts[owner] = counts[owner] or {}
	978.	
	979.	                                counts[owner][v.Text] = (counts[owner][v.Text] or 0) + 1
	980.	
	981.	                                found = true
	982.	
	983.	 
	984.	                                if not lastResults[owner] or not lastResults[owner][v.Text] then
	985.	
	986.	                                    newPetsFound = true
	987.	
	988.	                                end
	989.	
	990.	                            end
	991.	
	992.	                        end
	993.	
	994.	                    end
	995.	
	996.	                end
	997.	
	998.	 
	999.	                if found then
	1000.	
	1001.	                    local resultText = ""
	1002.	
	1003.	                    for owner, pets in pairs(counts) do
	1004.	
	1005.	                        for name, count in pairs(pets) do
	1006.	
	1007.	                            resultText = resultText .. name.." x"..count.." | Owner: "..owner.."\n"
	1008.	
	1009.	 
	1010.	                            if newPetsFound and (os.time() - lnt) > nc then
	1011.	
	1012.	                                Fluent:Notify({
	1013.	
	1014.	                                    Title = "Pet Finder",
	1015.	
	1016.	                                    Content = "Found "..name.." x"..count.." Owner: "..owner,
	1017.	
	1018.	                                    Duration = 2
	1019.	
	1020.	                                })
	1021.	
	1022.	                                lnt = os.time()
	1023.	
	1024.	                            end
	1025.	
	1026.	                        end
	1027.	
	1028.	                    end
	1029.	
	1030.	                    Rparagraph:SetTitle(resultText)
	1031.	
	1032.	                else
	1033.	
	1034.	                    Rparagraph:SetTitle("No selected pets found")
	1035.	
	1036.	                end
	1037.	
	1038.	 
	1039.	                lastResults = counts
	1040.	
	1041.	                task.wait(0.5)
	1042.	
	1043.	            end
	1044.	
	1045.	 
	1046.	            isRunning = false
	1047.	
	1048.	            Rparagraph:SetTitle("No pets selected")
	1049.	
	1050.	        end)
	1051.	
	1052.	    elseif #SelectedPets == 0 then
	1053.	
	1054.	        Rparagraph:SetTitle("No pets selected")
	1055.	
	1056.	    end
	1057.	
	1058.	end)
	1059.	
	1060.	 
	1061.	 
	1062.	Tabs.Server:AddSection("Other")
	1063.	
	1064.	 
	1065.	 
	1066.	Tabs.Server:AddButton({
	1067.	
	1068.	    Title = "Server Hop",
	1069.	
	1070.	    Description = "Joins a Different Server",
	1071.	
	1072.	    Callback = function()
	1073.	
	1074.	        local PlaceID = game.PlaceId
	1075.	
	1076.	        local AllIDs = {}
	1077.	
	1078.	        local foundAnything = ""
	1079.	
	1080.	        local actualHour = os.date("!*t").hour
	1081.	
	1082.	        local Deleted = false
	1083.	
	1084.	        local File = pcall(function()
	1085.	
	1086.	            AllIDs = game:GetService('HttpService'):JSONDecode(readfile("NotSameServers.json"))
	1087.	
	1088.	        end)
	1089.	
	1090.	        if not File then
	1091.	
	1092.	            table.insert(AllIDs, actualHour)
	1093.	
	1094.	            writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
	1095.	
	1096.	        end
	1097.	
	1098.	        function TPReturner()
	1099.	
	1100.	            local Site;
	1101.	
	1102.	            if foundAnything == "" then
	1103.	
	1104.	                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
	1105.	
	1106.	            else
	1107.	
	1108.	                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
	1109.	
	1110.	            end
	1111.	
	1112.	            local ID = ""
	1113.	
	1114.	            if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
	1115.	
	1116.	                foundAnything = Site.nextPageCursor
	1117.	
	1118.	            end
	1119.	
	1120.	            local num = 0;
	1121.	
	1122.	            for _,v in pairs(Site.data) do
	1123.	
	1124.	                local Possible = true
	1125.	
	1126.	                ID = tostring(v.id)
	1127.	
	1128.	                if tonumber(v.maxPlayers) > tonumber(v.playing) then
	1129.	
	1130.	                    for _,Existing in pairs(AllIDs) do
	1131.	
	1132.	                        if num ~= 0 then
	1133.	
	1134.	                            if ID == tostring(Existing) then
	1135.	
	1136.	                                Possible = false
	1137.	
	1138.	                                end
	1139.	
	1140.	                            else
	1141.	
	1142.	                                if tonumber(actualHour) ~= tonumber(Existing) then
	1143.	
	1144.	                                    local delFile = pcall(function()
	1145.	
	1146.	                                        delfile("NotSameServers.json")
	1147.	
	1148.	                                        AllIDs = {}
	1149.	
	1150.	                                        table.insert(AllIDs, actualHour)
	1151.	
	1152.	                                        end)
	1153.	
	1154.	                                    end
	1155.	
	1156.	                                end
	1157.	
	1158.	                            num = num + 1
	1159.	
	1160.	                        end
	1161.	
	1162.	                    if Possible == true then
	1163.	
	1164.	                        table.insert(AllIDs, ID)
	1165.	
	1166.	                        task.wait()
	1167.	
	1168.	                        pcall(function()
	1169.	
	1170.	                            writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
	1171.	
	1172.	                            task.wait()
	1173.	
	1174.	                            game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
	1175.	
	1176.	                        end)
	1177.	
	1178.	                task.wait(4)
	1179.	
	1180.	            end
	1181.	
	1182.	        end
	1183.	
	1184.	    end
	1185.	
	1186.	end
	1187.	
	1188.	function Teleport()
	1189.	
	1190.	    while task.wait() do
	1191.	
	1192.	        pcall(function()
	1193.	
	1194.	            TPReturner()
	1195.	
	1196.	            if foundAnything ~= "" then
	1197.	
	1198.	                TPReturner()
	1199.	
	1200.	            end
	1201.	
	1202.	        end)
	1203.	
	1204.	    end
	1205.	
	1206.	end
	1207.	
	1208.	Teleport()
	1209.	
	1210.	    end
	1211.	
	1212.	})
	1213.	
	1214.	 
	1215.	Tabs.Server:AddButton({
	1216.	
	1217.	    Title = "Rejoin",
	1218.	
	1219.	    Description = "Rejoins The Same Server",
	1220.	
	1221.	    Callback = function()
	1222.	
	1223.	        local ts = game:GetService("TeleportService")
	1224.	
	1225.	        local p = game:GetService("Players").LocalPlayer
	1226.	
	1227.	        ts:TeleportToPlaceInstance(game.PlaceId, game.JobId, p)
	1228.	
	1229.	    end
	1230.	
	1231.	})
	1232.	
	1233.	 
	1234.	 
	1235.	local Timer = Tabs.Updates:AddParagraph({ Title = "Time: 00:00:00" })
	1236.	
	1237.	local st = os.time()
	1238.	
	1239.	 
	1240.	task.spawn(function()
	1241.	
	1242.	    while true do
	1243.	
	1244.	        local et = os.difftime(os.time(), st)
	1245.	
	1246.	        Timer:SetTitle(string.format("Time: %02d:%02d:%02d", math.floor(et / 3600), math.floor((et % 3600) / 60), et % 60))
	1247.	
	1248.	        task.wait(1)
	1249.	
	1250.	    end
	1251.	
	1252.	end)
	1253.	
	1254.	 
	1255.	Tabs.Updates:AddButton({
	1256.	
	1257.	    Title = "Discord Server",
	1258.	
	1259.	    Description = "Copies Discord Invite Link",
	1260.	
	1261.	    Callback = function()
	1262.	
	1263.	        setclipboard("WASHEDZ IS SLICK")
	1264.	
	1265.	        Fluent:Notify({ Title = "Stellar", Content = "Copied Successfully", Duration = 2 })
	1266.	
	1267.	    end
	1268.	
	1269.	})
	1270.	
	1271.	 
	1272.	Tabs.Updates:AddButton({
	1273.	
	1274.	    Title = "Run Infinite Yield",
	1275.	
	1276.	    Callback = function()
	1277.	
	1278.	        loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
	1279.	
	1280.	    end
	1281.	
	1282.	})
	1283.	
	1284.	 
	1285.	game:GetService('Players').LocalPlayer.Idled:Connect(function()
	1286.	
	1287.	    game:GetService('VirtualUser'):CaptureController()
	1288.	
	1289.	    game:GetService('VirtualUser'):ClickButton2(Vector2.new())
	1290.	
	1291.	end)
	1292.	
	1293.	 
	1294.	loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()
	1295.	
	1296.	 
	1297.	SaveManager:SetLibrary(Fluent)
	1298.	
	1299.	SaveManager:BuildConfigSection(Tabs.Settings)
	1300.	
	1301.	SaveManager:LoadAutoloadConfig()
	1302.	
	1303.	 
	1304.	Window:SelectTab(1)
	1305.	
	1306.	 
