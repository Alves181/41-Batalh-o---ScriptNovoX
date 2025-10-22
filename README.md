local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RunService = game:GetService("RunService")
local Lighting = game:GetService("Lighting")
local UserInputService = game:GetService("UserInputService")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Limpar GUI anterior
if playerGui:FindFirstChild("SimpleSpam") then
	playerGui:FindFirstChild("SimpleSpam"):Destroy()
end

-- Criar ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "SimpleSpam"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- Painel principal expandido (aumentado para acomodar novas funcionalidades)
local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 350, 0, 240)
mainFrame.Position = UDim2.new(0.5, -175, 0.5, -120)
mainFrame.BackgroundColor3 = Color3.fromRGB(40, 42, 54)
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Visible = false
mainFrame.Parent = screenGui

-- Imagem de fundo
local backgroundImage = Instance.new("ImageLabel")
backgroundImage.Size = UDim2.new(1, 0, 1, 0)
backgroundImage.Position = UDim2.new(0, 0, 0, 0)
backgroundImage.BackgroundTransparency = 1
backgroundImage.Image = "rbxassetid://75783005071755"
backgroundImage.ImageTransparency = 0.3
backgroundImage.ScaleType = Enum.ScaleType.Crop
backgroundImage.Parent = mainFrame

-- Cantos arredondados
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 8)
corner.Parent = mainFrame

local backgroundCorner = Instance.new("UICorner")
backgroundCorner.CornerRadius = UDim.new(0, 8)
backgroundCorner.Parent = backgroundImage

-- Header rainbow
local header = Instance.new("Frame")
header.Size = UDim2.new(1, 0, 0, 35)
header.Position = UDim2.new(0, 0, 0, 0)
header.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
header.BorderSizePixel = 0
header.Parent = mainFrame

local headerCorner = Instance.new("UICorner")
headerCorner.CornerRadius = UDim.new(0, 8)
headerCorner.Parent = header

local headerFix = Instance.new("Frame")
headerFix.Size = UDim2.new(1, 0, 0, 8)
headerFix.Position = UDim2.new(0, 0, 1, -8)
headerFix.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
headerFix.BorderSizePixel = 0
headerFix.Parent = header

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -100, 1, 0)
title.Position = UDim2.new(0, 10, 0, 0)
title.BackgroundTransparency = 1
title.Text = "41° Batalhão - Script"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.TextSize = 14
title.Font = Enum.Font.SourceSansBold
title.TextXAlignment = Enum.TextXAlignment.Left
title.TextStrokeTransparency = 0.5
title.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
title.Parent = header

-- Botão de hacks visuais (mais visível)
local visualBtn = Instance.new("TextButton")
visualBtn.Size = UDim2.new(0, 30, 0, 25)
visualBtn.Position = UDim2.new(1, -60, 0, 5)
visualBtn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
visualBtn.BorderSizePixel = 1
visualBtn.BorderColor3 = Color3.fromRGB(255, 255, 255)
visualBtn.Text = "👁️"
visualBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
visualBtn.TextSize = 14
visualBtn.Font = Enum.Font.SourceSansBold
visualBtn.TextStrokeTransparency = 0.5
visualBtn.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
visualBtn.Parent = header

local visualBtnCorner = Instance.new("UICorner")
visualBtnCorner.CornerRadius = UDim.new(0, 4)
visualBtnCorner.Parent = visualBtn

-- Botão fechar
local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 25, 0, 25)
closeBtn.Position = UDim2.new(1, -25, 0, 5)
closeBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
closeBtn.BorderSizePixel = 0
closeBtn.Text = "×"
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.TextSize = 14
closeBtn.Font = Enum.Font.SourceSansBold
closeBtn.Parent = header

local closeBtnCorner = Instance.new("UICorner")
closeBtnCorner.CornerRadius = UDim.new(0, 4)
closeBtnCorner.Parent = closeBtn

-- SEÇÃO DE SPAM
local spamSection = Instance.new("Frame")
spamSection.Name = "SpamSection"
spamSection.Size = UDim2.new(1, 0, 1, -35)
spamSection.Position = UDim2.new(0, 0, 0, 35)
spamSection.BackgroundTransparency = 1
spamSection.Visible = true
spamSection.Parent = mainFrame

-- Caixa de texto
local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(1, -20, 0, 35)
textBox.Position = UDim2.new(0, 10, 0, 15)
textBox.BackgroundColor3 = Color3.fromRGB(55, 58, 74)
textBox.BorderSizePixel = 0
textBox.Text = "//Mat - 41 BPM"
textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
textBox.TextSize = 12
textBox.Font = Enum.Font.SourceSans
textBox.PlaceholderText = "Digite sua mensagem..."
textBox.PlaceholderColor3 = Color3.fromRGB(150, 150, 150)
textBox.TextWrapped = true
textBox.Parent = spamSection

local textBoxCorner = Instance.new("UICorner")
textBoxCorner.CornerRadius = UDim.new(0, 6)
textBoxCorner.Parent = textBox

