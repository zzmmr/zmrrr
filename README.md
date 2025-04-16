local player = game.Players.LocalPlayer

function createKeyFrame()
	local screenGui = Instance.new("ScreenGui")
	screenGui.Name = "ScreenGui"
	screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	screenGui.Parent = game:GetService("CoreGui")

	local frame = Instance.new("Frame")
	frame.Name = "Frame"
	frame.AnchorPoint = Vector2.new(0.5, 0.5)
	frame.BackgroundColor3 = Color3.fromRGB(14, 29, 48)
	frame.BackgroundTransparency = 0.1
	frame.Position = UDim2.fromScale(0.499545, 0.5288)
	frame.Size = UDim2.fromScale(0.283997, 0.3536)

	local imageLabel = Instance.new("ImageLabel")
	imageLabel.Name = "ImageLabel"
	imageLabel.AnchorPoint = Vector2.new(0.5, 0.5)
	imageLabel.BackgroundTransparency = 1
	imageLabel.Image = "rbxassetid://118100076756008"
	imageLabel.Position = UDim2.fromScale(0.498713, 0.177452)
	imageLabel.Rotation = 45
	imageLabel.Size = UDim2.fromScale(0.163551, 0.275214)

	local uIAspectRatioConstraint = Instance.new("UIAspectRatioConstraint")
	uIAspectRatioConstraint.Name = "UIAspectRatioConstraint"
	uIAspectRatioConstraint.Parent = imageLabel

	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.CornerRadius = UDim.new(0.5, 0)
	uICorner.Parent = imageLabel

	imageLabel.Parent = frame

	local uICorner1 = Instance.new("UICorner")
	uICorner1.Name = "UICorner"
	uICorner1.CornerRadius = UDim.new(0.03, 0)
	uICorner1.Parent = frame

	local key = Instance.new("TextBox")
	key.Name = "Key"
	key.AnchorPoint = Vector2.new(0.5, 0.5)
	key.BackgroundColor3 = Color3.fromRGB(25, 52, 85)
	key.CursorPosition = -1
	key.FontFace = Font.new(
		"rbxasset://fonts/families/GothamSSm.json",
		Enum.FontWeight.SemiBold,
		Enum.FontStyle.Normal
	)
	key.PlaceholderColor3 = Color3.fromRGB(68, 156, 220)
	key.PlaceholderText = "Key"
	key.Position = UDim2.fromScale(0.5, 0.435604)
	key.Size = UDim2.fromScale(0.947569, 0.178543)
	key.Text = ""
	key.TextColor3 = Color3.new(1, 1, 1)
	key.TextScaled = true

	local uIPadding = Instance.new("UIPadding")
	uIPadding.Name = "UIPadding"
	uIPadding.PaddingBottom = UDim.new(0.25, 0)
	uIPadding.PaddingTop = UDim.new(0.25, 0)
	uIPadding.Parent = key

	local uICorner2 = Instance.new("UICorner")
	uICorner2.Name = "UICorner"
	uICorner2.CornerRadius = UDim.new(0.1, 0)
	uICorner2.Parent = key

	key.Parent = frame

	local submit = Instance.new("TextButton")
	submit.Name = "Submit"
	submit.AnchorPoint = Vector2.new(0.5, 0.5)
	submit.BackgroundColor3 = Color3.fromRGB(68, 156, 220)
	submit.FontFace = Font.new(
		"rbxassetid://11702779517",
		Enum.FontWeight.SemiBold,
		Enum.FontStyle.Normal
	)
	submit.Position = UDim2.fromScale(0.5, 0.872758)
	submit.Size = UDim2.fromScale(0.947569, 0.178543)
	submit.Text = "Submit"
	submit.TextColor3 = Color3.fromRGB(14, 29, 48)
	submit.TextScaled = true

	local uIPadding1 = Instance.new("UIPadding")
	uIPadding1.Name = "UIPadding"
	uIPadding1.PaddingBottom = UDim.new(0.25, 0)
	uIPadding1.PaddingTop = UDim.new(0.25, 0)
	uIPadding1.Parent = submit

	local uICorner3 = Instance.new("UICorner")
	uICorner3.Name = "UICorner"
	uICorner3.CornerRadius = UDim.new(0.1, 0)
	uICorner3.Parent = submit

	submit.Parent = frame

	local submit1 = Instance.new("TextButton")
	submit1.Name = "Submit"
	submit1.AnchorPoint = Vector2.new(0.5, 0.5)
	submit1.BackgroundColor3 = Color3.fromRGB(68, 156, 220)
	submit1.FontFace = Font.new(
		"rbxassetid://11702779517",
		Enum.FontWeight.SemiBold,
		Enum.FontStyle.Normal
	)
	submit1.Position = UDim2.fromScale(0.5, 0.646514)
	submit1.Size = UDim2.fromScale(0.947569, 0.178543)
	submit1.Text = "Copy Link"
	submit1.TextColor3 = Color3.fromRGB(14, 29, 48)
	submit1.TextScaled = true
	submit1.Activated:Connect(function()
		setclipboard("https://ads.luarmor.net/get_key?for=key-xizANDvIwBwq")
		submit1.Text = "Copied"
		wait(1)
		submit1.Text = "Copy Link"
	end)

	local uIPadding2 = Instance.new("UIPadding")
	uIPadding2.Name = "UIPadding"
	uIPadding2.PaddingBottom = UDim.new(0.25, 0)
	uIPadding2.PaddingTop = UDim.new(0.25, 0)
	uIPadding2.Parent = submit1

	local uICorner4 = Instance.new("UICorner")
	uICorner4.Name = "UICorner"
	uICorner4.CornerRadius = UDim.new(0.1, 0)
	uICorner4.Parent = submit1

	submit1.Parent = frame

	frame.Parent = screenGui
	return screenGui
end
function checkKey(key)
	local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
	api.script_id = "edf760b8704c87a87799653c0f80cb6b"

	local status = api.check_key(key); 

	if (status.code == "KEY_VALID") then
		writefile("overflowkey.txt", key)
		api.load_script();
		return true

	elseif (status.code == "KEY_HWID_LOCKED") then
		player:Kick("Key linked to a different HWID. Please reset it using our bot")
		return

	elseif (status.code == "KEY_INCORRECT") then
		print("key is wrong or deleted")
		return    
	else
		print(status.message .. " Code: " .. status.code)
	end
end
if not isfile("overflowkey.txt") or not checkKey(readfile("overflowkey.txt")) then
	local gui = createKeyFrame()
	gui.Frame.Submit.Activated:Connect(function()
		local c = checkKey(gui.Frame.Key.Text)
		if not c then
			gui.Frame.Submit.Text = "Invalid"
			wait(1)
			gui.Frame.Submit.Text = "Submit"
		else
			gui:Destroy()
		end
	end)
end
