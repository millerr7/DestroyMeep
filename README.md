local Players = game:GetService("Players")

-- Lista de IDs de usuários autorizados
local authorizedUsers = {
    1802711930, -- Miller
    7725083309, -- Tie
    1185053847, -- Alemao
    748889121 -- Noah
}

local player = Players.LocalPlayer

-- Verifica se o jogador está na lista
local function isUserAuthorized(userId)
    for _, id in ipairs(authorizedUsers) do
        if userId == id then
            return true
        end
    end
    return false
end

if not isUserAuthorized(player.UserId) then
    -- Encerra o script se o usuário não estiver autorizado
    game:GetService("StarterGui"):SetCore("SendNotification", {
        Title = "Acesso Negado",
        Text = "Você não tem permissão para usar este script!",
        Duration = 5
    })
    return -- Para a execução do script
end

print("Usuário autorizado! Carregando o script...")

local function service(...) return game:GetService(...) end
local Players = service("Players")
local MarketplaceService = service("MarketplaceService")
local ReplicatedStorage = service("ReplicatedStorage")
local HttpService = service("HttpService")
local Constants = require(ReplicatedStorage:WaitForChild("Constants"))
local Connection = ReplicatedStorage:WaitForChild("Connection")
local ConnectionEvent = ReplicatedStorage:WaitForChild("ConnectionEvent")
local player = game.Players.LocalPlayer
local MarketplaceService = game:GetService("MarketplaceService")
local executorName = identifyexecutor()
local gameName = MarketplaceService:GetProductInfo(game.PlaceId).Name
local openingSound = Instance.new("Sound")
openingSound.SoundId = "rbxassetid://6958727243" 
openingSound.Volume = 5 
openingSound.PlayOnRemove = false
openingSound.Looped = false
openingSound.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui") 

local function playOpeningSound()
    openingSound:Play()
end

playOpeningSound()
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "👾MeepCity👾",
   Icon = 106006409982737, 
   LoadingTitle = "DestroyMeep Premium",
   LoadingSubtitle = "Carregando...",
   Theme = {Default},

   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false,

   ConfigurationSaving = {
      Enabled = false,
      FolderName = nil,
      FileName = "Big Hub"
   },

   Discord = {
      Enabled = true,
      Invite = "jbbg_777",
      RememberJoins = true
   },

   KeySystem = true,
   KeySettings = {
      Title = "DestroyMeep Premium",
      Subtitle = "Key System",
      Note = ".gg/valkyres",
      FileName = "examplekey",
      SaveKey = true,
      GrabKeyFromSite = true,
      Key = {"valkyresnotopo"}
   }
})

local MainTab = Window:CreateTab("Meepcity", 105651797171702)-- Título, Imagem
local MainSection = MainTab:CreateSection("Meepcity")

Rayfield:Notify({
   Title = "Feito por Miller",
   Content = "dc: confused3",
   Duration = 6.5,
   Image = 85473985380115,
})

