local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "FetlessGui"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local function addShadow(instance)
	local stroke = Instance.new("UIStroke")
	stroke.Color = Color3.fromRGB(0, 0, 0)
	stroke.Thickness = 1.2
	stroke.Transparency = 0.4
	stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
	stroke.Parent = instance
end

local function styleButton(button)
	button.AutoButtonColor = false
	addShadow(button)
	local stroke = Instance.new("UIStroke", button)
	stroke.Color = Color3.fromRGB(255, 255, 255)
	stroke.Thickness = 1
	stroke.Transparency = 0.6
	stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

	button.MouseEnter:Connect(function()
		TweenService:Create(button, TweenInfo.new(0.2), {BackgroundTransparency = 0.1}):Play()
	end)
	button.MouseLeave:Connect(function()
		TweenService:Create(button, TweenInfo.new(0.2), {BackgroundTransparency = 0}):Play()
	end)
end

-- Botão de Abrir
local openBtn = Instance.new("ImageButton", gui)
openBtn.Name = "OpenButton"
openBtn.Size = UDim2.new(0, 50, 0, 50)
openBtn.Position = UDim2.new(0, 20, 0.5, -25)
openBtn.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
openBtn.Image = "rbxthumb://type=Asset&id=130800893288109&w=420&h=420"
openBtn.Draggable = true
openBtn.Active = true
Instance.new("UICorner", openBtn)
addShadow(openBtn)

-- Painel principal
local panel = Instance.new("Frame", gui)
panel.Size = UDim2.new(0, 300, 0, 390) -- Aumentei altura para caber mais botões
panel.Position = UDim2.new(0.5, -150, 0.5, -195)
panel.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
panel.BackgroundTransparency = 0.2
panel.Visible = false
panel.ZIndex = 1
Instance.new("UICorner", panel)
addShadow(panel)

-- Fundo da GUI
local bg = Instance.new("ImageLabel", panel)
bg.Size = UDim2.new(1, 0, 1, 0)
bg.Position = UDim2.new(0, 0, 0, 0)
bg.Image = "rbxthumb://type=Asset&id=137928809091955&w=420&h=420"
bg.BackgroundTransparency = 1
bg.ZIndex = 0

-- Ícone ao lado do nome
local icon = Instance.new("ImageLabel", panel)
icon.Size = UDim2.new(0, 40, 0, 40)
icon.Position = UDim2.new(0, 5, 0, 5)
icon.Image = "rbxthumb://type=Asset&id=130800893288109&w=420&h=420"
icon.BackgroundTransparency = 1
icon.ZIndex = 2

-- Nome do título
local title = Instance.new("TextLabel", panel)
title.Size = UDim2.new(1, -50, 0, 40)
title.Position = UDim2.new(0, 50, 0, 0)
title.Text = "Fetless"
title.TextColor3 = Color3.new(1, 1, 1)
title.TextStrokeTransparency = 0.8
title.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
title.TextScaled = true
title.Font = Enum.Font.GothamBold
title.BackgroundTransparency = 1
title.ZIndex = 2

-- Subtítulo
local subTitle = Instance.new("TextLabel", panel)
subTitle.Size = UDim2.new(1, 0, 0, 20)
subTitle.Position = UDim2.new(0, 0, 0, 40)
subTitle.Text = ".Hub SOCCER League"
subTitle.TextColor3 = Color3.fromRGB(0, 255, 0)
subTitle.TextStrokeTransparency = 0.8
subTitle.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
subTitle.TextScaled = true
subTitle.Font = Enum.Font.GothamBold
subTitle.BackgroundTransparency = 1
subTitle.ZIndex = 2

-- Botão de Fechar
local closeBtn = Instance.new("TextButton", panel)
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -35, 0, 5)
closeBtn.Text = "X"
closeBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
closeBtn.TextColor3 = Color3.new(1, 1, 1)
closeBtn.TextScaled = true
closeBtn.Font = Enum.Font.GothamBold
closeBtn.ZIndex = 2
Instance.new("UICorner", closeBtn)
styleButton(closeBtn)

-- Botão JuninhoReact
local juninhoBtn = Instance.new("TextButton", panel)
juninhoBtn.Size = UDim2.new(0, 270, 0, 40)
juninhoBtn.Position = UDim2.new(0, 15, 0, 80)
juninhoBtn.Text = "JuninhoReact"
juninhoBtn.BackgroundColor3 = Color3.fromRGB(255, 150, 0)
juninhoBtn.TextColor3 = Color3.new(1, 1, 1)
juninhoBtn.TextScaled = true
juninhoBtn.Font = Enum.Font.GothamBold
juninhoBtn.ZIndex = 2
Instance.new("UICorner", juninhoBtn)
styleButton(juninhoBtn)