-- Botão de spam
local spamBtn = Instance.new("TextButton")
spamBtn.Size = UDim2.new(1, -20, 0, 40)
spamBtn.Position = UDim2.new(0, 10, 0, 60)
spamBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
spamBtn.BorderSizePixel = 0
spamBtn.Text = "🚀 ENVIAR SPAM"
spamBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
spamBtn.TextSize = 14
spamBtn.Font = Enum.Font.SourceSansBold
spamBtn.TextStrokeTransparency = 0.5
spamBtn.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
spamBtn.Parent = spamSection

local spamBtnCorner = Instance.new("UICorner")
spamBtnCorner.CornerRadius = UDim.new(0, 6)
spamBtnCorner.Parent = spamBtn

-- Toggle para spam com tecla E
local eKeyFrame = Instance.new("Frame")
eKeyFrame.Size = UDim2.new(1, -20, 0, 35)
eKeyFrame.Position = UDim2.new(0, 10, 0, 110)
eKeyFrame.BackgroundColor3 = Color3.fromRGB(55, 58, 74)
eKeyFrame.BorderSizePixel = 0
eKeyFrame.Parent = spamSection

local eKeyFrameCorner = Instance.new("UICorner")
eKeyFrameCorner.CornerRadius = UDim.new(0, 6)
eKeyFrameCorner.Parent = eKeyFrame

local eKeyLabel = Instance.new("TextLabel")
eKeyLabel.Size = UDim2.new(1, -50, 1, 0)
eKeyLabel.Position = UDim2.new(0, 10, 0, 0)
eKeyLabel.BackgroundTransparency = 1
eKeyLabel.Text = "⌨️ Spam com Tecla E"
eKeyLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
eKeyLabel.TextSize = 12
eKeyLabel.Font = Enum.Font.SourceSansBold
eKeyLabel.TextXAlignment = Enum.TextXAlignment.Left
eKeyLabel.Parent = eKeyFrame

local eKeyToggle = Instance.new("TextButton")
eKeyToggle.Size = UDim2.new(0, 35, 0, 20)
eKeyToggle.Position = UDim2.new(1, -40, 0, 7.5)
eKeyToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
eKeyToggle.BorderSizePixel = 0
eKeyToggle.Text = "OFF"
eKeyToggle.TextColor3 = Color3.fromRGB(255, 255, 255)
eKeyToggle.TextSize = 10
eKeyToggle.Font = Enum.Font.SourceSansBold
eKeyToggle.Parent = eKeyFrame

local eKeyToggleCorner = Instance.new("UICorner")
eKeyToggleCorner.CornerRadius = UDim.new(0, 10)
eKeyToggleCorner.Parent = eKeyToggle

-- Status
local status = Instance.new("TextLabel")
status.Size = UDim2.new(1, -20, 0, 15)
status.Position = UDim2.new(0, 10, 0, 155)
status.BackgroundTransparency = 1
status.Text = "Pronto para enviar"
status.TextColor3 = Color3.fromRGB(150, 150, 150)
status.TextSize = 11
status.Font = Enum.Font.SourceSans
status.TextXAlignment = Enum.TextXAlignment.Center
status.Parent = spamSection

-- SEÇÃO DE HACKS VISUAIS (com ScrollFrame para acomodar mais opções)
local visualSection = Instance.new("ScrollingFrame")
visualSection.Name = "VisualSection"
visualSection.Size = UDim2.new(1, 0, 1, -35)
visualSection.Position = UDim2.new(0, 0, 0, 35)
visualSection.BackgroundTransparency = 1
visualSection.BorderSizePixel = 0
visualSection.ScrollBarThickness = 6
visualSection.ScrollBarImageColor3 = Color3.fromRGB(255, 255, 255)
visualSection.CanvasSize = UDim2.new(0, 0, 0, 400)
visualSection.Visible = false
visualSection.Parent = mainFrame

-- ESP Toggle
local espFrame = Instance.new("Frame")
espFrame.Size = UDim2.new(1, -20, 0, 40)
espFrame.Position = UDim2.new(0, 10, 0, 15)
espFrame.BackgroundColor3 = Color3.fromRGB(55, 58, 74)
espFrame.BorderSizePixel = 0
espFrame.Parent = visualSection

local espFrameCorner = Instance.new("UICorner")
espFrameCorner.CornerRadius = UDim.new(0, 6)
espFrameCorner.Parent = espFrame

local espLabel = Instance.new("TextLabel")
espLabel.Size = UDim2.new(1, -50, 1, 0)
espLabel.Position = UDim2.new(0, 10, 0, 0)
espLabel.BackgroundTransparency = 1
espLabel.Text = "👁️ ESP Players"
espLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
espLabel.TextSize = 12
espLabel.Font = Enum.Font.SourceSansBold
espLabel.TextXAlignment = Enum.TextXAlignment.Left
espLabel.Parent = espFrame