local Button = MainTab:CreateButton({
   Name = "Itens fora de mercado",
   Callback = function()
      loadstring(game:HttpGet('https://raw.githubusercontent.com/yLegendzz/Scripts/main/Meepcity'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Falsificar Plus/Boombox/Candypack",
   Callback = function()
      local player = game.Players.LocalPlayer

-- Falsificar PLUS/BOOMBOX/CANDYPACK
local function falsificarPlusBoomBoxCandyPack(valor)
    if valor then
        player:SetAttribute("PLUS", true)
        player:SetAttribute("BoomBox", true)
        player:SetAttribute("CandyPack", true)
    else
        player:SetAttribute("PLUS", false)
        player:SetAttribute("BoomBox", false)
        player:SetAttribute("CandyPack", false)
    end
end

-- Chamar a função diretamente com o valor desejado
falsificarPlusBoomBoxCandyPack(true)  -- Para ativar
-- falsificarPlusBoomBoxCandyPack(false) -- Para desativar
   end,
})

local RunService = game:GetService("RunService")
local player = game.Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = char:WaitForChild("HumanoidRootPart")
local TPWalkEnabled = false -- Controle de ativação
local TPWalkConnection = nil -- Conexão para o loop
local TPWalkSpeed = 10 -- Velocidade inicial

-- Atualiza o personagem caso ele seja recriado
player.CharacterAdded:Connect(function(newChar)
    char = newChar
    humanoidRootPart = char:WaitForChild("HumanoidRootPart")
end)

-- Função para iniciar/parar o TPWalk
local function toggleTPWalk(enabled)
    if TPWalkConnection then
        TPWalkConnection:Disconnect()
        TPWalkConnection = nil
    end

    if enabled and TPWalkSpeed > 0 then
        TPWalkConnection = RunService.Stepped:Connect(function()
            if char and humanoidRootPart and char:FindFirstChild("Humanoid") then
                local moveDirection = char.Humanoid.MoveDirection
                if moveDirection.Magnitude > 0 then
                    humanoidRootPart.CFrame = humanoidRootPart.CFrame + (moveDirection * TPWalkSpeed * 0.1)
                end
            end
        end)
    end
end

-- Slider para ajustar a velocidade do TPWalk
local Slider = MainTab:CreateSlider({
    Name = "Velocidade de TPWalk",
    Range = {0, 50}, -- Inclui 0 para desativar o movimento
    Increment = 1,
    Suffix = " studs",
    CurrentValue = TPWalkSpeed, -- Velocidade inicial
    Flag = "TPWalkSpeed",
    Callback = function(value)
        TPWalkSpeed = value
        if TPWalkEnabled then
            toggleTPWalk(true) -- Atualiza o movimento caso esteja ativado
        end
    end,
})

-- Botão para ativar/desativar o TPWalk
local Button = MainTab:CreateButton({
    Name = "Ativar/Desativar TPWalk",
    Callback = function()
        TPWalkEnabled = not TPWalkEnabled -- Inverte o estado atual
        toggleTPWalk(TPWalkEnabled)
        Rayfield:Notify({
            Title = "TPWalk",
            Content = TPWalkEnabled and "Ativado!" or "Desativado!",
            Duration = 5,
        })
    end,
})

local Button = MainTab:CreateButton({
   Name = "Tamanho Ilimitado de Sussurro",
   Callback = function()
        if Constants and Constants.STATS then
            Constants.STATS.WHISPER_MAX_CHARACTERS = math.huge
        else
            warn("Erro: Estrutura Constants.STATS não encontrada!")
        end
    end
})

local Button = MainTab:CreateButton({
   Name = "Synolope",
   Callback = function()
      loadstring(game:HttpGet('https://rawscripts.net/raw/MeepCity-MeepCity-OP-GUI-(TONS-OF-OP-FEATURES)-1629'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "MeepCracked",
   Callback = function()
      loadstring(game:HttpGet('https://rawscripts.net/raw/MeepCity-Meepcity-cracked-6349'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Girar caixa",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/XiMMHZ2K'))()
   end,
})

local MainTab = Window:CreateTab("Destroy",101037411679101)

local Button = MainTab:CreateButton({
   Name = "LAG",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/AWurbmb7'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Dar itens",
   Callback = function()
       -- Gui to Lua
-- Version: 3.2

-- Instances:

local ScreenGui = Instance.new("ScreenGui")
local Ui = Instance.new("Frame")
local TextBox = Instance.new("TextBox")
local TextLabel = Instance.new("TextLabel")
local TextButton = Instance.new("TextButton")
local TextButton_2 = Instance.new("TextButton")
local TextButton_3 = Instance.new("TextButton")
local TextButton_4 = Instance.new("TextButton")
local TextButton_5 = Instance.new("TextButton")
local TextButton_6 = Instance.new("TextButton")

--Properties:

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Ui.Name = "Ui"
Ui.Parent = ScreenGui
Ui.AnchorPoint = Vector2.new(0.5, 0.5)
Ui.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Ui.BorderColor3 = Color3.fromRGB(0, 0, 0)
Ui.BorderSizePixel = 0
Ui.Position = UDim2.new(0.5, 0, 0.5, 0)
Ui.Size = UDim2.new(0, 400, 0, 250)

TextBox.Parent = Ui
TextBox.BackgroundColor3 = Color3.fromRGB(162, 162, 162)
TextBox.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextBox.BorderSizePixel = 0
TextBox.Position = UDim2.new(0.037562713, 0, 0.167375669, 0)
TextBox.Size = UDim2.new(0, 369, 0, 35)
TextBox.ClearTextOnFocus = false
TextBox.Font = Enum.Font.SourceSans
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(0, 0, 0)
TextBox.TextScaled = true
TextBox.TextSize = 14.000
TextBox.TextWrapped = true

TextLabel.Parent = Ui
TextLabel.BackgroundColor3 = Color3.fromRGB(197, 197, 197)
TextLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.BorderSizePixel = 0
TextLabel.Size = UDim2.new(0, 400, 0, 27)
TextLabel.Font = Enum.Font.SourceSansBold
TextLabel.Text = "By Miller"
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextSize = 20.000

TextButton.Parent = Ui
TextButton.BackgroundColor3 = Color3.fromRGB(159, 0, 0)
TextButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.0363163762, 0, 0.495375782, 0)
TextButton.Size = UDim2.new(0, 103, 0, 31)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "Dar Donut"
TextButton.TextColor3 = Color3.fromRGB(214, 214, 214)
TextButton.TextScaled = true
TextButton.TextSize = 14.000
TextButton.TextWrapped = true

TextButton_2.Parent = Ui
TextButton_2.BackgroundColor3 = Color3.fromRGB(159, 0, 0)
TextButton_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton_2.BorderSizePixel = 0
TextButton_2.Position = UDim2.new(0.0338160694, 0, 0.644345522, 0)
TextButton_2.Size = UDim2.new(0, 211, 0, 78)
TextButton_2.Font = Enum.Font.SourceSans
TextButton_2.Text = "Dar snowball"
TextButton_2.TextColor3 = Color3.fromRGB(214, 214, 214)
TextButton_2.TextScaled = true
TextButton_2.TextSize = 14.000
TextButton_2.TextWrapped = true

TextButton_3.Parent = Ui
TextButton_3.BackgroundColor3 = Color3.fromRGB(159, 0, 0)
TextButton_3.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton_3.BorderSizePixel = 0
TextButton_3.Position = UDim2.new(0.0363163762, 0, 0.339456618, 0)
TextButton_3.Size = UDim2.new(0, 103, 0, 31)
TextButton_3.Font = Enum.Font.SourceSans
TextButton_3.Text = "Dar água"
TextButton_3.TextColor3 = Color3.fromRGB(214, 214, 214)
TextButton_3.TextScaled = true
TextButton_3.TextSize = 14.000
TextButton_3.TextWrapped = true

TextButton_4.Parent = Ui
TextButton_4.BackgroundColor3 = Color3.fromRGB(159, 0, 0)
TextButton_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton_4.BorderSizePixel = 0
TextButton_4.Position = UDim2.new(0.304175258, 0, 0.339456618, 0)
TextButton_4.Size = UDim2.new(0, 103, 0, 31)
TextButton_4.Font = Enum.Font.SourceSans
TextButton_4.Text = "Dar livro"
TextButton_4.TextColor3 = Color3.fromRGB(214, 214, 214)
TextButton_4.TextScaled = true
TextButton_4.TextSize = 14.000
TextButton_4.TextWrapped = true

TextButton_5.Parent = Ui
TextButton_5.BackgroundColor3 = Color3.fromRGB(159, 0, 0)
TextButton_5.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton_5.BorderSizePixel = 0
TextButton_5.Position = UDim2.new(0.304175258, 0, 0.495375782, 0)
TextButton_5.Size = UDim2.new(0, 103, 0, 31)
TextButton_5.Font = Enum.Font.SourceSans
TextButton_5.Text = "Dar Curry"
TextButton_5.TextColor3 = Color3.fromRGB(214, 214, 214)
TextButton_5.TextScaled = true
TextButton_5.TextSize = 14.000
TextButton_5.TextWrapped = true

TextButton_6.Parent = Ui
TextButton_6.BackgroundColor3 = Color3.fromRGB(159, 0, 0)
TextButton_6.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton_6.BorderSizePixel = 0
TextButton_6.Position = UDim2.new(0.583816051, 0, 0.336345524, 0)
TextButton_6.Size = UDim2.new(0, 150, 0, 155)
TextButton_6.Font = Enum.Font.SourceSans
TextButton_6.Text = "Mudar skin (Skin Pronta)"
TextButton_6.TextColor3 = Color3.fromRGB(214, 214, 214)
TextButton_6.TextSize = 23.000
TextButton_6.TextWrapped = true

-- Scripts:

local function PIZCLXV_fake_script() -- Ui.drag 
	local script = Instance.new('LocalScript', Ui)

	local a=game:GetService("UserInputService")function dragify(b)dragToggle=nil;local c=0;dragInput=nil;dragStart=nil;local d=nil;function updateInput(e)local f=e.Position-dragStart;local g=UDim2.new(startPos.X.Scale,startPos.X.Offset+f.X,startPos.Y.Scale,startPos.Y.Offset+f.Y)game:GetService("TweenService"):Create(b,TweenInfo.new(0.25),{Position=g}):Play()end;b.InputBegan:Connect(function(e)if(e.UserInputType==Enum.UserInputType.MouseButton1 or e.UserInputType==Enum.UserInputType.Touch)and a:GetFocusedTextBox()==nil then dragToggle=true;dragStart=e.Position;startPos=b.Position;e.Changed:Connect(function()if e.UserInputState==Enum.UserInputState.End then dragToggle=false end end)end end)b.InputChanged:Connect(function(e)if e.UserInputType==Enum.UserInputType.MouseMovement or e.UserInputType==Enum.UserInputType.Touch then dragInput=e end end)game:GetService("UserInputService").InputChanged:Connect(function(e)if e==dragInput and dragToggle then updateInput(e)end end)end;dragify(script.Parent)
end
coroutine.wrap(PIZCLXV_fake_script)()
local function IXWU_fake_script() -- TextButton.LocalScript 
	local script = Instance.new('LocalScript', TextButton)

	local Players = game:GetService("Players")
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	
	-- Equip item function
	local function equipItem()
		local equipArgs = {201, 1372}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(equipArgs))
		end)
		if not success then
			warn("Equip item failed:", result)
		end
	end
	
	
	local function UnEquip()
		local args = {
			[1] = 202,
		}
	
		game:GetService("ReplicatedStorage"):WaitForChild("Connection"):InvokeServer(unpack(args))
	end
	-- Give item to player by username
	local function giveItemToPlayer(userId)
		local giveArgs = {userId, 1372}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("FunctionConnections"):WaitForChild("RequestSendPassAlongActionItem"):InvokeServer(unpack(giveArgs))
		end)
		if not success then
			warn("Give item failed for userId " .. userId .. ":", result)
		end
	end
	
	-- Find a player by username or part of it
	local function getPlayerByName(username)
		for _, player in ipairs(Players:GetPlayers()) do
			if player.Name:lower():sub(1, #username):lower() == username:lower() then
				return player
			end
		end
		return nil
	end
	
	-- Button click event
	script.Parent.MouseButton1Click:Connect(function()
		local username = TextBox.Text
		if username and username ~= "" then
			local player = getPlayerByName(username)
			if player then
				-- Equip item to local player
				equipItem()
	
				-- Give item to the local player and the targeted player
				giveItemToPlayer(game.Players.LocalPlayer.UserId)
				giveItemToPlayer(player.UserId)
				wait(0)
				UnEquip()
			else
				warn("Player not found!")
			end
		else
			warn("Please enter a valid username!")
		end
	end)
end
coroutine.wrap(IXWU_fake_script)()
local function LMFFR_fake_script() -- TextButton_2.LocalScript 
	local script = Instance.new('LocalScript', TextButton_2)

	local Players = game:GetService("Players")
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	
	-- Equip item function
	local function equipItem()
		local equipArgs = {201, 932}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(equipArgs))
		end)
		if not success then
			warn("Equip item failed:", result)
		end
	end
	
	local function UnEquip()
		local args = {
			[1] = 202,
		}
	
		game:GetService("ReplicatedStorage"):WaitForChild("Connection"):InvokeServer(unpack(args))
	end
	
	-- Give item to player by username
	local function giveItemToPlayer(userId)
		local giveArgs = {userId, 932}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("FunctionConnections"):WaitForChild("RequestSendPassAlongActionItem"):InvokeServer(unpack(giveArgs))
		end)
		if not success then
			warn("Give item failed for userId " .. userId .. ":", result)
		end
	end
	
	-- Find a player by username or part of it
	local function getPlayerByName(username)
		for _, player in ipairs(Players:GetPlayers()) do
			if player.Name:lower():sub(1, #username):lower() == username:lower() then
				return player
			end
		end
		return nil
	end
	
	-- Button click event
	script.Parent.MouseButton1Click:Connect(function()
		local username = TextBox.Text
		if username and username ~= "" then
			local player = getPlayerByName(username)
			if player then
				-- Equip item to local player
				equipItem()
	
				-- Give item to the local player and the targeted player
				giveItemToPlayer(game.Players.LocalPlayer.UserId)
				giveItemToPlayer(player.UserId)
				wait(0)
				UnEquip()
			else
				warn("Player not found!")
			end
		else
			warn("Please enter a valid username!")
		end
	end)
end
coroutine.wrap(LMFFR_fake_script)()
local function AJYB_fake_script() -- TextButton_3.LocalScript 
	local script = Instance.new('LocalScript', TextButton_3)

	local Players = game:GetService("Players")
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	
	-- Equip item function
	local function equipItem()
		local equipArgs = {201, 1344}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(equipArgs))
		end)
		if not success then
			warn("Equip item failed:", result)
		end
	end
	
	local function UnEquip()
		local args = {
			[1] = 202,
		}
	
		game:GetService("ReplicatedStorage"):WaitForChild("Connection"):InvokeServer(unpack(args))
	end
	
	-- Give item to player by username
	local function giveItemToPlayer(userId)
		local giveArgs = {userId, 1344}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("FunctionConnections"):WaitForChild("RequestSendPassAlongActionItem"):InvokeServer(unpack(giveArgs))
		end)
		if not success then
			warn("Give item failed for userId " .. userId .. ":", result)
		end
	end
	
	-- Find a player by username or part of it
	local function getPlayerByName(username)
		for _, player in ipairs(Players:GetPlayers()) do
			if player.Name:lower():sub(1, #username):lower() == username:lower() then
				return player
			end
		end
		return nil
	end
	
	-- Button click event
	script.Parent.MouseButton1Click:Connect(function()
		local username = TextBox.Text
		if username and username ~= "" then
			local player = getPlayerByName(username)
			if player then
				-- Equip item to local player
				equipItem()
	
				-- Give item to the local player and the targeted player
				giveItemToPlayer(game.Players.LocalPlayer.UserId)
				giveItemToPlayer(player.UserId)
				wait(0)
				UnEquip()
			else
				warn("Player not found!")
			end
		else
			warn("Please enter a valid username!")
		end
	end)
end
coroutine.wrap(AJYB_fake_script)()
local function NBJR_fake_script() -- TextButton_4.LocalScript 
	local script = Instance.new('LocalScript', TextButton_4)

	local Players = game:GetService("Players")
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	
	-- Equip item function
	local function equipItem()
		local equipArgs = {201, 1141}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(equipArgs))
		end)
		if not success then
			warn("Equip item failed:", result)
		end
	end
	
	local function UnEquip()
		local args = {
			[1] = 202,
		}
	
		game:GetService("ReplicatedStorage"):WaitForChild("Connection"):InvokeServer(unpack(args))
	end
	
	-- Give item to player by username
	local function giveItemToPlayer(userId)
		local giveArgs = {userId, 1141}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("FunctionConnections"):WaitForChild("RequestSendPassAlongActionItem"):InvokeServer(unpack(giveArgs))
		end)
		if not success then
			warn("Give item failed for userId " .. userId .. ":", result)
		end
	end
	
	-- Find a player by username or part of it
	local function getPlayerByName(username)
		for _, player in ipairs(Players:GetPlayers()) do
			if player.Name:lower():sub(1, #username):lower() == username:lower() then
				return player
			end
		end
		return nil
	end
	
	-- Button click event
	script.Parent.MouseButton1Click:Connect(function()
		local username = TextBox.Text
		if username and username ~= "" then
			local player = getPlayerByName(username)
			if player then
				-- Equip item to local player
				equipItem()
	
				-- Give item to the local player and the targeted player
				giveItemToPlayer(game.Players.LocalPlayer.UserId)
				giveItemToPlayer(player.UserId)
				wait(0)
				UnEquip()
			else
				warn("Player not found!")
			end
		else
			warn("Please enter a valid username!")
		end
	end)
end
coroutine.wrap(NBJR_fake_script)()
local function OQTJV_fake_script() -- TextButton_5.LocalScript 
	local script = Instance.new('LocalScript', TextButton_5)

	local Players = game:GetService("Players")
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	
	-- Equip item function
	local function equipItem()
		local equipArgs = {201, 698}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(equipArgs))
		end)
		if not success then
			warn("Equip item failed:", result)
		end
	end
	
	local function UnEquip()
		local args = {
			[1] = 202,
		}
	
		game:GetService("ReplicatedStorage"):WaitForChild("Connection"):InvokeServer(unpack(args))
	end
	
	-- Give item to player by username
	local function giveItemToPlayer(userId)
		local giveArgs = {userId, 698}
		local success, result = pcall(function()
			ReplicatedStorage:WaitForChild("FunctionConnections"):WaitForChild("RequestSendPassAlongActionItem"):InvokeServer(unpack(giveArgs))
		end)
		if not success then
			warn("Give item failed for userId " .. userId .. ":", result)
		end
	end
	
	-- Find a player by username or part of it
	local function getPlayerByName(username)
		for _, player in ipairs(Players:GetPlayers()) do
			if player.Name:lower():sub(1, #username):lower() == username:lower() then
				return player
			end
		end
		return nil
	end
	
	-- Button click event
	script.Parent.MouseButton1Click:Connect(function()
		local username = TextBox.Text
		if username and username ~= "" then
			local player = getPlayerByName(username)
			if player then
				-- Equip item to local player
				equipItem()
	
				-- Give item to the local player and the targeted player
				giveItemToPlayer(game.Players.LocalPlayer.UserId)
				giveItemToPlayer(player.UserId)
				wait(0)
				UnEquip()
			else
				warn("Player not found!")
			end
		else
			warn("Please enter a valid username!")
		end
	end)
end
coroutine.wrap(OQTJV_fake_script)()
local function CFBXF_fake_script() -- TextButton_6.LocalScript 
	local script = Instance.new('LocalScript', TextButton_6)

	
	script.Parent.MouseButton1Click:Connect(function()
		local args = {
			[1] = {
				["HatAccessory"] = "21070012,3154654707,335080779,132809431,183468963",
				["RightLegColor"] = {
					[1] = "255",
					[2] = "255",
					[3] = "255"
				},
				["WaistAccessory"] = "53623350",
				["Torso"] = 109182039511426,
				["WidthScale"] = 0.6,
				["LeftArm"] = 80900302406002,
				["BodyTypeScale"] = 0.016367793083190918,
				["BackAccessory"] = "34398653",
				["Shirt"] = 0,
				["FaceAccessory"] = "89171071,233705354,191101707,24114402",
				["Pants"] = 0,
				["RightArmColor"] = {
					[1] = "255",
					[2] = "255",
					[3] = "255"
				},
				["LeftArmColor"] = {
					[1] = "255",
					[2] = "255",
					[3] = "255"
				},
				["HairAccessory"] = "172246820",
				["ShouldersAccessory"] = "11563251,86494893,12562495,11999247",
				["RightArm"] = 109536486803444,
				["ProportionScale"] = 0.5081838965415955,
				["Head"] = 14731382899,
				["FrontAccessory"] = "1046895,26382698,130497352,5966071922",
				["Emotes"] = {
					["1"] = {
						[1] = 11563251
					},
					["4"] = {
						[1] = 3576968026
					},
					["3"] = {
						[1] = 3576823880
					},
					["2"] = {
						[1] = 3360689775
					}
				},
				["NeckAccessory"] = "398693210,68633810,96850523",
				["Face"] = 0,
				["HeadColor"] = {
					[1] = "17",
					[2] = "17",
					[3] = "17"
				},
				["TorsoColor"] = {
					[1] = "245",
					[2] = "205",
					[3] = "48"
				},
				["DepthScale"] = 0.6,
				["RightLeg"] = 2608538559,
				["HeadScale"] = 1.25,
				["HeightScale"] = 0.6,
				["LeftLegColor"] = {
					[1] = "255",
					[2] = "255",
					[3] = "255"
				},
				["LeftLeg"] = 2608536258
			}
		}
	
		game:GetService("ReplicatedStorage"):WaitForChild("FunctionConnections"):WaitForChild("NewAESaveAvatar"):InvokeServer(unpack(args))
	end)
end
coroutine.wrap(CFBXF_fake_script)()
   end,
})

