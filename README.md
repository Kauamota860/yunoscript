--// Yuno Scripts Hub
--// ESP Team + Speed + Noclip + Key System

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

-- KEYS
local Keys = {
	"YUNO-X7A91",
	"YUNO-P4K82",
	"YUNO-L9Q13",
	"YUNO-T5M77",
	"YUNO-V2B44",
	"YUNO-H8Z66",
	"YUNO-R3D21",
	"YUNO-N1F90"
}

-- GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "YunoScripts"
ScreenGui.Parent = game.CoreGui
ScreenGui.ResetOnSpawn = false

-- MAIN
local Main = Instance.new("Frame")
Main.Parent = ScreenGui
Main.Size = UDim2.new(0, 420, 0, 300)
Main.Position = UDim2.new(0.35, 0, 0.25, 0)
Main.BackgroundColor3 = Color3.fromRGB(10,10,10)
Main.BorderSizePixel = 0
Main.Active = true
Main.Draggable = true
Main.Visible = false

local UICorner = Instance.new("UICorner", Main)
UICorner.CornerRadius = UDim.new(0,12)

-- TITLE
local Title = Instance.new("TextLabel")
Title.Parent = Main
Title.Size = UDim2.new(1,0,0,45)
Title.BackgroundTransparency = 1
Title.Text = "Yuno Scripts"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 26

-- MINIMIZE
local Minimize = Instance.new("TextButton")
Minimize.Parent = Main
Minimize.Size = UDim2.new(0,35,0,35)
Minimize.Position = UDim2.new(1,-45,0,5)
Minimize.Text = "-"
Minimize.Font = Enum.Font.GothamBold
Minimize.TextSize = 25
Minimize.TextColor3 = Color3.fromRGB(255,255,255)
Minimize.BackgroundColor3 = Color3.fromRGB(30,30,30)

local MinCorner = Instance.new("UICorner", Minimize)
MinCorner.CornerRadius = UDim.new(1,0)

local Closed = false

Minimize.MouseButton1Click:Connect(function()
	Closed = not Closed
	
	for _,v in pairs(Main:GetChildren()) do
		if v:IsA("Frame") and v.Name ~= "TopBar" then
			v.Visible = not Closed
		end
	end
	
	if Closed then
		Main.Size = UDim2.new(0,420,0,50)
	else
		Main.Size = UDim2.new(0,420,0,300)
	end
end)

-- KEY SYSTEM
local KeyFrame = Instance.new("Frame")
KeyFrame.Parent = ScreenGui
KeyFrame.Size = UDim2.new(0,350,0,220)
KeyFrame.Position = UDim2.new(0.38,0,0.3,0)
KeyFrame.BackgroundColor3 = Color3.fromRGB(15,15,15)
KeyFrame.BorderSizePixel = 0
KeyFrame.Active = true
KeyFrame.Draggable = true

local KeyCorner = Instance.new("UICorner", KeyFrame)
KeyCorner.CornerRadius = UDim.new(0,12)

local KeyTitle = Instance.new("TextLabel")
KeyTitle.Parent = KeyFrame
KeyTitle.Size = UDim2.new(1,0,0,50)
KeyTitle.BackgroundTransparency = 1
KeyTitle.Text = "Yuno Scripts | KEY SYSTEM"
KeyTitle.Font = Enum.Font.GothamBold
KeyTitle.TextSize = 22
KeyTitle.TextColor3 = Color3.new(1,1,1)

local KeyBox = Instance.new("TextBox")
KeyBox.Parent = KeyFrame
KeyBox.Size = UDim2.new(0,280,0,45)
KeyBox.Position = UDim2.new(0,35,0,70)
KeyBox.PlaceholderText = "Digite sua Key..."
KeyBox.Text = ""
KeyBox.Font = Enum.Font.Gotham
KeyBox.TextSize = 18
KeyBox.TextColor3 = Color3.new(1,1,1)
KeyBox.BackgroundColor3 = Color3.fromRGB(25,25,25)

local BoxCorner = Instance.new("UICorner", KeyBox)
BoxCorner.CornerRadius = UDim.new(0,8)

local CheckButton = Instance.new("TextButton")
CheckButton.Parent = KeyFrame
CheckButton.Size = UDim2.new(0,130,0,40)
CheckButton.Position = UDim2.new(0,35,0,130)
CheckButton.Text = "VERIFICAR"
CheckButton.Font = Enum.Font.GothamBold
CheckButton.TextSize = 18
CheckButton.TextColor3 = Color3.new(1,1,1)
CheckButton.BackgroundColor3 = Color3.fromRGB(0,170,255)

local CheckCorner = Instance.new("UICorner", CheckButton)
CheckCorner.CornerRadius = UDim.new(0,8)

local GetKeyButton = Instance.new("TextButton")
GetKeyButton.Parent = KeyFrame
GetKeyButton.Size = UDim2.new(0,130,0,40)
GetKeyButton.Position = UDim2.new(0,185,0,130)
GetKeyButton.Text = "PEGAR KEY"
GetKeyButton.Font = Enum.Font.GothamBold
GetKeyButton.TextSize = 18
GetKeyButton.TextColor3 = Color3.new(1,1,1)
GetKeyButton.BackgroundColor3 = Color3.fromRGB(255,90,90)

local GetCorner = Instance.new("UICorner", GetKeyButton)
GetCorner.CornerRadius = UDim.new(0,8)