local espToggle = Instance.new("TextButton")
espToggle.Size = UDim2.new(0, 35, 0, 20)
espToggle.Position = UDim2.new(1, -40, 0, 10)
espToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
espToggle.BorderSizePixel = 0
espToggle.Text = "OFF"
espToggle.TextColor3 = Color3.fromRGB(255, 255, 255)
espToggle.TextSize = 10
espToggle.Font = Enum.Font.SourceSansBold
espToggle.Parent = espFrame

local espToggleCorner = Instance.new("UICorner")
espToggleCorner.CornerRadius = UDim.new(0, 10)
espToggleCorner.Parent = espToggle

-- FullBright Section
local brightFrame = Instance.new("Frame")
brightFrame.Size = UDim2.new(1, -20, 0, 80)
brightFrame.Position = UDim2.new(0, 10, 0, 65)
brightFrame.BackgroundColor3 = Color3.fromRGB(55, 58, 74)
brightFrame.BorderSizePixel = 0
brightFrame.Parent = visualSection

local brightFrameCorner = Instance.new("UICorner")
brightFrameCorner.CornerRadius = UDim.new(0, 6)
brightFrameCorner.Parent = brightFrame

local brightLabel = Instance.new("TextLabel")
brightLabel.Size = UDim2.new(1, -50, 0, 25)
brightLabel.Position = UDim2.new(0, 10, 0, 5)
brightLabel.BackgroundTransparency = 1
brightLabel.Text = "💡 FullBright"
brightLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
brightLabel.TextSize = 12
brightLabel.Font = Enum.Font.SourceSansBold
brightLabel.TextXAlignment = Enum.TextXAlignment.Left
brightLabel.Parent = brightFrame

local brightToggle = Instance.new("TextButton")
brightToggle.Size = UDim2.new(0, 35, 0, 20)
brightToggle.Position = UDim2.new(1, -40, 0, 7)
brightToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
brightToggle.BorderSizePixel = 0
brightToggle.Text = "OFF"
brightToggle.TextColor3 = Color3.fromRGB(255, 255, 255)
brightToggle.TextSize = 10
brightToggle.Font = Enum.Font.SourceSansBold
brightToggle.Parent = brightFrame

local brightToggleCorner = Instance.new("UICorner")
brightToggleCorner.CornerRadius = UDim.new(0, 10)
brightToggleCorner.Parent = brightToggle

-- Slider de intensidade
local sliderLabel = Instance.new("TextLabel")
sliderLabel.Size = UDim2.new(1, -20, 0, 15)
sliderLabel.Position = UDim2.new(0, 10, 0, 35)
sliderLabel.BackgroundTransparency = 1
sliderLabel.Text = "Intensidade: 2"
sliderLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
sliderLabel.TextSize = 10
sliderLabel.Font = Enum.Font.SourceSans
sliderLabel.TextXAlignment = Enum.TextXAlignment.Left
sliderLabel.Parent = brightFrame

local sliderBg = Instance.new("Frame")
sliderBg.Size = UDim2.new(1, -20, 0, 8)
sliderBg.Position = UDim2.new(0, 10, 0, 55)
sliderBg.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
sliderBg.BorderSizePixel = 0
sliderBg.Parent = brightFrame

local sliderBgCorner = Instance.new("UICorner")
sliderBgCorner.CornerRadius = UDim.new(0, 4)
sliderBgCorner.Parent = sliderBg

local sliderFill = Instance.new("Frame")
sliderFill.Size = UDim2.new(0.4, 0, 1, 0)
sliderFill.Position = UDim2.new(0, 0, 0, 0)
sliderFill.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
sliderFill.BorderSizePixel = 0
sliderFill.Parent = sliderBg

local sliderFillCorner = Instance.new("UICorner")
sliderFillCorner.CornerRadius = UDim.new(0, 4)
sliderFillCorner.Parent = sliderFill

local sliderBtn = Instance.new("TextButton")
sliderBtn.Size = UDim2.new(0, 16, 0, 16)
sliderBtn.Position = UDim2.new(0.4, -8, 0, -4)
sliderBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
sliderBtn.BorderSizePixel = 0
sliderBtn.Text = ""
sliderBtn.Parent = sliderBg

local sliderBtnCorner = Instance.new("UICorner")
sliderBtnCorner.CornerRadius = UDim.new(0, 8)
sliderBtnCorner.Parent = sliderBtn

-- TELEPORT Section
local tpFrame = Instance.new("Frame")
tpFrame.Size = UDim2.new(1, -20, 0, 80)
tpFrame.Position = UDim2.new(0, 10, 0, 155)
tpFrame.BackgroundColor3 = Color3.fromRGB(55, 58, 74)
tpFrame.BorderSizePixel = 0
tpFrame.Parent = visualSection

local tpFrameCorner = Instance.new("UICorner")
tpFrameCorner.CornerRadius = UDim.new(0, 6)
tpFrameCorner.Parent = tpFrame