local Button = MainTab:CreateButton({
    Name = "Enviar mensagem privada para todos (amigos no servidor)",
    Callback = function()
        if mensagem ~= "" then
            for _, jogador in ipairs(Players:GetPlayers()) do
                local prepareArgs = {
                    [1] = jogador.UserId,
                    [2] = mensagem
                }
                ReplicatedStorage.FunctionConnections.PrepareComposeWhisper:InvokeServer(unpack(prepareArgs))

                local sendArgs = {
                    [1] = jogador.UserId
                }
                ReplicatedStorage.EventConnections.SendPreparedWhisper:FireServer(unpack(sendArgs))
            end
        else
            print("Por favor, insira uma mensagem no campo de entrada.")
        end
    end,
})

local Button = MainTab:CreateButton({
    Name = "Enviar solicitação de amizade para todos no servidor",
    Callback = function()
        local Players = game:GetService("Players")
        local ReplicatedStorage = game:GetService("ReplicatedStorage")

        for _, jogador in ipairs(Players:GetPlayers()) do
            local statusArgs = {
                [1] = jogador.UserId
            }
            ReplicatedStorage.FunctionConnections.RequestPlayerStatusResponseForUserId:InvokeServer(unpack(statusArgs))

            local bioArgs = {
                [1] = jogador.UserId
            }
            ReplicatedStorage.FunctionConnections.RequestPlayerBioForUserId:InvokeServer(unpack(bioArgs))

            local friendArgs = {
                [1] = jogador
            }
            ReplicatedStorage.FunctionConnections.RequestSendFriendRequest:InvokeServer(unpack(friendArgs))
        end
    end,
})