local Status = Instance.new("TextLabel")
Status.Parent = KeyFrame
Status.Size = UDim2.new(1,0,0,30)
Status.Position = UDim2.new(0,0,1,-35)
Status.BackgroundTransparency = 1
Status.Text = "Pegue sua key válida por 24h"
Status.Font = Enum.Font.Gotham
Status.TextSize = 16
Status.TextColor3 = Color3.fromRGB(200,200,200)

-- VERIFY KEY
CheckButton.MouseButton1Click:Connect(function()
	local Valid = false
	
	for _,Key in pairs(Keys) do
		if KeyBox.Text == Key then
			Valid = true
			break
		end
	end
	
	if Valid then
		KeyFrame:Destroy()
		Main.Visible = true
	else
		Status.Text = "Key inválida!"
		Status.TextColor3 = Color3.fromRGB(255,0,0)
	end
end)

-- GET KEY
GetKeyButton.MouseButton1Click:Connect(function()
	setclipboard("https://wa.me/5585992886293")
	
	Status.Text = "WhatsApp do dono copiado!"
	Status.TextColor3 = Color3.fromRGB(0,255,0)
end)

-- CONTENT
local Container = Instance.new("Frame")
Container.Parent = Main
Container.BackgroundTransparency = 1
Container.Position = UDim2.new(0,0,0,50)
Container.Size = UDim2.new(1,0,1,-50)

-- ESP BUTTON
local EspButton = Instance.new("TextButton")
EspButton.Parent = Container
EspButton.Size = UDim2.new(0,180,0,45)
EspButton.Position = UDim2.new(0,20,0,20)
EspButton.Text = "ESP PLAYERS"
EspButton.Font = Enum.Font.GothamBold
EspButton.TextSize = 18
EspButton.TextColor3 = Color3.new(1,1,1)
EspButton.BackgroundColor3 = Color3.fromRGB(255,90,90)

local EspCorner = Instance.new("UICorner", EspButton)
EspCorner.CornerRadius = UDim.new(0,8)

-- SPEED BUTTON
local SpeedButton = Instance.new("TextButton")
SpeedButton.Parent = Container
SpeedButton.Size = UDim2.new(0,180,0,45)
SpeedButton.Position = UDim2.new(0,20,0,80)
SpeedButton.Text = "SPEED: OFF"
SpeedButton.Font = Enum.Font.GothamBold
SpeedButton.TextSize = 18
SpeedButton.TextColor3 = Color3.new(1,1,1)
SpeedButton.BackgroundColor3 = Color3.fromRGB(255,90,90)

local SpeedCorner = Instance.new("UICorner", SpeedButton)
SpeedCorner.CornerRadius = UDim.new(0,8)

-- NOCLIP BUTTON
local NoclipButton = Instance.new("TextButton")
NoclipButton.Parent = Container
NoclipButton.Size = UDim2.new(0,180,0,45)
NoclipButton.Position = UDim2.new(0,20,0,140)
NoclipButton.Text = "NOCLIP: OFF"
NoclipButton.Font = Enum.Font.GothamBold
NoclipButton.TextSize = 18
NoclipButton.TextColor3 = Color3.new(1,1,1)
NoclipButton.BackgroundColor3 = Color3.fromRGB(255,90,90)

local NoclipCorner = Instance.new("UICorner", NoclipButton)
NoclipCorner.CornerRadius = UDim.new(0,8)

-- ESP
local ESPEnabled = false
local ESPs = {}

local function CreateESP(player)
	if player == LocalPlayer then return end
	
	local Highlight = Instance.new("Highlight")
	Highlight.Parent = player.Character or player.CharacterAdded:Wait()
	Highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
	
	if player.Team == LocalPlayer.Team then
		Highlight.FillColor = Color3.fromRGB(0,170,255)
	else
		Highlight.FillColor = Color3.fromRGB(255,0,0)
	end
	
	Highlight.OutlineColor = Color3.new(1,1,1)
	
	ESPs[player] = Highlight
end

local function RemoveESP()
	for _,v in pairs(ESPs) do
		if v then
			v:Destroy()
		end
	end
	ESPs = {}
end

EspButton.MouseButton1Click:Connect(function()
	ESPEnabled = not ESPEnabled
	
	if ESPEnabled then
		for _,plr in pairs(Players:GetPlayers()) do
			if plr ~= LocalPlayer then
				CreateESP(plr)
			end
		end
		
		EspButton.Text = "ESP PLAYERS: ON"
	else
		RemoveESP()
		EspButton.Text = "ESP PLAYERS: OFF"
	end
end)

Players.PlayerAdded:Connect(function(plr)
	plr.CharacterAdded:Connect(function()
		if ESPEnabled then
			CreateESP(plr)
		end
	end)
end)

-- SPEED
local SpeedEnabled = false

SpeedButton.MouseButton1Click:Connect(function()
	SpeedEnabled = not SpeedEnabled
	
	local char = LocalPlayer.Character
	if char and char:FindFirstChild("Humanoid") then
		if SpeedEnabled then
			char.Humanoid.WalkSpeed = 50
			SpeedButton.Text = "SPEED: ON"
		else
			char.Humanoid.WalkSpeed = 16
			SpeedButton.Text = "SPEED: OFF"
		end
	end
end)

-- NOCLIP
local Noclip = false

NoclipButton.MouseButton1Click:Connect(function()
	Noclip = not Noclip
	
	if Noclip then
		NoclipButton.Text = "NOCLIP: ON"
	else
		NoclipButton.Text = "NOCLIP: OFF"
	end
end)

RunService.Stepped:Connect(function()
	if Noclip and LocalPlayer.Character then
		for _,v in pairs(LocalPlayer.Character:GetDescendants()) do
			if v:IsA("BasePart") then
				v.CanCollide = false
			end
		end
	end
end)
