local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local FlyButton = Instance.new("TextButton")
local NightButton = Instance.new("TextButton")

-- Configurando a GUI
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 200, 0, 150)
Frame.Position = UDim2.new(0.1, 0, 0.1, 0)
Frame.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)

-- Configurando Botão de Voar
FlyButton.Parent = Frame
FlyButton.Size = UDim2.new(0, 180, 0, 50)
FlyButton.Position = UDim2.new(0, 10, 0, 10)
FlyButton.Text = "Voar"
FlyButton.BackgroundColor3 = Color3.new(0, 1, 0)

-- Configurando Botão de Noite
NightButton.Parent = Frame
NightButton.Size = UDim2.new(0, 180, 0, 50)
NightButton.Position = UDim2.new(0, 10, 0, 70)
NightButton.Text = "Modo Noturno"
NightButton.BackgroundColor3 = Color3.new(0, 0, 1)

-- Função para Voar
local function toggleFly()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
    
    if humanoidRootPart then
        humanoidRootPart.Velocity = Vector3.new(0, 50, 0) -- Faz o jogador subir
    end
end

FlyButton.MouseButton1Click:Connect(toggleFly)

-- Função para alternar para noite
local function setNight()
    game.Lighting.TimeOfDay = "00:00:00" -- Define o horário para meia-noite
end

NightButton.MouseButton1Click:Connect(setNight)