-- Variável global usada no outro script
getgenv().JuninhoReact = false

juninhoBtn.MouseButton1Click:Connect(function()
	getgenv().JuninhoReact = not getgenv().JuninhoReact

	if getgenv().JuninhoReact then
		juninhoBtn.Text = "JuninhoReact (Ativado)"
		juninhoBtn.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
	else
		juninhoBtn.Text = "JuninhoReact"
		juninhoBtn.BackgroundColor3 = Color3.fromRGB(255, 150, 0)
	end
end)

-- Botão zz helper
local zzBtn = Instance.new("TextButton", panel)
zzBtn.Size = UDim2.new(0, 270, 0, 40)
zzBtn.Position = UDim2.new(0, 15, 0, 130)
zzBtn.Text = "zz helper"
zzBtn.BackgroundColor3 = Color3.fromRGB(255, 100, 255)
zzBtn.TextColor3 = Color3.new(1, 1, 1)
zzBtn.TextScaled = true
zzBtn.Font = Enum.Font.GothamBold
zzBtn.ZIndex = 2
Instance.new("UICorner", zzBtn)
styleButton(zzBtn)

getgenv().zzHelper = false

zzBtn.MouseButton1Click:Connect(function()
	getgenv().zzHelper = not getgenv().zzHelper

	if getgenv().zzHelper then
		zzBtn.Text = "zz helper (Ativado)"
		zzBtn.BackgroundColor3 = Color3.fromRGB(0, 200, 200)
	else
		zzBtn.Text = "zz helper"
		zzBtn.BackgroundColor3 = Color3.fromRGB(255, 100, 255)
	end
end)

-- Botão InfiniteDribble Helper
local infiniteBtn = Instance.new("TextButton", panel)
infiniteBtn.Size = UDim2.new(0, 270, 0, 40)
infiniteBtn.Position = UDim2.new(0, 15, 0, 180)
infiniteBtn.Text = "InfiniteDribble Helper"
infiniteBtn.BackgroundColor3 = Color3.fromRGB(100, 255, 100)
infiniteBtn.TextColor3 = Color3.new(1, 1, 1)
infiniteBtn.TextScaled = true
infiniteBtn.Font = Enum.Font.GothamBold
infiniteBtn.ZIndex = 2
Instance.new("UICorner", infiniteBtn)
styleButton(infiniteBtn)

getgenv().InfiniteDribbleHelper = false

infiniteBtn.MouseButton1Click:Connect(function()
	getgenv().InfiniteDribbleHelper = not getgenv().InfiniteDribbleHelper

	if getgenv().InfiniteDribbleHelper then
		infiniteBtn.Text = "InfiniteDribble Helper (Ativado)"
		infiniteBtn.BackgroundColor3 = Color3.fromRGB(0, 180, 0)
	else
		infiniteBtn.Text = "InfiniteDribble Helper"
		infiniteBtn.BackgroundColor3 = Color3.fromRGB(100, 255, 100)
	end
end)

-- Botão Shoot Helper
local shootBtn = Instance.new("TextButton", panel)
shootBtn.Size = UDim2.new(0, 270, 0, 40)
shootBtn.Position = UDim2.new(0, 15, 0, 230)
shootBtn.Text = "Shoot Helper"
shootBtn.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
shootBtn.TextColor3 = Color3.new(1, 1, 1)
shootBtn.TextScaled = true
shootBtn.Font = Enum.Font.GothamBold
shootBtn.ZIndex = 2
Instance.new("UICorner", shootBtn)
styleButton(shootBtn)

getgenv().ShootHelper = false

shootBtn.MouseButton1Click:Connect(function()
	getgenv().ShootHelper = not getgenv().ShootHelper

	if getgenv().ShootHelper then
		shootBtn.Text = "Shoot Helper (Ativado)"
		shootBtn.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
	else
		shootBtn.Text = "Shoot Helper"
		shootBtn.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
	end
end)

-- Abrir/Fechar GUI
openBtn.MouseButton1Click:Connect(function()
	if not panel.Visible then
		panel.BackgroundTransparency = 1
		panel.Visible = true
		TweenService:Create(panel, TweenInfo.new(0.3), {BackgroundTransparency = 0.2}):Play()
	else
		TweenService:Create(panel, TweenInfo.new(0.3), {BackgroundTransparency = 1}):Play()
		wait(0.3)
		panel.Visible = false
	end
end)