local tpLabel = Instance.new("TextLabel")
tpLabel.Size = UDim2.new(1, -20, 0, 20)
tpLabel.Position = UDim2.new(0, 10, 0, 5)
tpLabel.BackgroundTransparency = 1
tpLabel.Text = "🚀 Teleport to Player"
tpLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
tpLabel.TextSize = 12
tpLabel.Font = Enum.Font.SourceSansBold
tpLabel.TextXAlignment = Enum.TextXAlignment.Left
tpLabel.Parent = tpFrame

local tpTextBox = Instance.new("TextBox")
tpTextBox.Size = UDim2.new(1, -20, 0, 25)
tpTextBox.Position = UDim2.new(0, 10, 0, 30)
tpTextBox.BackgroundColor3 = Color3.fromRGB(40, 42, 54)
tpTextBox.BorderSizePixel = 0
tpTextBox.Text = ""
tpTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
tpTextBox.TextSize = 11
tpTextBox.Font = Enum.Font.SourceSans
tpTextBox.PlaceholderText = "Digite o nick do player..."
tpTextBox.PlaceholderColor3 = Color3.fromRGB(150, 150, 150)
tpTextBox.Parent = tpFrame

local tpTextBoxCorner = Instance.new("UICorner")
tpTextBoxCorner.CornerRadius = UDim.new(0, 4)
tpTextBoxCorner.Parent = tpTextBox

local tpBtn = Instance.new("TextButton")
tpBtn.Size = UDim2.new(0, 60, 0, 20)
tpBtn.Position = UDim2.new(1, -65, 0, 55)
tpBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
tpBtn.BorderSizePixel = 0
tpBtn.Text = "TELEPORT"
tpBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
tpBtn.TextSize = 9
tpBtn.Font = Enum.Font.SourceSansBold
tpBtn.Parent = tpFrame

local tpBtnCorner = Instance.new("UICorner")
tpBtnCorner.CornerRadius = UDim.new(0, 4)
tpBtnCorner.Parent = tpBtn

-- SPEED Section
local speedFrame = Instance.new("Frame")
speedFrame.Size = UDim2.new(1, -20, 0, 100)
speedFrame.Position = UDim2.new(0, 10, 0, 245)
speedFrame.BackgroundColor3 = Color3.fromRGB(55, 58, 74)
speedFrame.BorderSizePixel = 0
speedFrame.Parent = visualSection

local speedFrameCorner = Instance.new("UICorner")
speedFrameCorner.CornerRadius = UDim.new(0, 6)
speedFrameCorner.Parent = speedFrame

local speedLabel = Instance.new("TextLabel")
speedLabel.Size = UDim2.new(1, -50, 0, 25)
speedLabel.Position = UDim2.new(0, 10, 0, 5)
speedLabel.BackgroundTransparency = 1
speedLabel.Text = "⚡ Speed Hack"
speedLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
speedLabel.TextSize = 12
speedLabel.Font = Enum.Font.SourceSansBold
speedLabel.TextXAlignment = Enum.TextXAlignment.Left
speedLabel.Parent = speedFrame

local speedToggle = Instance.new("TextButton")
speedToggle.Size = UDim2.new(0, 35, 0, 20)
speedToggle.Position = UDim2.new(1, -40, 0, 7)
speedToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
speedToggle.BorderSizePixel = 0
speedToggle.Text = "OFF"
speedToggle.TextColor3 = Color3.fromRGB(255, 255, 255)
speedToggle.TextSize = 10
speedToggle.Font = Enum.Font.SourceSansBold
speedToggle.Parent = speedFrame

local speedToggleCorner = Instance.new("UICorner")
speedToggleCorner.CornerRadius = UDim.new(0, 10)
speedToggleCorner.Parent = speedToggle

-- Slider de velocidade
local speedSliderLabel = Instance.new("TextLabel")
speedSliderLabel.Size = UDim2.new(1, -20, 0, 15)
speedSliderLabel.Position = UDim2.new(0, 10, 0, 35)
speedSliderLabel.BackgroundTransparency = 1
speedSliderLabel.Text = "Velocidade: 16"
speedSliderLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
speedSliderLabel.TextSize = 10
speedSliderLabel.Font = Enum.Font.SourceSans
speedSliderLabel.TextXAlignment = Enum.TextXAlignment.Left
speedSliderLabel.Parent = speedFrame

local speedSliderBg = Instance.new("Frame")
speedSliderBg.Size = UDim2.new(1, -20, 0, 8)
speedSliderBg.Position = UDim2.new(0, 10, 0, 55)
speedSliderBg.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
speedSliderBg.BorderSizePixel = 0
speedSliderBg.Parent = speedFrame

local speedSliderBgCorner = Instance.new("UICorner")
speedSliderBgCorner.CornerRadius = UDim.new(0, 4)
speedSliderBgCorner.Parent = speedSliderBg

local speedSliderFill = Instance.new("Frame")
speedSliderFill.Size = UDim2.new(0, 0, 1, 0)
speedSliderFill.Position = UDim2.new(0, 0, 0, 0)
speedSliderFill.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
speedSliderFill.BorderSizePixel = 0
speedSliderFill.Parent = speedSliderBg