local Section = MainTab:CreateSection("As pessoas receberão a solicitação novamente ao recusá-la.")
local Button = MainTab:CreateButton({
    Name = "Solicitar teletransporte para todos no servidor (amigos)",
    Callback = function()
        local Players = game:GetService("Players")
        local ReplicatedStorage = game:GetService("ReplicatedStorage")

        local function sendInviteToAllPlayers()
            while true do
                for _, jogador in ipairs(Players:GetPlayers()) do
                    local statusArgs = { [1] = jogador.UserId }
                    ReplicatedStorage.FunctionConnections.RequestPlayerStatusResponseForUserId:InvokeServer(unpack(statusArgs))

                    local bioArgs = { [1] = jogador.UserId }
                    ReplicatedStorage.FunctionConnections.RequestPlayerBioForUserId:InvokeServer(unpack(bioArgs))

                    local locationArgs = { [1] = jogador.UserId }
                    ReplicatedStorage.FunctionConnections.RequestPlayerLocationForUserId:InvokeServer(unpack(locationArgs))

                    local inviteFromArgs = { [1] = jogador.UserId }
                    ReplicatedStorage.FunctionConnections.RequestInviteFromFriend:InvokeServer(unpack(inviteFromArgs))

                    local sendInviteArgs = { [1] = jogador.UserId }
                    ReplicatedStorage.FunctionConnections.RequestSendInviteToFriend:InvokeServer(unpack(sendInviteArgs))
                end
                wait(0)
            end
        end

        sendInviteToAllPlayers()
    end,
})

local Button = MainTab:CreateButton({
   Name = "Dar snowball para outros",
   Callback = function()
      local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local isRunning = false

local function equipItem()
    local equipArgs = {201, 932}
    local success, result = pcall(function()
        ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(equipArgs))
    end)
    if not success then
        warn("Equip item failed:", result)
    end
end

local function unEquip()
    local args = {202}
    pcall(function()
        ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(args))
    end)
end

local function hasItemEquipped(player)
    local equippedItems = player:FindFirstChild("Backpack"):FindFirstChild(932)
    return equippedItems ~= nil
end

local function giveItemToAllPlayers()
    for _, player in pairs(Players:GetPlayers()) do
        if not hasItemEquipped(player) then
            local giveArgs = {player.UserId, 932}
            local success, result = pcall(function()
                ReplicatedStorage:WaitForChild("FunctionConnections"):WaitForChild("RequestSendPassAlongActionItem"):InvokeServer(unpack(giveArgs))
            end)
            if not success then
                warn("Give item failed for " .. player.Name .. ":", result)
            end
        end
    end
end

-- Chamar a função para executar tudo diretamente
if not isRunning then
    isRunning = true

    equipItem()
    giveItemToAllPlayers()
    unEquip()

    isRunning = false
else
    wait(1)
end
   end,
})