closeBtn.MouseButton1Click:Connect(function()
	Twlocal Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "FetlessGui"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local function addShadow(instance)
	local stroke = Instance.new("UIStroke")
	stroke.Color = Color3.fromRGB(0, 0, 0)
	stroke.Thickness = 1.2
	stroke.Transparency = 0.4
	stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
	stroke.Parent = instance
end

local function styleButton(button)
	button.AutoButtonColor = false
	addShadow(button)
	local stroke = Instance.new("UIStroke", button)
	stroke.Color = Color3.fromRGB(255, 255, 255)
	stroke.Thickness = 1
	stroke.Transparency = 0.6
	stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

	button.MouseEnter:Connect(function()
		TweenService:Create(button, TweenInfo.new(0.2), {BackgroundTransparency = 0.1}):Play()
	end)
	button.MouseLeave:Connect(function()
		TweenService:Create(button, TweenInfo.new(0.2), {BackgroundTransparency = 0}):Play()
	end)
end

-- Botão de Abrir
local openBtn = Instance.new("ImageButton", gui)
openBtn.Name = "OpenButton"
openBtn.Size = UDim2.new(0, 50, 0, 50)
openBtn.Position = UDim2.new(0, 20, 0.5, -25)
openBtn.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
openBtn.Image = "rbxthumb://type=Asset&id=130800893288109&w=420&h=420"
openBtn.Draggable = true
openBtn.Active = true
Instance.new("UICorner", openBtn)
addShadow(openBtn)

-- Painel principal
local panel = Instance.new("Frame", gui)
panel.Size = UDim2.new(0, 300, 0, 390) -- Aumentei altura para caber mais botões
panel.Position = UDim2.new(0.5, -150, 0.5, -195)
panel.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
panel.BackgroundTransparency = 0.2
panel.Visible = false
panel.ZIndex = 1
Instance.new("UICorner", panel)
addShadow(panel)

-- Fundo da GUI
local bg = Instance.new("ImageLabel", panel)
bg.Size = UDim2.new(1, 0, 1, 0)
bg.Position = UDim2.new(0, 0, 0, 0)
bg.Image = "rbxthumb://type=Asset&id=137928809091955&w=420&h=420"
bg.BackgroundTransparency = 1
bg.ZIndex = 0

-- Ícone ao lado do nome
local icon = Instance.new("ImageLabel", panel)
icon.Size = UDim2.new(0, 40, 0, 40)
icon.Position = UDim2.new(0, 5, 0, 5)
icon.Image = "rbxthumb://type=Asset&id=130800893288109&w=420&h=420"
icon.BackgroundTransparency = 1
icon.ZIndex = 2

-- Nome do título
local title = Instance.new("TextLabel", panel)
title.Size = UDim2.new(1, -50, 0, 40)
title.Position = UDim2.new(0, 50, 0, 0)
title.Text = "Fetless"
title.TextColor3 = Color3.new(1, 1, 1)
title.TextStrokeTransparency = 0.8
title.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
title.TextScaled = true
title.Font = Enum.Font.GothamBold
title.BackgroundTransparency = 1
title.ZIndex = 2

-- Subtítulo
local subTitle = Instance.new("TextLabel", panel)
subTitle.Size = UDim2.new(1, 0, 0, 20)
subTitle.Position = UDim2.new(0, 0, 0, 40)
subTitle.Text = ".Hub SOCCER League"
subTitle.TextColor3 = Color3.fromRGB(0, 255, 0)
subTitle.TextStrokeTransparency = 0.8
subTitle.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
subTitle.TextScaled = true
subTitle.Font = Enum.Font.GothamBold
subTitle.BackgroundTransparency = 1
subTitle.ZIndex = 2

-- Botão de Fechar
local closeBtn = Instance.new("TextButton", panel)
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -35, 0, 5)
closeBtn.Text = "X"
closeBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
closeBtn.TextColor3 = Color3.new(1, 1, 1)
closeBtn.TextScaled = true
closeBtn.Font = Enum.Font.GothamBold
closeBtn.ZIndex = 2
Instance.new("UICorner", closeBtn)
styleButton(closeBtn)

-- Botão JuninhoReact
local juninhoBtn = Instance.new("TextButton", panel)
juninhoBtn.Size = UDim2.new(0, 270, 0, 40)
juninhoBtn.Position = UDim2.new(0, 15, 0, 80)
juninhoBtn.Text = "JuninhoReact"
juninhoBtn.BackgroundColor3 = Color3.fromRGB(255, 150, 0)
juninhoBtn.TextColor3 = Color3.new(1, 1, 1)
juninhoBtn.TextScaled = true
juninhoBtn.Font = Enum.Font.GothamBold
juninhoBtn.ZIndex = 2
Instance.new("UICorner", juninhoBtn)
styleButton(juninhoBtn)

-- Variável global usada no outro script
getgenv().JuninhoReact = false