local speedSliderFillCorner = Instance.new("UICorner")
speedSliderFillCorner.CornerRadius = UDim.new(0, 4)
speedSliderFillCorner.Parent = speedSliderFill

local speedSliderBtn = Instance.new("TextButton")
speedSliderBtn.Size = UDim2.new(0, 16, 0, 16)
speedSliderBtn.Position = UDim2.new(0, -8, 0, -4)
speedSliderBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
speedSliderBtn.BorderSizePixel = 0
speedSliderBtn.Text = ""
speedSliderBtn.Parent = speedSliderBg

local speedSliderBtnCorner = Instance.new("UICorner")
speedSliderBtnCorner.CornerRadius = UDim.new(0, 8)
speedSliderBtnCorner.Parent = speedSliderBtn

-- Campo de entrada manual de velocidade
local speedTextBox = Instance.new("TextBox")
speedTextBox.Size = UDim2.new(0, 60, 0, 20)
speedTextBox.Position = UDim2.new(0, 10, 0, 75)
speedTextBox.BackgroundColor3 = Color3.fromRGB(40, 42, 54)
speedTextBox.BorderSizePixel = 0
speedTextBox.Text = "16"
speedTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
speedTextBox.TextSize = 10
speedTextBox.Font = Enum.Font.SourceSans
speedTextBox.PlaceholderText = "16"
speedTextBox.PlaceholderColor3 = Color3.fromRGB(150, 150, 150)
speedTextBox.Parent = speedFrame

local speedTextBoxCorner = Instance.new("UICorner")
speedTextBoxCorner.CornerRadius = UDim.new(0, 4)
speedTextBoxCorner.Parent = speedTextBox

local speedSetBtn = Instance.new("TextButton")
speedSetBtn.Size = UDim2.new(0, 40, 0, 20)
speedSetBtn.Position = UDim2.new(0, 75, 0, 75)
speedSetBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
speedSetBtn.BorderSizePixel = 0
speedSetBtn.Text = "SET"
speedSetBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
speedSetBtn.TextSize = 9
speedSetBtn.Font = Enum.Font.SourceSansBold
speedSetBtn.Parent = speedFrame

local speedSetBtnCorner = Instance.new("UICorner")
speedSetBtnCorner.CornerRadius = UDim.new(0, 4)
speedSetBtnCorner.Parent = speedSetBtn

-- Botão de toggle principal (com imagem original)
local toggleBtn = Instance.new("ImageButton")
toggleBtn.Name = "ToggleButton"
toggleBtn.Size = UDim2.new(0, 50, 0, 50)
toggleBtn.Position = UDim2.new(0, 20, 0, 100)
toggleBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
toggleBtn.BorderSizePixel = 0
toggleBtn.Image = "rbxassetid://115515766727055"
toggleBtn.Active = true
toggleBtn.Draggable = true
toggleBtn.Parent = screenGui

local toggleBtnCorner = Instance.new("UICorner")
toggleBtnCorner.CornerRadius = UDim.new(0, 25)
toggleBtnCorner.Parent = toggleBtn

-- Variáveis
local rainbowColors = {
	Color3.fromRGB(139, 0, 0),   -- Vermelho escuro
	Color3.fromRGB(0, 100, 0),   -- Verde escuro
	Color3.fromRGB(0, 100, 255)  -- Azul
}
local currentColorIndex = 1
local isOpen = false
local currentSection = "spam" -- "spam" ou "visual"
local espEnabled = false
local fullbrightEnabled = false
local speedEnabled = false
local eKeySpamEnabled = false
local brightIntensity = 2
local speedValue = 16
local originalLighting = {}
local originalSpeed = 16
local espObjects = {}
local speedConnection = nil
local eKeyConnection = nil

-- Salvar configurações de iluminação originais
originalLighting.Brightness = Lighting.Brightness
originalLighting.Ambient = Lighting.Ambient
originalLighting.OutdoorAmbient = Lighting.OutdoorAmbient