local Button = MainTab:CreateButton({
   Name = "Tacar snowball em todos",
   Callback = function()
      local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local ThrowItemEvent = ReplicatedStorage.EventConnections.ThrowItem
local RunService = game:GetService("RunService")

local function getRandomPlayer()
    local allPlayers = Players:GetPlayers()
    local randomIndex = math.random(1, #allPlayers)
    local randomPlayer = allPlayers[randomIndex]
    if randomPlayer and randomPlayer.Character and randomPlayer.Character:FindFirstChild("HumanoidRootPart") then
        return randomPlayer
    else
        return nil
    end
end

local function throwAtRandomPlayer()
    local randomPlayer = getRandomPlayer()
    if randomPlayer then
        local targetPosition = randomPlayer.Character.HumanoidRootPart.Position
        local args = {
            [1] = string.format("[932,[\"%s\",\"%s\",\"%s\"],[\"%s\",\"%s\",\"%s\"],[\"%s\",\"%s\",\"%s\"],75]",
                tostring(targetPosition.X), tostring(targetPosition.Y), tostring(targetPosition.Z),
                tostring(targetPosition.X + 3), tostring(targetPosition.Y + 3), tostring(targetPosition.Z + 3),
                tostring(targetPosition.X - 3), tostring(targetPosition.Y - 3), tostring(targetPosition.Z - 3))
        }
        ThrowItemEvent:FireServer(unpack(args))
    end
end

-- Executar a função de lançar a bola de neve para um jogador aleatório sem interação
RunService.Heartbeat:Connect(function()
    for _ = 1, 1 do
        throwAtRandomPlayer()
    end
end)
   end,
})

local Button = MainTab:CreateButton({
   Name = "Tacar ovo em todos",
   Callback = function()
      local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local ThrowItemEvent = ReplicatedStorage.EventConnections.ThrowItem
local RequestAssetModel = ReplicatedStorage.FunctionConnections.RequestAssetModel
local ClearRequestedAssetModels = ReplicatedStorage.EventConnections.ClearRequestedAssetModels
local RunService = game:GetService("RunService")

local function getRandomPlayer()
    local allPlayers = Players:GetPlayers()
    local randomIndex = math.random(1, #allPlayers)
    local randomPlayer = allPlayers[randomIndex]
    if randomPlayer and randomPlayer.Character and randomPlayer.Character:FindFirstChild("HumanoidRootPart") then
        return randomPlayer
    else
        return nil
    end
end

local function throwAtRandomPlayer()
    local randomPlayer = getRandomPlayer()
    if randomPlayer then
        local targetPosition = randomPlayer.Character.HumanoidRootPart.Position

        -- Solicita o modelo do ovo antes de lançar
        local requestArgs = {
            [1] = {
                [1] = 602
            }
        }
        RequestAssetModel:InvokeServer(unpack(requestArgs))

        -- Lança o ovo
        local throwArgs = {
            [1] = string.format("[602,[\"%s\",\"%s\",\"%s\"],[\"%s\",\"%s\",\"%s\"],[\"%s\",\"%s\",\"%s\"],50]",
                tostring(targetPosition.X), tostring(targetPosition.Y), tostring(targetPosition.Z),
                tostring(targetPosition.X + 3), tostring(targetPosition.Y + 3), tostring(targetPosition.Z + 3),
                tostring(targetPosition.X - 3), tostring(targetPosition.Y - 3), tostring(targetPosition.Z - 3))
        }
        ThrowItemEvent:FireServer(unpack(throwArgs))

        -- Limpa o modelo solicitado do ovo
        ClearRequestedAssetModels:FireServer(unpack(requestArgs))
    end
end

-- Executa a função de lançar o ovo para um jogador aleatório repetidamente
RunService.Heartbeat:Connect(function()
    for _ = 1, 1 do
        throwAtRandomPlayer()
    end
end)
   end,
})

local Button = MainTab:CreateButton({
   Name = "Dar babymeep para outros",
   Callback = function()
      local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local isRunning = false

local function equipItem()
    local equipArgs = {201, 1232}
    local success, result = pcall(function()
        ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(equipArgs))
    end)
    if not success then
        warn("Equip item failed:", result)
    end
end

local function unEquip()
    local args = {202}
    pcall(function()
        ReplicatedStorage:WaitForChild("Connection"):InvokeServer(unpack(args))
    end)
end

local function hasItemEquipped(player)
    local equippedItems = player:FindFirstChild("Backpack"):FindFirstChild(1232)  -- Corrigido para o item correto
    return equippedItems ~= nil
end

local function giveItemToAllPlayers()
    for _, player in pairs(Players:GetPlayers()) do
        if not hasItemEquipped(player) then
            local giveArgs = {player.UserId, 1232}  -- Corrigido para o item correto
            local success, result = pcall(function()
                ReplicatedStorage:WaitForChild("FunctionConnections"):WaitForChild("RequestSendPassAlongActionItem"):InvokeServer(unpack(giveArgs))
            end)
            if not success then
                warn("Give item failed for " .. player.Name .. ":", result)
            end
        end
    end
end

-- Executa a função sem interação do usuário
if not isRunning then
    isRunning = true

    equipItem()
    giveItemToAllPlayers()
    unEquip()

    isRunning = false
else
    wait(1)
end
   end,
})

local Button = MainTab:CreateButton({
   Name = "Fogos",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/PWaEZitv'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Fogos V2 PING+",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/h29pyd3t'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Fogos V3 PING++",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/49JdxKSJ'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Spam fogos",
   Callback = function()
      local spawnFirework = true
local lastFireworkTime = 0
local fireworkCooldown = 2 -- Defina o tempo de cooldown entre os fogos de artifício
local fireworkConnection

-- Conecta-se ao Heartbeat do RunService para execução contínua
fireworkConnection = game:GetService("RunService").Heartbeat:Connect(function()
    if spawnFirework and tick() - lastFireworkTime >= fireworkCooldown then
        game:GetService("ReplicatedStorage").Connection:InvokeServer(202, 1310)
        game:GetService("ReplicatedStorage").Connection:InvokeServer(201, 1310, {})
        game:GetService("ReplicatedStorage").ConnectionEvent:FireServer(210)
        lastFireworkTime = tick()
    end
end)

-- O script já está configurado para rodar automaticamente ao ser executado.
   end,
})

local Button = MainTab:CreateButton({
   Name = "Spawn varas no céu",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/y9SUYpA7'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Spawn varas no céu V2 +LAG",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/5FPScAj7'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Varas pelo mapa (Perto)",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/bzmLUW5H'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Varas pelo mapa (Longe)",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/dtAfU0My'))()
   end,
})

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local backpack = player:WaitForChild("Backpack")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local Toggle = false 

local function equipAllTools()
    for _, tool in pairs(backpack:GetChildren()) do
        if tool:IsA("Tool") then
            tool.Parent = character 
        end
    end
end

local function getItem()
    ReplicatedStorage.Connection:InvokeServer(9, 0)
    wait(0.1)

    ReplicatedStorage.Connection:InvokeServer(9, 1)

    ReplicatedStorage.Connection:InvokeServer(49)
    ReplicatedStorage.Connection:InvokeServer(50)
    ReplicatedStorage.Connection:InvokeServer(51)

    local ohNumber1 = 11
    local ohTable2 = {
        ["FishingPolePos"] = Workspace.TempFish.Position,
        ["Power"] = math.random(),
        ["Face"] = Workspace.TempFish.Position,
        ["PlayerPos"] = Workspace.TempFish.Position,
        ["FishingZonePos"] = Vector3.new(-5.29345703, -18.0412292, 43.7173767),
    }
    ReplicatedStorage.Connection:InvokeServer(ohNumber1, ohTable2)
end

local function startFishing()
    while Toggle do
        for _ = 1, 1 do
            spawn(function() 
                equipAllTools()
            end)

            spawn(function()
                getItem()
            end)
        end
        wait(0)
    end
end

local Toggle = MainTab:CreateToggle({
   Name = "Loop Equipar Varas de Pesca (Sem Lags)",
   CurrentValue = false,
   Flag = "Toggle1", 
   Callback = function(value)
       Toggle = value
       if Toggle then
           startFishing()
       end
   end,
})

local Toggle = MainTab:CreateToggle({
   Name = "Loop Soltar Varas",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(value)
       isSpamming = value
        
       if isSpamming then
           spawn(function()
               while isSpamming do
                   game:GetService("VirtualInputManager"):SendKeyEvent(true, Enum.KeyCode.Backspace, false, game)
                   wait(0)
               end
           end)
       end
   end,
})

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local localPlayer = Players.LocalPlayer
local character = localPlayer.Character or localPlayer.CharacterAdded:Wait()

local spinningToggle = false
local activeSpinConnections = {}

local function spinAroundPlayer(targetPlayer)
    local rootPart = character:FindFirstChild("HumanoidRootPart")
    if not rootPart then return end

    local targetCharacter = targetPlayer.Character
    if not targetCharacter then return end

    local targetRoot = targetCharacter:FindFirstChild("HumanoidRootPart")
    if not targetRoot then return end

    local spinDuration = 2
    local radius = 6
    local spinSpeed = 720

    local startTime = tick()
    local connection

    connection = RunService.Heartbeat:Connect(function()
        if not spinningToggle then
            connection:Disconnect()
            return
        end

        local elapsedTime = tick() - startTime
        if elapsedTime > spinDuration then
            connection:Disconnect()
            return
        end

        local angle = math.rad((elapsedTime * spinSpeed) % 360)
        local offset = Vector3.new(math.cos(angle) * radius, 0, math.sin(angle) * radius)
        local targetPosition = targetRoot.Position + offset

        rootPart.CFrame = CFrame.new(targetPosition, targetRoot.Position)
    end)

    table.insert(activeSpinConnections, connection)
    wait(spinDuration)
end

local function spinAroundAllPlayers()
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= localPlayer then
            pcall(function()
                spinAroundPlayer(player)
            end)
        end
    end
end

local function startSpinning()
    while spinningToggle do
        spinAroundAllPlayers()
        wait(0.1)
    end
end

local function stopSpinning()
    for _, connection in ipairs(activeSpinConnections) do
        connection:Disconnect()
    end
    activeSpinConnections = {}
end

local SpinToggle = MainTab:CreateToggle({
    Name = "Girar ao redor dos Jogadores",
    CurrentValue = false,
    Flag = "SpinToggle",
    Callback = function(value)
        spinningToggle = value
        if spinningToggle then
            spawn(startSpinning)
        else
            stopSpinning()
        end
    end,
})

local Button = MainTab:CreateButton({
   Name = "Chat næzï",
   Callback = function()
local TextChatService = game:GetService("TextChatService")

local lines = {
    "⬜⬜⬜⬜⬜⬜⬜",
    "⬜⬛⬜⬛⬛⬛⬜",
    "⬜⬛⬜⬛⬜⬜⬜",
    "⬜⬛⬛⬛⬛⬛⬜",
    "⬜⬜⬜⬛⬜⬛⬜",
    "⬜⬛⬛⬛⬜⬛⬜",
    "⬜⬜⬜⬜⬜⬜⬜"
}

local function sendMessage(message)
    local textChannel = TextChatService:WaitForChild("TextChannels"):FindFirstChild("RBXGeneral")
    if textChannel then
        textChannel:SendAsync(message)
    end
end

for _, line in ipairs(lines) do
    sendMessage(line)
    wait(0) 
end
   end,
})

local chatButton = MainTab:CreateButton({
    Name = "Chat d¹ldō", 
    Callback = function()
        local TextChatService = game:GetService("TextChatService")

        local linhas = {
            "⬜⬜⬜⬜⬜⬜⬜⬜",
            "⬜⬜⬜⬛⬛⬜⬜⬜",
            "⬜⬜⬜⬛⬛⬜⬜⬜",
            "⬜⬜⬜⬛⬛⬜⬜⬜",
            "⬜⬜⬜⬛⬛⬜⬜⬜",
            "⬜⬜⬜⬛⬛⬜⬜⬜",
            "⬜⬛⬛⬜⬜⬛⬛⬜",
            "⬜⬛⬛⬜⬜⬛⬛⬜"
        }

        local function enviarMensagem(mensagem)
            local textChannel = TextChatService:WaitForChild("TextChannels"):FindFirstChild("RBXGeneral")
            if textChannel then
                textChannel:SendAsync(mensagem)
            end
        end

        for _, linha in ipairs(linhas) do
            enviarMensagem(linha)
            wait(0) 
        end
    end,
})

local MainTab = Window:CreateTab("Farm",93869833341209)
local MainSection = MainTab:CreateSection("Farm")

local Button = MainTab:CreateButton({
   Name = "100% de Sucesso ao Pescar",
   Callback = function()
	Constants.STATS.FISHCastObjectMinDistanceToCatch = math.huge
   end,
})

local Button = MainTab:CreateButton({
   Name = "Tamanho Ilimitado do Balde de Pesca",
   Callback = function()
	Constants.STATS.FISHMaxAllowedInBucket = math.huge
   end,
})

local Button = MainTab:CreateButton({
   Name = "Iniciar Auto-Farm",
   Callback = function()
       while true do
           local args1 = { [1] = 10 }
           game:GetService("ReplicatedStorage").ConnectionEvent:FireServer(unpack(args1))

           local args2 = {
               [1] = 11,
               [2] = {
                   ["Power"] = 1,
                   ["FishingZonePos"] = Vector3.new(82.066064453125, -18.149871826171875, 96.40253448486328),
                   ["Face"] = Vector3.new(0.9990392923355103, 0.005603702738881111, -0.04346461594104767),
                   ["PlayerPos"] = Vector3.new(62.121219635009766, -12.388772010803223, 93.4290542602539),
                   ["FishingPolePos"] = Vector3.new(64.75240325927734, -5.818235397338867, 94.7131118774414)
               }
           }
           game:GetService("ReplicatedStorage").Connection:InvokeServer(unpack(args2))

           local args3 = { [1] = 49 }
           game:GetService("ReplicatedStorage").Connection:InvokeServer(unpack(args3))

           local args4 = { [1] = 10 }
           game:GetService("ReplicatedStorage").ConnectionEvent:FireServer(unpack(args4))

           local args5 = { [1] = 50 }
           game:GetService("ReplicatedStorage").Connection:InvokeServer(unpack(args5))

           local args6 = { [1] = 51 }
           game:GetService("ReplicatedStorage").Connection:InvokeServer(unpack(args6))

           local args7 = { [1] = 9, [2] = 23 }
           game:GetService("ReplicatedStorage").Connection:InvokeServer(unpack(args7))

           wait(0)
       end
   end,
})

local MainTab = Window:CreateTab("Spam + Plantar",85369033961046)
local MainSection = MainTab:CreateSection("Spam + Plantar")

local Button = MainTab:CreateButton({
   Name = "Spam Balão",
   Callback = function()
      local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Início automático do processo de espalhar balões
local spawnAllBalloons = true

task.spawn(function()
    while spawnAllBalloons do
        local args = {
            [1] = 201,
            [2] = nil,  -- ID do balão será definido em cada iteração
            [3] = {}
        }
        local args2 = {
            [1] = 202
        }

        -- IDs dos balões a serem espalhados
        local balloonIDs = {1311, 1312, 1313, 1314, 1315, 1039}

        -- Executar a criação e remoção de cada balão
        for _, id in ipairs(balloonIDs) do
            args[2] = id
            pcall(function()
                ReplicatedStorage.Connection:InvokeServer(unpack(args))
                ReplicatedStorage.Connection:InvokeServer(unpack(args2))
            end)
        end

        task.wait(0.1)  -- Intervalo entre cada ciclo
    end
end)
   end,
})

local Button = MainTab:CreateButton({
   Name = "Plantar Frango",
   Callback = function()
      loadstring(game:HttpGet("https://pastebin.com/raw/dy1gTsr1"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Loop plantar frango",
   Callback = function()
     loadstring(game:HttpGet("https://pastebin.com/raw/8eMe1Da3"))() 
   end,
})

local Button = MainTab:CreateButton({
   Name = "Plantar bolo",
   Callback = function()
      loadstring(game:HttpGet("https://pastebin.com/raw/m2QftL55"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Loop plantar bolo",
   Callback = function()
      loadstring(game:HttpGet("https://pastebin.com/raw/m2QftL55"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Plantar brownie",
   Callback = function()
      loadstring(game:HttpGet("https://pastebin.com/raw/qebwvWSE"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Loop plantar brownie",
   Callback = function()
      loadstring(game:HttpGet("https://pastebin.com/raw/P2iyKr3m"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Plantar pizza",
   Callback = function()
      loadstring(game:HttpGet("https://pastebin.com/raw/Khamf1tU"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Loop plantar pizza",
   Callback = function()
      loadstring(game:HttpGet("https://pastebin.com/raw/zFRtJdFK"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Plantar prato",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/2F7jVJ5x'))()
   end,
})

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Função para converter Color3 para uma tabela com valores de 0-255
local function colorToTable(clr)
    return {tostring(clr.R * 255), tostring(clr.G * 255), tostring(clr.B * 255)}
end

-- Função que extrai os dados do humanoide
local function ExtractData(humdes)
    local ava = {}

    -- Copiar os dados de escala
    for _, v in pairs({"WidthScale", "HeightScale", "DepthScale", "BodyTypeScale", "ProportionScale", "HeadScale"}) do
        ava[v] = humdes[v]
    end

    -- Copiar a configuração do corpo (Face, Head, Arms, Legs, etc)
    for _, v in pairs({"Face", "Head", "LeftArm", "RightArm", "LeftLeg", "RightLeg", "Torso"}) do
        ava[v] = humdes[v]
    end

    -- Copiar as cores das partes do corpo
    for _, v in pairs({"HeadColor", "LeftArmColor", "RightArmColor", "LeftLegColor", "RightLegColor", "TorsoColor"}) do
        ava[v] = colorToTable(humdes[v]) -- Convertendo a cor para tabela RGB (0-255)
    end

    -- Copiar roupas (camisa, calça, etc)
    for _, v in pairs({"GraphicTShirt", "Shirt", "Pants"}) do
        ava[v] = humdes[v]
    end

    -- Copiar animações (Idle, Run, Jump, etc)
    for _, v in pairs({"IdleAnimation", "RunAnimation", "JumpAnimation", "SwimAnimation", "WalkAnimation", "ClimbAnimation", "FallAnimation"}) do
        ava[v] = humdes[v]
    end

    -- Copiar acessórios
    for _, v in pairs({"Hat", "Hair", "Back", "Face", "Front", "Neck", "Shoulders", "Waist"}) do
        ava[v .. "Accessory"] = humdes[v .. "Accessory"]
    end

    -- Copiar acessórios em camadas (layered)
    local layered = humdes:GetAccessories(false)
    for i, accessory in pairs(layered) do
        if accessory.AccessoryType and typeof(accessory.AccessoryType) == "EnumItem" then
            accessory.AccessoryType = accessory.AccessoryType.Name
        end
        accessory.Order = i
    end
    ava.AccessoryBlob = layered

    -- Copiar emotes
    ava.Emotes = humdes:GetEmotes()

    return ava
end

-- Função para carregar o avatar de um jogador com base no UserId
local function LoadAvatarFromUserId(userid)
    local success, humdes = pcall(function()
        return Players:GetHumanoidDescriptionFromUserId(tonumber(userid))
    end)
    
    if success and humdes then
        local data = ExtractData(humdes)
        ReplicatedStorage.FunctionConnections.NewAESaveAvatar:InvokeServer(data)
        print("Avatar do UserId " .. userid .. " copiado com sucesso!")
    else
        warn("Erro ao carregar o avatar para o UserId: " .. userid)
    end
end

-- Função para carregar o avatar de um jogador com base no Username
local function LoadAvatarFromUsername(username)
    local success, userId = pcall(function()
        return Players:GetUserIdFromNameAsync(username)
    end)
    
    if success and userId then
        LoadAvatarFromUserId(userId)
    else
        warn("Erro ao encontrar o UserId para o Username: " .. username)
    end
end

-- Criar a interface usando Rayfield
local Window = Rayfield:CreateWindow({
    Name = "👾Meepcity👾",
    LoadingTitle = "Carregando...",
    LoadingSubtitle = "Aguarde um momento...",
})

local Tab = Window:CreateTab("Avatar",109650706901296)

-- Criar o Textbox para inserir o nome de usuário
local LoadAvatarFromUsernameInput = Tab:CreateInput({
    Name = "Carregar avatar por nickname",
    CurrentValue = "",
    PlaceholderText = "Insira o nickname",
    RemoveTextAfterFocusLost = false,
    Flag = "LoadAvatarUsername",
    Callback = function(username)
        if username and username ~= "" then
            LoadAvatarFromUsername(username)
        else
            print("Por favor, insira um nome de usuário válido.")
        end
    end,
})

local Button = Tab:CreateButton({
   Name = "Vestir todos os itens (Reiniciar para removê-los)",
   Callback = function()
      local ReplicatedStorage = game:GetService("ReplicatedStorage")

      local function tryID(id)
          ReplicatedStorage.Connection:InvokeServer(201, id, {})
      end

      for id = 0, 8000 do
          coroutine.wrap(tryID)(id)  
      end
   end,
})

local Button = Tab:CreateButton({
   Name = "Virar criança",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/zKyQLQ4w'))()
   end,
})

local Button = Tab:CreateButton({
   Name = "Virar adolescente",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/Ms6iJXpL'))()
   end,
})

local Button = Tab:CreateButton({
   Name = "Virar adulto",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/TYFqdwRN'))()
   end,
})

-- Variável para controlar o estado do sono
local isSleeping = false
local animationId = "rbxassetid://2176786857"
local animation = Instance.new("Animation")
animation.AnimationId = animationId

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local animationTrack

-- Criar o botão de alternar sono
local Button = Tab:CreateButton({
    Name = "Alternar Sono", 
    Callback = function()
        -- Alternar o estado de sono
        isSleeping = not isSleeping

        local args = {
            [1] = isSleeping, 
            [2] = 1
        }

        if isSleeping then
            -- Ativar animação de sono
            if not animationTrack or animationTrack.IsPlaying == false then
                animationTrack = humanoid:LoadAnimation(animation)
                animationTrack:Play()
            end
            game:GetService("ReplicatedStorage").EventConnections.SetCharacterIsSleeping:FireServer(unpack(args))
        else
            -- Desativar animação de sono
            if animationTrack and animationTrack.IsPlaying then
                animationTrack:Stop()
            end
            args[1] = false
            game:GetService("ReplicatedStorage").EventConnections.SetCharacterIsSleeping:FireServer(unpack(args))
        end
    end
})

local antiAFK = false
local Button = Tab:CreateButton({
   Name = "Anti AFK",
   Callback = function()
       antiAFK = not antiAFK
       if antiAFK then
           local player = game.Players.LocalPlayer
           local playerHeadIcon = "https://www.roblox.com/headshot-thumbnail/image?userId=" .. player.UserId .. "&width=420&height=420&format=png"

           game.StarterGui:SetCore("SendNotification", {
               Title = "Anti AFK",
               Text = "Anti-AFK habilitado",
               Icon = playerHeadIcon,
               Duration = 3,
               Button1 = "ok"
           })
           local vu = game:GetService("VirtualUser")
           game.Players.LocalPlayer.Idled:Connect(function()
               vu:CaptureController()
               vu:ClickButton2(Vector2.new(0, 0))
           end)
       else
           local player = game.Players.LocalPlayer
           local playerHeadIcon = "https://www.roblox.com/headshot-thumbnail/image?userId=" .. player.UserId .. "&width=420&height=420&format=png"
           game.StarterGui:SetCore("SendNotification", {
               Title = "Anti AFK",
               Text = "Anti-AFK desabilitado (requer reinício para resetar conexão Idled)",
               Icon = playerHeadIcon,
               Duration = 3,
               Button1 = "ok"
           })
       end
   end,
})

local MainTab = Window:CreateTab("Visual",105065053321743)
local MainSection = MainTab:CreateSection("Visual Apenas")

local Input = MainTab:CreateInput({
   Name = "Meep Coins",
   CurrentValue = "",
   PlaceholderText = "quantidade de dinheiro",
   RemoveTextAfterFocusLost = false,
   Flag = "Input1",
   Callback = function(Value)
      local coinAmount = tonumber(Value) 

      if coinAmount then
         game:GetService("Players").LocalPlayer.PlayerGui.MainGui.CoinsContainer.Container.Amount.Text = coinAmount
         game:GetService("Players").SlayerssUnleashedd.PlayerGui.ShopGui.Background.Content.Main.TopContainer.CoinsContainer.TotalCoins.Text = coinAmount
         game:GetService("Players").SlayerssUnleashedd.PlayerGui.ScreenGui.ItemShop.ShopContent.TopBar.ButtonBuyCoins.CoinAmount.Text = coinAmount
      else
         warn("Entrada inválida! Por favor, insira um número válido.")
      end
   end,
})

local Button = MainTab:CreateButton({
   Name = "Dinheiro infinito",
   Callback = function()
      game:GetService("Players").LocalPlayer.PlayerGui.MainGui.CoinsContainer.Container.Amount.Text = math.huge
      game:GetService("Players").SlayerssUnleashedd.PlayerGui.ShopGui.Background.Content.Main.TopContainer.CoinsContainer.TotalCoins.Text = math.huge
      game:GetService("Players").SlayerssUnleashedd.PlayerGui.ScreenGui.ItemShop.ShopContent.TopBar.ButtonBuyCoins.CoinAmount.Text = math.huge
   end,
})

local MainTab = Window:CreateTab("Teleport",91328400138691)
local MainSection = MainTab:CreateSection("Teleport")

local Button = MainTab:CreateButton({
   Name = "Tp cafeteria",
   Callback = function()
      local args = {
    [1] = 11,
    [2] = {
        ["DestinationVW"] = 11,
        ["DestinationDoorId"] = 1
    }
}

game:GetService("ReplicatedStorage").FunctionConnections.RequestTeleportToUniverse:InvokeServer(unpack(args))

   end,
})

local Button = MainTab:CreateButton({
   Name = "Tp escola",
   Callback = function()
      local args = {
    [1] = 4,
    [2] = {
        ["DestinationVW"] = 13,
        ["DestinationDoorId"] = 1
    }
}

game:GetService("ReplicatedStorage").FunctionConnections.RequestTeleportToUniverse:InvokeServer(unpack(args))

   end,
})

local Button = MainTab:CreateButton({
   Name = "Tp pizzaria",
   Callback = function()
      local args = {
    [1] = 3,
    [2] = {
        ["DestinationVW"] = 7,
        ["DestinationDoorId"] = 1
    }
}

game:GetService("ReplicatedStorage").FunctionConnections.RequestTeleportToUniverse:InvokeServer(unpack(args))

   end,
})

local Button = MainTab:CreateButton({
   Name = "Tp sorveteria",
   Callback = function()
      local args = {
    [1] = 10,
    [2] = {
        ["DestinationVW"] = 9,
        ["DestinationDoorId"] = 1
    }
}

game:GetService("ReplicatedStorage").FunctionConnections.RequestTeleportToUniverse:InvokeServer(unpack(args))

   end,
})

local MainTab = Window:CreateTab("Outros",134738852937478)
local MainSection = MainTab:CreateSection("Outros")

function LOSEYOURSELF()
    workspace.Gravity = 0

    local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid")
    local rootPart = game.Players.LocalPlayer.Character and getRoot(game.Players.LocalPlayer.Character)

    if humanoid and rootPart then
        humanoid.Sit = true
        task.wait(0.1)
        rootPart.CFrame = rootPart.CFrame * CFrame.Angles(math.pi * 0.5, 0, 0)
        for _, animTrack in ipairs(humanoid:GetPlayingAnimationTracks()) do
            animTrack:Stop()
        end

        for _, v in pairs(rootPart:GetChildren()) do
            if v.Name == "Spinning" then
                v:Destroy()
            end
        end

        local spin = Instance.new("BodyAngularVelocity")
        spin.Name = "Spinning"
        spin.Parent = rootPart
        spin.MaxTorque = Vector3.new(0, math.huge, 0)
        spin.AngularVelocity = Vector3.new(0, 2, 0)
    else
        warn("Humanoid ou HumanoidRootPart não encontrados.")
    end
end

function UNLOSEYOURSELF()
    workspace.Gravity = 196.2

    local rootPart = game.Players.LocalPlayer.Character and getRoot(game.Players.LocalPlayer.Character)
    if rootPart then
        for _, v in pairs(rootPart:GetChildren()) do
            if v.Name == "Spinning" then
                v:Destroy()
            end
        end
    end
end

local FLYING = false

local function sFLY()
    FLYING = true
    repeat task.wait() until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid")
    local T = game.Players.LocalPlayer.Character.PrimaryPart
    local CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
    local SPEED = 0
    local BG = Instance.new('BodyGyro')
    local BV = Instance.new('BodyVelocity')

    BG.P = 9e4
    BG.Parent = T
    BV.Parent = T
    BG.maxTorque = Vector3.new(9e9, 9e9, 9e9)
    BG.cframe = T.CFrame
    BV.velocity = Vector3.new(0, 0, 0)
    BV.maxForce = Vector3.new(9e9, 9e9, 9e9)

    local userInputService = game:GetService("UserInputService")

    local humanoid = game.Players.LocalPlayer.Character:WaitForChild("Humanoid")
    humanoid:ChangeState(Enum.HumanoidStateType.Physics)
    humanoid.PlatformStand = true

    userInputService.InputBegan:Connect(function(input, gameProcessed)
        if gameProcessed then return end
        if input.UserInputType == Enum.UserInputType.Keyboard then
            if input.KeyCode == Enum.KeyCode.W then CONTROL.F = 1 end
            if input.KeyCode == Enum.KeyCode.S then CONTROL.B = -1 end
            if input.KeyCode == Enum.KeyCode.A then CONTROL.L = -1 end
            if input.KeyCode == Enum.KeyCode.D then CONTROL.R = 1 end
            if input.KeyCode == Enum.KeyCode.Space then CONTROL.E = 1 end
            if input.KeyCode == Enum.KeyCode.LeftControl then CONTROL.Q = -1 end
        end
    end)

    userInputService.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.Keyboard then
            if input.KeyCode == Enum.KeyCode.W then CONTROL.F = 0 end
            if input.KeyCode == Enum.KeyCode.S then CONTROL.B = 0 end
            if input.KeyCode == Enum.KeyCode.A then CONTROL.L = 0 end
            if input.KeyCode == Enum.KeyCode.D then CONTROL.R = 0 end
            if input.KeyCode == Enum.KeyCode.Space then CONTROL.E = 0 end
            if input.KeyCode == Enum.KeyCode.LeftControl then CONTROL.Q = 0 end
        end
    end)

    task.spawn(function()
        repeat task.wait()
            if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0 then
                SPEED = 50
            else
                SPEED = 0
            end

            BV.velocity = ((workspace.CurrentCamera.CFrame.LookVector * (CONTROL.F + CONTROL.B)) +
                            ((workspace.CurrentCamera.CFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CFrame.p)) * SPEED
            BG.cframe = workspace.CurrentCamera.CFrame
        until not FLYING
        BG:Destroy()
        BV:Destroy()

        humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
        humanoid.PlatformStand = false
    end)
end

local function NOFLY()
    FLYING = false
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
        local humanoid = game.Players.LocalPlayer.Character.Humanoid
        humanoid.PlatformStand = false
        humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
    end
end

local FlyToggle = MainTab:CreateToggle({
    Name = "Voar/Desvoar",
    CurrentValue = false,
    Flag = "FlyToggle",
    Callback = function(Value)
        if Value then
            if FLYING == false then
                sFLY()
            end
        else
            if FLYING == true then
                NOFLY()
            end
        end
    end,
})

local FlyKeybind = MainTab:CreateKeybind({
    Name = "Tecla para Voar/Desvoar",
    CurrentKeybind = "F", 
    HoldToInteract = false,
    Flag = "FlyKeybind", 
    Callback = function(Keybind)
        if FLYING then
            NOFLY()
        else
            sFLY()
        end
    end,
})

local Button = MainTab:CreateButton({
   Name = "Infinite Yield",
   Callback = function()
      loadstring(game:HttpGet('htthttps://rawscripts.net/raw/Infinite-Yield_500'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Nameless Admin FE",
   Callback = function()
      loadstring(game:HttpGet('https://rawscripts.net/raw/Universal-Script-Nameless-Admin-FE-11243'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Chat Bypass",
   Callback = function()
      loadstring(game:HttpGet('https://rawscripts.net/raw/Universal-Script-Chat-bypass-idkw-24726'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Chat Bypass V2",
   Callback = function()
      loadstring(game:HttpGet('https://raw.githubusercontent.com/AlgariBot/lua/refs/heads/Lua-Script-Executor/LocalNeverPatchedBypass.txt'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Fly (Mobile)",
   Callback = function()
      loadstring(game:HttpGet('https://raw.githubusercontent.com/XNEOFF/FlyGuiV3/main/FlyGuiV3.txt'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Clone FE",
   Callback = function()
      loadstring(game:HttpGet('https://raw.githubusercontent.com/0Ben1/fe/main/obf_11l7Y131YqJjZ31QmV5L8pI23V02b3191sEg26E75472Wl78Vi8870jRv5txZyL1.lua.txt'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Rochips Universal",
   Callback = function()
      loadstring(game:HttpGet('https://rawscripts.net/raw/Universal-Script-rochips-usefull-24163'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Haxker 666",
   Callback = function()
      loadstring(game:HttpGet('https://rawscripts.net/raw/Universal-Script-Haxker666-Script-hub-9666'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Anti Lag",
   Callback = function()
      loadstring(game:HttpGet('https://pastebin.com/raw/YbkYweS5'))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Shaders",
   Callback = function()
      loadstring(game:HttpGet('https://raw.githubusercontent.com/randomstring0/pshade-ultimate/refs/heads/main/src/cd.lua'))()
   end,
}) 

local vibrateButton = MainTab:CreateButton({
    Name = "Furacão Bósnia",
    Callback = function()
        local Players = game:GetService("Players")
        local RunService = game:GetService("RunService")
        local LocalPlayer = Players.LocalPlayer
        local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()

        local ScreenGui = Instance.new("ScreenGui")
        local Frame = Instance.new("Frame")
        local ToggleButton = Instance.new("TextButton")
        local Title = Instance.new("TextLabel")

        ScreenGui.Parent = game.CoreGui
        ScreenGui.Name = "GUIFuracaoBósnia"

        Frame.Name = "MainFrame"
        Frame.Parent = ScreenGui
        Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
        Frame.BorderSizePixel = 0
        Frame.Size = UDim2.new(0, 200, 0, 100)
        Frame.Position = UDim2.new(0.5, -100, 0.5, -50)
        Frame.Draggable = true
        Frame.Active = true

        Title.Name = "Title"
        Title.Parent = Frame
        Title.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
        Title.Size = UDim2.new(1, 0, 0, 25)
        Title.Font = Enum.Font.SourceSansBold
        Title.Text = "By Miller"
        Title.TextColor3 = Color3.new(1, 1, 1)
        Title.TextSize = 16

        ToggleButton.Name = "ToggleButton"
        ToggleButton.Parent = Frame
        ToggleButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
        ToggleButton.Size = UDim2.new(0.8, 0, 0.4, 0)
        ToggleButton.Position = UDim2.new(0.1, 0, 0.5, 0)
        ToggleButton.Font = Enum.Font.SourceSans
        ToggleButton.Text = "Ativar Furacão Bósnia"
        ToggleButton.TextColor3 = Color3.new(1, 1, 1)
        ToggleButton.TextSize = 16
        ToggleButton.BorderSizePixel = 0

        local Vibrando = false
        local ConexaoVibracao

        local function AlternarVibracao()
            Vibrando = not Vibrando

            if Vibrando then
                ToggleButton.Text = "Parar Furacão Bósnia"
                
                if Character and Character:FindFirstChild("HumanoidRootPart") then
                    Character.HumanoidRootPart.Anchored = true
                end

                ConexaoVibracao = RunService.Stepped:Connect(function()
                    if Character and Character:FindFirstChild("HumanoidRootPart") and Character:FindFirstChild("Head") then
                        local root = Character.HumanoidRootPart
                        local head = Character.Head

                        root.CFrame = root.CFrame * CFrame.new(
                            math.random(-5, 5) * 0.05,
                            math.random(-5, 5) * 0.05,
                            math.random(-5, 5) * 0.05
                        )

                        head.CFrame = head.CFrame * CFrame.Angles(0, math.rad(math.random(-30, 30)), 0)

                        root.CFrame = root.CFrame * CFrame.Angles(0, math.rad(math.random(-20, 20)), 0)
                    end
                end)
            else
                ToggleButton.Text = "Ativar Furacão Bósnia"

                if Character and Character:FindFirstChild("HumanoidRootPart") then
                    Character.HumanoidRootPart.Anchored = false
                end

                if ConexaoVibracao then
                    ConexaoVibracao:Disconnect()
                end

                if Character and Character:FindFirstChild("Head") then
                    Character.Head.CFrame = Character.HumanoidRootPart.CFrame
                end
            end
        end

        ToggleButton.MouseButton1Click:Connect(AlternarVibracao)
    end
})

local Button = MainTab:CreateButton({
   Name = "Giro Rápido",
   Callback = function()
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer
local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ToggleButton = Instance.new("TextButton")
local Title = Instance.new("TextLabel")

ScreenGui.Parent = game.CoreGui
ScreenGui.Name = "GUIGiroRapido"

Frame.Name = "MainFrame"
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.BorderSizePixel = 0
Frame.Size = UDim2.new(0, 200, 0, 100)
Frame.Position = UDim2.new(0.5, -100, 0.5, -50)
Frame.Draggable = true
Frame.Active = true

Title.Name = "Title"
Title.Parent = Frame
Title.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
Title.Size = UDim2.new(1, 0, 0, 25)
Title.Font = Enum.Font.SourceSansBold
Title.Text = "By Miller"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.TextSize = 16

ToggleButton.Name = "ToggleButton"
ToggleButton.Parent = Frame
ToggleButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
ToggleButton.Size = UDim2.new(0.8, 0, 0.4, 0)
ToggleButton.Position = UDim2.new(0.1, 0, 0.5, 0)
ToggleButton.Font = Enum.Font.SourceSans
ToggleButton.Text = "Ativar Giro Rápido"
ToggleButton.TextColor3 = Color3.new(1, 1, 1)
ToggleButton.TextSize = 16
ToggleButton.BorderSizePixel = 0

local IsToggled = false
local BackAndForthConnection

local function AlternarGiro()
    IsToggled = not IsToggled

    if IsToggled then
        ToggleButton.Text = "Parar Giro Rápido"

        BackAndForthConnection = RunService.Heartbeat:Connect(function()
            if Character and Character:FindFirstChild("HumanoidRootPart") then
                local root = Character.HumanoidRootPart
                local currentLookVector = root.CFrame.LookVector

                if currentLookVector.Z > 0 then
                    root.CFrame = root.CFrame * CFrame.Angles(0, math.pi, 0)
                else
                    root.CFrame = root.CFrame * CFrame.Angles(0, math.pi, 0)
                end

                wait(0.1)
            end
        end)
    else
        ToggleButton.Text = "Ativar Giro Rápido"
        if BackAndForthConnection then
            BackAndForthConnection:Disconnect()
        end
    end
end

ToggleButton.MouseButton1Click:Connect(AlternarGiro)

   end,
})

local Button = MainTab:CreateButton({
   Name = "Ferramenta de Masturbação (Habilite o inventário primeiro)",
   Callback = function()
       loadstring(game:HttpGet("https://pastefy.app/YZoglOyJ/raw"))()
   end,
})

local Button = MainTab:CreateButton({
   Name = "Pulo na Parede",
   Callback = function()
local wallJumpForce = Vector3.new(0, -70, -70)
local wallDetectionDistance = 3
local cooldownTime = 0

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local rootPart = character:WaitForChild("HumanoidRootPart")
local canWallJump = true

local function isNearWall()
    local rayParams = RaycastParams.new()
    rayParams.FilterDescendantsInstances = {character}
    rayParams.FilterType = Enum.RaycastFilterType.Blacklist

    local directions = {
        Vector3.new(1, 0, 0),
        Vector3.new(-1, 0, 0),
        Vector3.new(0, 0, 1),
        Vector3.new(0, 0, -1)
    }

    for _, dir in ipairs(directions) do
        local ray = workspace:Raycast(rootPart.Position, dir * wallDetectionDistance, rayParams)
        if ray then
            return ray
        end
    end

    return nil
end

local function wallJump()
    if not canWallJump then return end

    local wallRay = isNearWall()
    if wallRay then
        canWallJump = false

        local jumpDirection = wallRay.Normal * wallJumpForce.Magnitude
        rootPart.Velocity = Vector3.new(jumpDirection.X, wallJumpForce.Y, jumpDirection.Z)

        humanoid:ChangeState(Enum.HumanoidStateType.Jumping)

        wait(cooldownTime)
        canWallJump = true
    end
end

game:GetService("UserInputService").InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end

    if input.KeyCode == Enum.KeyCode.Space then
        wallJump()
    end
end)
end,
})

local Button = MainTab:CreateButton({
   Name = "Invisibilidade",
   Callback = function()
       loadstring(game:HttpGet('https://pastebin.com/raw/3Rnd9rHf'))()
   end,
})