juninhoBtn.MouseButton1Click:Connect(function()
	getgenv().JuninhoReact = not getgenv().JuninhoReact

	if getgenv().JuninhoReact then
		juninhoBtn.Text = "JuninhoReact (Ativado)"
		juninhoBtn.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
	else
		juninhoBtn.Text = "JuninhoReact"
		juninhoBtn.BackgroundColor3 = Color3.fromRGB(255, 150, 0)
	end
end)

-- Botão zz helper
local zzBtn = Instance.new("TextButton", panel)
zzBtn.Size = UDim2.new(0, 270, 0, 40)
zzBtn.Position = UDim2.new(0, 15, 0, 130)
zzBtn.Text = "zz helper"
zzBtn.BackgroundColor3 = Color3.fromRGB(255, 100, 255)
zzBtn.TextColor3 = Color3.new(1, 1, 1)
zzBtn.TextScaled = true
zzBtn.Font = Enum.Font.GothamBold
zzBtn.ZIndex = 2
Instance.new("UICorner", zzBtn)
styleButton(zzBtn)

getgenv().zzHelper = false

zzBtn.MouseButton1Click:Connect(function()
	getgenv().zzHelper = not getgenv().zzHelper

	if getgenv().zzHelper then
		zzBtn.Text = "zz helper (Ativado)"
		zzBtn.BackgroundColor3 = Color3.fromRGB(0, 200, 200)
	else
		zzBtn.Text = "zz helper"
		zzBtn.BackgroundColor3 = Color3.fromRGB(255, 100, 255)
	end
end)

-- Botão InfiniteDribble Helper
local infiniteBtn = Instance.new("TextButton", panel)
infiniteBtn.Size = UDim2.new(0, 270, 0, 40)
infiniteBtn.Position = UDim2.new(0, 15, 0, 180)
infiniteBtn.Text = "InfiniteDribble Helper"
infiniteBtn.BackgroundColor3 = Color3.fromRGB(100, 255, 100)
infiniteBtn.TextColor3 = Color3.new(1, 1, 1)
infiniteBtn.TextScaled = true
infiniteBtn.Font = Enum.Font.GothamBold
infiniteBtn.ZIndex = 2
Instance.new("UICorner", infiniteBtn)
styleButton(infiniteBtn)

getgenv().InfiniteDribbleHelper = false

infiniteBtn.MouseButton1Click:Connect(function()
	getgenv().InfiniteDribbleHelper = not getgenv().InfiniteDribbleHelper

	if getgenv().InfiniteDribbleHelper then
		infiniteBtn.Text = "InfiniteDribble Helper (Ativado)"
		infiniteBtn.BackgroundColor3 = Color3.fromRGB(0, 180, 0)
	else
		infiniteBtn.Text = "InfiniteDribble Helper"
		infiniteBtn.BackgroundColor3 = Color3.fromRGB(100, 255, 100)
	end
end)

-- Botão Shoot Helper
local shootBtn = Instance.new("TextButton", panel)
shootBtn.Size = UDim2.new(0, 270, 0, 40)
shootBtn.Position = UDim2.new(0, 15, 0, 230)
shootBtn.Text = "Shoot Helper"
shootBtn.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
shootBtn.TextColor3 = Color3.new(1, 1, 1)
shootBtn.TextScaled = true
shootBtn.Font = Enum.Font.GothamBold
shootBtn.ZIndex = 2
Instance.new("UICorner", shootBtn)
styleButton(shootBtn)

getgenv().ShootHelper = false

shootBtn.MouseButton1Click:Connect(function()
	getgenv().ShootHelper = not getgenv().ShootHelper

	if getgenv().ShootHelper then
		shootBtn.Text = "Shoot Helper (Ativado)"
		shootBtn.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
	else
		shootBtn.Text = "Shoot Helper"
		shootBtn.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
	end
end)

-- Abrir/Fechar GUI
openBtn.MouseButton1Click:Connect(function()
	if not panel.Visible then
		panel.BackgroundTransparency = 1
		panel.Visible = true
		TweenService:Create(panel, TweenInfo.new(0.3), {BackgroundTransparency = 0.2}):Play()
	else
		TweenService:Create(panel, TweenInfo.new(0.3), {BackgroundTransparency = 1}):Play()
		wait(0.3)
		panel.Visible = false
	end
end)

closeBtn.MouseButton1Click:Connect(function()
	TweenService:Create(panel, TweenInfo.new(0.3), {BackgroundTransparency = 1}):Play()
	wait(0.3)
	panel.Visible = false
end)
eenService:Create(panel, TweenInfo.new(0.3), {BackgroundTransparency = 1}):Play()
	wait(0.3)
	panel.Visible = false
end)