-- Sistema Rainbow
local function startRainbow()
	spawn(function()
		while true do
			local targetColor = rainbowColors[currentColorIndex]
			local tweenInfo = TweenInfo.new(1.5, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut)

			TweenService:Create(header, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(headerFix, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(spamBtn, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(toggleBtn, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(closeBtn, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(sliderFill, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(speedSliderFill, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(tpBtn, tweenInfo, {BackgroundColor3 = targetColor}):Play()
			TweenService:Create(speedSetBtn, tweenInfo, {BackgroundColor3 = targetColor}):Play()

			currentColorIndex = currentColorIndex + 1
			if currentColorIndex > #rainbowColors then
				currentColorIndex = 1
			end

			wait(1.5)
		end
	end)
end

-- ESP System
local function createESP(player)
	if player == Players.LocalPlayer then return end
	if espObjects[player] then return end

	local character = player.Character
	if not character then return end

	local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
	if not humanoidRootPart then return end

	-- Criar highlight sutil
	local highlight = Instance.new("Highlight")
	highlight.Name = "UltraGazESP"
	highlight.Adornee = character
	highlight.FillColor = Color3.new(1, 1, 1)
	highlight.FillTransparency = 0.7
	highlight.OutlineColor = Color3.new(0, 1, 1)
	highlight.OutlineTransparency = 0.3
	highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
	highlight.Parent = character

	espObjects[player] = highlight
end

local function removeESP(player)
	if espObjects[player] then
		espObjects[player]:Destroy()
		espObjects[player] = nil
	end
end

local function toggleESP()
	espEnabled = not espEnabled

	if espEnabled then
		espToggle.BackgroundColor3 = Color3.fromRGB(92, 184, 92)
		espToggle.Text = "ON"

		-- Adicionar ESP para todos os jogadores
		for _, player in pairs(Players:GetPlayers()) do
			if player.Character then
				createESP(player)
			end
		end

		-- Conectar eventos
		Players.PlayerAdded:Connect(function(player)
			if espEnabled then
				player.CharacterAdded:Connect(function()
					wait(1)
					if espEnabled then
						createESP(player)
					end
				end)
			end
		end)

	else
		espToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
		espToggle.Text = "OFF"

		-- Remover todos os ESP
		for player, _ in pairs(espObjects) do
			removeESP(player)
		end
	end
end

-- FullBright System
local function toggleFullBright()
	fullbrightEnabled = not fullbrightEnabled

	if fullbrightEnabled then
		brightToggle.BackgroundColor3 = Color3.fromRGB(92, 184, 92)
		brightToggle.Text = "ON"

		-- Aplicar fullbright
		Lighting.Brightness = brightIntensity
		Lighting.Ambient = Color3.new(1, 1, 1)
		Lighting.OutdoorAmbient = Color3.new(1, 1, 1)

	else
		brightToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
		brightToggle.Text = "OFF"

		-- Restaurar iluminação original
		Lighting.Brightness = originalLighting.Brightness
		Lighting.Ambient = originalLighting.Ambient
		Lighting.OutdoorAmbient = originalLighting.OutdoorAmbient
	end
end

-- Teleport System
local function teleportToPlayer()
	local targetName = tpTextBox.Text:lower()
	if targetName == "" then return end

	local targetPlayer = nil
	for _, player in pairs(Players:GetPlayers()) do
		if player.Name:lower():find(targetName) or player.DisplayName:lower():find(targetName) then
			targetPlayer = player
			break
		end
	end

	if not targetPlayer then
		-- Mostrar erro temporariamente
		local originalText = tpTextBox.Text
		tpTextBox.Text = "Player não encontrado!"
		tpTextBox.TextColor3 = Color3.fromRGB(255, 95, 87)
		wait(2)
		tpTextBox.Text = originalText
		tpTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
		return
	end

	if targetPlayer == Players.LocalPlayer then
		local originalText = tpTextBox.Text
		tpTextBox.Text = "Não pode teleportar para si mesmo!"
		tpTextBox.TextColor3 = Color3.fromRGB(255, 95, 87)
		wait(2)
		tpTextBox.Text = originalText
		tpTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
		return
	end

	local character = Players.LocalPlayer.Character
	local targetCharacter = targetPlayer.Character

	if character and targetCharacter then
		local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
		local targetHumanoidRootPart = targetCharacter:FindFirstChild("HumanoidRootPart")

		if humanoidRootPart and targetHumanoidRootPart then
			humanoidRootPart.CFrame = targetHumanoidRootPart.CFrame + Vector3.new(0, 0, -3)
			-- Mostrar sucesso temporariamente
			local originalText = tpTextBox.Text
			tpTextBox.Text = "Teleportado para " .. targetPlayer.Name .. "!"
			tpTextBox.TextColor3 = Color3.fromRGB(92, 184, 92)
			wait(2)
			tpTextBox.Text = originalText
			tpTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
		end
	end
end

-- Speed System
local function updateSpeedValue()
	local humanoid = nil
	if Players.LocalPlayer.Character then
		humanoid = Players.LocalPlayer.Character:FindFirstChild("Humanoid")
	end

	if humanoid and speedEnabled then
		humanoid.WalkSpeed = speedValue
	end
end

local function toggleSpeed()
	speedEnabled = not speedEnabled

	if speedEnabled then
		speedToggle.BackgroundColor3 = Color3.fromRGB(92, 184, 92)
		speedToggle.Text = "ON"

		-- Aplicar velocidade
		updateSpeedValue()

		-- Conectar para manter a velocidade quando o character respawnar
		speedConnection = Players.LocalPlayer.CharacterAdded:Connect(function()
			wait(1)
			if speedEnabled then
				updateSpeedValue()
			end
		end)

	else
		speedToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
		speedToggle.Text = "OFF"

		-- Restaurar velocidade original
		if Players.LocalPlayer.Character then
			local humanoid = Players.LocalPlayer.Character:FindFirstChild("Humanoid")
			if humanoid then
				humanoid.WalkSpeed = originalSpeed
			end
		end

		-- Desconectar evento
		if speedConnection then
			speedConnection:Disconnect()
			speedConnection = nil
		end
	end
end

-- Slider System (FullBright)
local function updateSlider()
	local percentage = (brightIntensity - 0.5) / 4.5 -- 0.5 a 5 = 0 a 1
	sliderFill.Size = UDim2.new(percentage, 0, 1, 0)
	sliderBtn.Position = UDim2.new(percentage, -8, 0, -4)
	sliderLabel.Text = "Intensidade: " .. tostring(brightIntensity)

	if fullbrightEnabled then
		Lighting.Brightness = brightIntensity
	end
end

-- Speed Slider System
local function updateSpeedSlider()
	local percentage = (speedValue - 16) / 84 -- 16 a 100 = 0 a 1
	speedSliderFill.Size = UDim2.new(percentage, 0, 1, 0)
	speedSliderBtn.Position = UDim2.new(percentage, -8, 0, -4)
	speedSliderLabel.Text = "Velocidade: " .. tostring(speedValue)
	speedTextBox.Text = tostring(speedValue)

	if speedEnabled then
		updateSpeedValue()
	end
end

-- Slider dragging (FullBright)
local dragging = false
sliderBtn.MouseButton1Down:Connect(function()
	dragging = true
end)

UserInputService.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = false
		speedDragging = false
	end
end)

UserInputService.InputChanged:Connect(function(input)
	if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
		local mouse = Players.LocalPlayer:GetMouse()
		local sliderPos = sliderBg.AbsolutePosition.X
		local sliderSize = sliderBg.AbsoluteSize.X
		local mouseX = mouse.X

		local percentage = math.clamp((mouseX - sliderPos) / sliderSize, 0, 1)
		brightIntensity = math.round((percentage * 4.5 + 0.5) * 10) / 10

		updateSlider()
	elseif speedDragging and input.UserInputType == Enum.UserInputType.MouseMovement then
		local mouse = Players.LocalPlayer:GetMouse()
		local sliderPos = speedSliderBg.AbsolutePosition.X
		local sliderSize = speedSliderBg.AbsoluteSize.X
		local mouseX = mouse.X

		local percentage = math.clamp((mouseX - sliderPos) / sliderSize, 0, 1)
		speedValue = math.floor(percentage * 84 + 16)

		updateSpeedSlider()
	end
end)

-- Speed Slider dragging
local speedDragging = false
speedSliderBtn.MouseButton1Down:Connect(function()
	speedDragging = true
end)

-- Função para alternar seções
local function switchSection()
	if currentSection == "spam" then
		currentSection = "visual"
		spamSection.Visible = false
		visualSection.Visible = true
		title.Text = "41° Batalhão - Hacks"
		-- Expandir painel para acomodar mais conteúdo
		mainFrame.Size = UDim2.new(0, 350, 0, 250)
		mainFrame.Position = UDim2.new(0.5, -175, 0.5, -125)
	else
		currentSection = "spam"
		spamSection.Visible = true
		visualSection.Visible = false
		title.Text = "41° Batalhão - Script"
		-- Voltar ao tamanho original
		mainFrame.Size = UDim2.new(0, 350, 0, 240)
		mainFrame.Position = UDim2.new(0.5, -175, 0.5, -120)
	end
end

-- Função para abrir/fechar
local function togglePanel()
	isOpen = not isOpen

	if isOpen then
		mainFrame.Visible = true
		if currentSection == "visual" then
			mainFrame.Size = UDim2.new(0, 50, 0, 50)
			mainFrame.Position = UDim2.new(0.5, -25, 0.5, -25)

			TweenService:Create(mainFrame, TweenInfo.new(0.25, Enum.EasingStyle.Quart), {
				Size = UDim2.new(0, 350, 0, 250),
				Position = UDim2.new(0.5, -175, 0.5, -125)
			}):Play()
		else
			mainFrame.Size = UDim2.new(0, 50, 0, 50)
			mainFrame.Position = UDim2.new(0.5, -25, 0.5, -25)

			TweenService:Create(mainFrame, TweenInfo.new(0.25, Enum.EasingStyle.Quart), {
				Size = UDim2.new(0, 350, 0, 240),
				Position = UDim2.new(0.5, -175, 0.5, -120)
			}):Play()
		end

		-- Efeito visual no botão de toggle
		TweenService:Create(toggleBtn, TweenInfo.new(0.2), {
			BackgroundColor3 = Color3.fromRGB(50, 150, 50)
		}):Play()
	else
		local closeTween = TweenService:Create(mainFrame, TweenInfo.new(0.2, Enum.EasingStyle.Quart), {
			Size = UDim2.new(0, 50, 0, 50),
			Position = UDim2.new(0.5, -25, 0.5, -25)
		})

		closeTween:Play()
		closeTween.Completed:Connect(function()
			mainFrame.Visible = false
		end)
	end
end

-- Função de envio de spam
local function sendMessage()
	local message = textBox.Text
	if message == "" or message:gsub("%s+", "") == "" then
		status.Text = "Digite alguma coisa!"
		status.TextColor3 = Color3.fromRGB(255, 95, 87)
		wait(2)
		status.Text = "Pronto para enviar"
		status.TextColor3 = Color3.fromRGB(150, 150, 150)
		return
	end

	status.Text = "Enviado!"
	status.TextColor3 = Color3.fromRGB(92, 184, 92)

	pcall(function()
		if ReplicatedStorage:FindFirstChild("DefaultChatSystemChatEvents") then
			local folder = ReplicatedStorage.DefaultChatSystemChatEvents
			if folder:FindFirstChild("SayMessageRequest") then
				folder.SayMessageRequest:FireServer(message, "All")
				return
			end
		end

		local TextChatService = game:GetService("TextChatService")
		if TextChatService then
			local textChannels = TextChatService:FindFirstChild("TextChannels")
			if textChannels then
				local general = textChannels:FindFirstChild("RBXGeneral")
				if general then
					general:SendAsync(message)
					return
				end
			end
		end
	end)

	wait(1.5)
	status.Text = "Pronto para enviar"
	status.TextColor3 = Color3.fromRGB(150, 150, 150)
end

-- Sistema de spam com tecla E
local function toggleEKeySpam()
	eKeySpamEnabled = not eKeySpamEnabled

	if eKeySpamEnabled then
		eKeyToggle.BackgroundColor3 = Color3.fromRGB(92, 184, 92)
		eKeyToggle.Text = "ON"

		-- Conectar evento da tecla E
		eKeyConnection = UserInputService.InputBegan:Connect(function(input, gameProcessed)
			if gameProcessed then return end
			if input.KeyCode == Enum.KeyCode.E then
				sendMessage()
			end
		end)

		status.Text = "Spam com tecla E ativado!"
		status.TextColor3 = Color3.fromRGB(92, 184, 92)
		wait(2)
		status.Text = "Pronto para enviar"
		status.TextColor3 = Color3.fromRGB(150, 150, 150)

	else
		eKeyToggle.BackgroundColor3 = Color3.fromRGB(255, 95, 87)
		eKeyToggle.Text = "OFF"

		-- Desconectar evento
		if eKeyConnection then
			eKeyConnection:Disconnect()
			eKeyConnection = nil
		end

		status.Text = "Spam com tecla E desativado"
		status.TextColor3 = Color3.fromRGB(255, 95, 87)
		wait(2)
		status.Text = "Pronto para enviar"
		status.TextColor3 = Color3.fromRGB(150, 150, 150)
	end
end

-- Inicializar
startRainbow()
updateSlider()
updateSpeedSlider()

-- Eventos
toggleBtn.MouseButton1Click:Connect(togglePanel)
closeBtn.MouseButton1Click:Connect(togglePanel)
visualBtn.MouseButton1Click:Connect(switchSection)
spamBtn.MouseButton1Click:Connect(sendMessage)
espToggle.MouseButton1Click:Connect(toggleESP)
brightToggle.MouseButton1Click:Connect(toggleFullBright)
tpBtn.MouseButton1Click:Connect(teleportToPlayer)
speedToggle.MouseButton1Click:Connect(toggleSpeed)
eKeyToggle.MouseButton1Click:Connect(toggleEKeySpam)

-- Evento para definir velocidade manualmente
speedSetBtn.MouseButton1Click:Connect(function()
	local newSpeed = tonumber(speedTextBox.Text)
	if newSpeed and newSpeed >= 16 and newSpeed <= 100 then
		speedValue = newSpeed
		updateSpeedSlider()
	else
		speedTextBox.Text = tostring(speedValue)
	end
end)

-- Evento para teleporte com Enter
tpTextBox.FocusLost:Connect(function(enterPressed)
	if enterPressed then
		teleportToPlayer()
	end
end)

-- Evento para speed com Enter
speedTextBox.FocusLost:Connect(function(enterPressed)
	if enterPressed then
		local newSpeed = tonumber(speedTextBox.Text)
		if newSpeed and newSpeed >= 16 and newSpeed <= 100 then
			speedValue = newSpeed
			updateSpeedSlider()
		else
			speedTextBox.Text = tostring(speedValue)
		end
	end
end)

textBox.FocusLost:Connect(function(enterPressed)
	if enterPressed then
		sendMessage()
	end
end)

-- Efeito hover no botão visual
visualBtn.MouseEnter:Connect(function()
	TweenService:Create(visualBtn, TweenInfo.new(0.2), {
		BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	}):Play()
end)

visualBtn.MouseLeave:Connect(function()
	TweenService:Create(visualBtn, TweenInfo.new(0.2), {
		BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	}):Play()
end)

-- Efeito hover no botão de toggle
toggleBtn.MouseEnter:Connect(function()
	if not isOpen then
		TweenService:Create(toggleBtn, TweenInfo.new(0.2), {
			Size = UDim2.new(0, 55, 0, 55)
		}):Play()
	end
end)

toggleBtn.MouseLeave:Connect(function()
	if not isOpen then
		TweenService:Create(toggleBtn, TweenInfo.new(0.2), {
			Size = UDim2.new(0, 50, 0, 50)
		}):Play()
	end
end)****
