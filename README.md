if game.PlaceId == 2753915549 or game.PlaceId == 4442272183 or game.PlaceId == 7449423635 then
    game.StarterGui:SetCore("SendNotification", {
      Icon = "rbxassetid://9152775759";
          Title = "Biel Hub", 
      Text = "Welcome BIEL!"
  })
  
  wait(1)
  
  game.StarterGui:SetCore("SendNotification", {
      Icon = "rbxassetid://9152775759";
      Title = "BIEL    ", 
      Text = "Loading Ui..."
  })
  
  wait(10)
  
   
      game:GetService("Players").LocalPlayer.Idled:connect(function()
          game:GetService("VirtualUser"):Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
          wait(1)
          game:GetService("VirtualUser"):Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
      end)
  
      _G.Color = Color3.fromRGB(255,0,0)
      if not game:IsLoaded() then repeat game.Loaded:Wait() until game:IsLoaded() end
      
      repeat wait() until game:GetService("Players")
      
      if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then repeat wait() until game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart") end
          
      wait(1)
      
      do
          local ui = game.CoreGui:FindFirstChild("BIELGUI")
          if ui then
              ui:Destroy()
          end
      end
      
      local UserInputService = game:GetService("UserInputService")
      local TweenService = game:GetService("TweenService")
      
      local function MakeDraggable(topbarobject, object)
          local Dragging = nil
          local DragInput = nil
          local DragStart = nil
          local StartPosition = nil
      
          local function Update(input)
              local Delta = input.Position - DragStart
              local pos =
                  UDim2.new(
                      StartPosition.X.Scale,
                      StartPosition.X.Offset + Delta.X,
                      StartPosition.Y.Scale,
                      StartPosition.Y.Offset + Delta.Y
                  )
              local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})
              Tween:Play()
          end
      
          topbarobject.InputBegan:Connect(
              function(input)
                  if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
                      Dragging = true
                      DragStart = input.Position
                      StartPosition = object.Position
      
                      input.Changed:Connect(
                          function()
                              if input.UserInputState == Enum.UserInputState.End then
                                  Dragging = false
                              end
                          end
                      )
                  end
              end
          )
      
          topbarobject.InputChanged:Connect(
              function(input)
                  if
                      input.UserInputType == Enum.UserInputType.MouseMovement or
                      input.UserInputType == Enum.UserInputType.Touch
                  then
                      DragInput = input
                  end
              end
          )
      
          UserInputService.InputChanged:Connect(
              function(input)
                  if input == DragInput and Dragging then
                      Update(input)
                  end
              end
          )
      end
      
      local library = {}
      
      function library:AddWindow(text,keybind)
          local bind = keybind or Enum.KeyCode.RightControl
          local ff = false
          local currenttab = ""
      
          local DoctorShiba = Instance.new("ScreenGui")
          DoctorShiba.Name = "BIELGUI"
          DoctorShiba.Parent = game.CoreGui
          DoctorShiba.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
      
          local Main = Instance.new("Frame")
          Main.Name = "Main"
          Main.Parent = DoctorShiba
          Main.AnchorPoint = Vector2.new(0.5, 0.5)
          Main.BackgroundColor3 = Color3.fromRGB(30, 28, 39)
          Main.BackgroundTransparency = 0.100
          Main.BorderSizePixel = 0
          Main.ClipsDescendants = true
          Main.Position = UDim2.new(0.499526083, 0, 0.499241292, 0)
          Main.Size = UDim2.new(0, 600, 0, 350)
      
          local Top = Instance.new("Frame")
          Top.Name = "Top"
          Top.Parent = Main
          Top.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
          Top.BackgroundTransparency = 1.000
          Top.BorderSizePixel = 0
          Top.Size = UDim2.new(0, 600, 0, 20)
      
          local Page = Instance.new("Frame")
          Page.Name = "Page"
          Page.Parent = Main
          Page.BackgroundColor3 = Color3.fromRGB(25, 23, 35)
          Page.BackgroundTransparency = 0.100
          Page.BorderSizePixel = 0
          Page.Size = UDim2.new(0, 125, 0, 350)
      
          local NameHub = Instance.new("TextLabel")
          NameHub.Name = "NameHub"
          NameHub.Parent = Page
          NameHub.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
          NameHub.BackgroundTransparency = 1.000
          NameHub.Position = UDim2.new(0.113333493, 0, 0, 0)
          NameHub.Size = UDim2.new(0, 110, 0, 20)
          NameHub.Font = Enum.Font.GothamSemibold
          NameHub.Text = text
          NameHub.TextColor3 = Color3.fromRGB(225, 0, 0)
          NameHub.TextSize = 11.000
          NameHub.TextXAlignment = Enum.TextXAlignment.Left
      
          local User = Instance.new("Frame")
          User.Name = "User"
          User.Parent = Page
          User.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
          User.BackgroundTransparency = 1.000
          User.Position = UDim2.new(0, 0, 0.8, 30)
          User.Size = UDim2.new(0, 125, 0, 40)
      
          local UserText = Instance.new("TextLabel")
          UserText.Name = "UserText"
          UserText.Parent = User
          UserText.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
          UserText.BackgroundTransparency = 1.000
          UserText.Position = UDim2.new(0.354999989, 0, 0, 11)
          UserText.Size = UDim2.new(0, 80, 0, 20)
          UserText.Font = Enum.Font.Gotham
          UserText.Text = tostring(game.Players.LocalPlayer.Name) 
          spawn(function()
              while wait() do
                  pcall(function()
                      wait(0.1) 
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(255, 0, 0)}
                      ):Play() 
                      wait(.5)            
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(255, 155, 0)}
                      ):Play() 
                      wait(.5)            
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(255, 255, 0)}
                      ):Play() 
                      wait(.5)            
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(0, 255, 0)}
                      ):Play() 
                      wait(.5)            
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(0, 255, 255)}
                      ):Play() 
                      wait(.5)            
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(0, 155, 255)}
                      ):Play() 
                      wait(.5)            
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(255, 0, 255)}
                      ):Play() 
                      wait(.5)            
                      game:GetService('TweenService'):Create(
                          UserText,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                          {TextColor3 = Color3.fromRGB(255, 0, 155)}
                      ):Play() 
                      wait(.5)
                  end)
              end
          end)
          UserText.TextScaled = true
          UserText.TextSize = 11.000
          UserText.TextWrapped = true
          UserText.TextXAlignment = Enum.TextXAlignment.Left
      
          local UITextSizeConstraint = Instance.new("UITextSizeConstraint")
          UITextSizeConstraint.Parent = UserText
          UITextSizeConstraint.MaxTextSize = 11
      
          local UserImage = Instance.new("ImageLabel")
          UserImage.Name = "UserImage"
          UserImage.Parent = User
          UserImage.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
          UserImage.Position = UDim2.new(0, 10, 0, 9)
          UserImage.Size = UDim2.new(0, 25, 0, 25)
          UserImage.Image = "https://www.roblox.com/headshot-thumbnail/image?userId="..game.Players.LocalPlayer.UserId.."&width=420&height=420&format=png"
      
          local UserImageCorner = Instance.new("UICorner")
          UserImageCorner.CornerRadius = UDim.new(0, 100)
          UserImageCorner.Name = "UserImageCorner"
          UserImageCorner.Parent = UserImage
      
          local ScrollPage = Instance.new("ScrollingFrame")
          ScrollPage.Name = "ScrollPage"
          ScrollPage.Parent = Page
          ScrollPage.Active = true
          ScrollPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
          ScrollPage.BackgroundTransparency = 1.000
          ScrollPage.BorderSizePixel = 0
          ScrollPage.Position = UDim2.new(0, 0, 0.086, 0)
          ScrollPage.Size = UDim2.new(0, 125, 0, 290)
          ScrollPage.CanvasSize = UDim2.new(0, 0, 0, 0)
          ScrollPage.ScrollBarThickness = 0
          local PageList = Instance.new("UIListLayout")
          PageList.Name = "PageList"
          PageList.Parent = ScrollPage
          PageList.SortOrder = Enum.SortOrder.LayoutOrder
          PageList.Padding = UDim.new(0, 7)
      
          local PagePadding = Instance.new("UIPadding")
          PagePadding.Name = "PagePadding"
          PagePadding.Parent = ScrollPage
          PagePadding.PaddingTop = UDim.new(0, 5)
          PagePadding.PaddingLeft = UDim.new(0, 28)
      
          local TabFolder = Instance.new("Folder")
          TabFolder.Name = "TabFolder"
          TabFolder.Parent = Main
      
          MakeDraggable(Top,Main)
      
          local uihide = false
      
          UserInputService.InputBegan:Connect(function(input)
              if input.KeyCode == bind then
                  if uihide == false then
                      uihide = true
                      Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.2,true)
                  else
                      uihide = false
                      Main:TweenSize(UDim2.new(0, 600, 0, 350),"Out","Quad",0.2,true)
                  end
              end
          end)
      
          local uitab = {}
      
          function uitab:AddTab(text,image)
              local Image = image or 6023426915
      
              local PageButton = Instance.new("TextButton")
              PageButton.Name = "PageButton"
              PageButton.Parent = ScrollPage
              PageButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
              PageButton.BackgroundTransparency = 1.000
              PageButton.BorderSizePixel = 0
              PageButton.Position = UDim2.new(0.224000007, 0, 0.029787235, 0)
              PageButton.Size = UDim2.new(0, 97, 0, 20)
              PageButton.AutoButtonColor = false
              PageButton.Font = Enum.Font.GothamSemibold
              PageButton.Text = text
              PageButton.TextColor3 = Color3.fromRGB(225, 225, 225)
              PageButton.TextSize = 11.000
              PageButton.TextXAlignment = Enum.TextXAlignment.Left
              
              local PageImage = Instance.new("ImageLabel")
              PageImage.Name = "PageImage"
              PageImage.Parent = PageButton
              PageImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
              PageImage.BackgroundTransparency = 1.000
              PageImage.Position = UDim2.new(0, -20, 0, 3)
              PageImage.Size = UDim2.new(0, 15, 0, 15)
              PageImage.Image = "rbxassetid://"..tostring(Image)
      
              local MainTab = Instance.new("Frame")
              MainTab.Name = "MainTab"
              MainTab.Parent = TabFolder
              MainTab.BackgroundColor3 = Color3.fromRGB(30, 28, 39)
              MainTab.BorderSizePixel = 0
              MainTab.Position = UDim2.new(0.208333328, 0, 0, 0)
              MainTab.Size = UDim2.new(0, 475, 0, 350)
              MainTab.Visible = false
      
              local ScrollTab = Instance.new("ScrollingFrame")
              ScrollTab.Name = "ScrollTab"
              ScrollTab.Parent = MainTab
              ScrollTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
              ScrollTab.BackgroundTransparency = 1.000
              ScrollTab.BorderSizePixel = 0
              ScrollTab.Position = UDim2.new(0, 0, 0.057, 0)
              ScrollTab.Size = UDim2.new(0, 475, 0, 330)
              ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
              ScrollTab.ScrollBarThickness = 3
      
              local TabList = Instance.new("UIListLayout")
              TabList.Name = "TabList"
              TabList.Parent = ScrollTab
              TabList.SortOrder = Enum.SortOrder.LayoutOrder
              TabList.Padding = UDim.new(0, 5)
      
              local TabPadding = Instance.new("UIPadding")
              TabPadding.Name = "TabPadding"
              TabPadding.Parent = ScrollTab
              TabPadding.PaddingLeft = UDim.new(0, 10)
              TabPadding.PaddingTop = UDim.new(0, 10)
      
              PageButton.MouseButton1Click:Connect(function()
                  currenttab = MainTab.Name
                  for i,v in next, TabFolder:GetChildren() do 
                      if v.Name == "MainTab" then
                          v.Visible = false
                      end
                  end
                  MainTab.Visible = true
      
                  for i,v in next, ScrollPage:GetChildren() do 
                      if v:IsA("TextButton") then
                          TweenService:Create(
                              v,
                              TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                              {TextColor3 = Color3.fromRGB(225, 225, 225)}
                          ):Play()
                      end
                      TweenService:Create(
                          PageButton,
                          TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                          {TextColor3 = Color3.fromRGB(255,0,0)}
                      ):Play()
                  end
              end)
      
              if ff == false then
                  TweenService:Create(
                      PageButton,
                      TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                      {TextColor3 = Color3.fromRGB(255,0,0)}
                  ):Play()
                  for i,v in next, TabFolder:GetChildren() do 
                      if v.Name == "MainTab" then
                          v.Visible = false
                      end
                      MainTab.Visible = true
                  end
                  ff = true
              end
      
              game:GetService("RunService").Stepped:Connect(function()
                  pcall(function()
                      ScrollPage.CanvasSize = UDim2.new(0,0,0,PageList.AbsoluteContentSize.Y + 10)
                      ScrollTab.CanvasSize = UDim2.new(0,0,0,TabList.AbsoluteContentSize.Y + 30)
                  end)
              end)
              
              local main = {}
              
              function main:AddButton(text,callback)
                  local Button = Instance.new("TextButton")
      
                  Button.Name = "Button"
                  Button.Parent = ScrollTab
                  Button.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
                  Button.BackgroundTransparency = 0.1
                  Button.BorderSizePixel = 0
                  Button.Size = UDim2.new(0, 455, 0, 30)
                  Button.AutoButtonColor = false
                  Button.Font = Enum.Font.Gotham
                  Button.Text = text
                  Button.TextColor3 = Color3.fromRGB(225, 225, 225)
                  Button.TextSize = 11.000
                  Button.TextWrapped = true
                  
                  local ButtonCorner = Instance.new("UICorner")
                  ButtonCorner.Name = "ButtonCorner"
                  ButtonCorner.CornerRadius = UDim.new(0, 5)
                  ButtonCorner.Parent = Button
                  
                  Button.MouseEnter:Connect(function()
                      TweenService:Create(
                          Button,
                          TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                          {TextColor3 = Color3.fromRGB(255,0,0)}
                      ):Play()
                  end)
                  
                  Button.MouseLeave:Connect(function()
                      TweenService:Create(
                          Button,
                          TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                          {TextColor3 = Color3.fromRGB(225, 225, 225)}
                      ):Play()
                  end)
                  
                  Button.MouseButton1Click:Connect(function()
                      callback()
                      Button.TextSize = 0
                      TweenService:Create(
                          Button,
                          TweenInfo.new(0.4,Enum.EasingStyle.Back,Enum.EasingDirection.Out),
                          {TextSize = 11}
                      ):Play()
                  end)
              end
              
              function main:AddToggle(text,config,callback)
                  local ToggleImage = Instance.new("Frame")
                  
                  local Toggle = Instance.new("TextButton")
                  Toggle.Name = "Toggle"
                  Toggle.Parent = ScrollTab
                  Toggle.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
                  Toggle.BackgroundTransparency = 0.1
                  Toggle.BorderSizePixel = 0
                  Toggle.AutoButtonColor = false
                  Toggle.Size = UDim2.new(0, 455, 0, 30)
                  Toggle.Font = Enum.Font.SourceSans
                  Toggle.Text = ""
                  Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)
                  Toggle.TextSize = 14.000
                  
                  local ToggleCorner = Instance.new("UICorner")
                  ToggleCorner.Name = "ToggleCorner"
                  ToggleCorner.CornerRadius = UDim.new(0, 5)
                  ToggleCorner.Parent = Toggle
      
                  local ToggleLabel = Instance.new("TextLabel")
                  ToggleLabel.Name = "ToggleLabel"
                  ToggleLabel.Parent = Toggle
                  ToggleLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  ToggleLabel.BackgroundTransparency = 1.000
                  ToggleLabel.Position = UDim2.new(0, 13, 0, 0)
                  ToggleLabel.Size = UDim2.new(0, 410, 0, 30)
                  ToggleLabel.Font = Enum.Font.Gotham
                  ToggleLabel.Text = text
                  ToggleLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
                  ToggleLabel.TextSize = 11.000
                  ToggleLabel.TextXAlignment = Enum.TextXAlignment.Left
      
                  ToggleImage.Name = "ToggleImage"
                  ToggleImage.Parent = Toggle
                  ToggleImage.BackgroundColor3 = Color3.fromRGB(70, 68, 79)
                  ToggleImage.Position = UDim2.new(0, 425, 0, 5)
                  ToggleImage.BorderSizePixel = 0
                  ToggleImage.Size = UDim2.new(0, 20, 0, 20)
                  local ToggleImageCorner = Instance.new("UICorner")
                  ToggleImageCorner.Name = "ToggleImageCorner"
                  ToggleImageCorner.CornerRadius = UDim.new(0, 5)
                  ToggleImageCorner.Parent = ToggleImage
      
                  local ToggleImage2 = Instance.new("Frame")
                  ToggleImage2.Name = "ToggleImage2"
                  ToggleImage2.Parent = ToggleImage
                  ToggleImage2.AnchorPoint = Vector2.new(0.5, 0.5)
                  ToggleImage2.BackgroundColor3 = Color3.fromRGB(255,0,0)
                  ToggleImage2.Position = UDim2.new(0, 10, 0, 10)
                  ToggleImage2.Visible = false
      
                  local ToggleImage2Corner = Instance.new("UICorner")
                  ToggleImage2Corner.Name = "ToggleImageCorner"
                  ToggleImage2Corner.CornerRadius = UDim.new(0, 5)
                  ToggleImage2Corner.Parent = ToggleImage2
                  
                  Toggle.MouseEnter:Connect(function()
                      TweenService:Create(
                          ToggleLabel,
                          TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                          {TextColor3 = Color3.fromRGB(255,0,0)}
                      ):Play()
                  end)
      
                  Toggle.MouseLeave:Connect(function()
                      TweenService:Create(
                          ToggleLabel,
                          TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                          {TextColor3 = Color3.fromRGB(225, 225, 225)}
                      ):Play()
                  end)
                  if config == nil then config = false end
                  local toggled = config or false
                  Toggle.MouseButton1Click:Connect(function()
                      if toggled == false then
                          toggled = true
                          ToggleImage2.Visible = true
                          ToggleImage2:TweenSize(UDim2.new(0, 21, 0, 21),"In","Quad",0.1,true)
                      else
                          toggled = false
                          ToggleImage2:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.1,true)
                          wait(0.1)
                          ToggleImage2.Visible = false
                      end
                      callback(toggled)
                  end)
                  
                  if config == true then
                      ToggleImage2.Visible = true
                      ToggleImage2:TweenSize(UDim2.new(0, 21, 0, 21),"In","Quad",0.1,true)
                      toggled = true
                      callback(toggled)
                  end
              end
      
              function main:AddTextbox(text,holder,disappear,callback)
                  local Textboxx = Instance.new("Frame")
                  local TextboxxCorner = Instance.new("UICorner")
                  local TextboxTitle = Instance.new("TextLabel")
                  local Textbox = Instance.new("TextBox")
                  local TextboxCorner = Instance.new("UICorner")
      
                  Textboxx.Name = "Textboxx"
                  Textboxx.Parent = ScrollTab
                  Textboxx.BackgroundColor3 = Color3.fromRGB(50, 48, 59)
                  Textboxx.Size = UDim2.new(0, 455, 0, 30)
      
                  TextboxxCorner.CornerRadius = UDim.new(0, 5)
                  TextboxxCorner.Name = "TextboxxCorner"
                  TextboxxCorner.Parent = Textboxx
      
                  TextboxTitle.Name = "TextboxTitle"
                  TextboxTitle.Parent = Textboxx
                  TextboxTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  TextboxTitle.BackgroundTransparency = 1.000
                  TextboxTitle.Position = UDim2.new(0, 15, 0, 0)
                  TextboxTitle.Size = UDim2.new(0, 300, 0, 30)
                  TextboxTitle.Font = Enum.Font.Gotham
                  TextboxTitle.Text = text
                  TextboxTitle.TextColor3 = Color3.fromRGB(225, 225, 225)
                  TextboxTitle.TextSize = 11.000
                  TextboxTitle.TextXAlignment = Enum.TextXAlignment.Left
      
                  Textbox.Name = "Textbox"
                  Textbox.Parent = Textboxx
                  Textbox.BackgroundColor3 = Color3.fromRGB(30, 28, 39)
                  Textbox.Position = UDim2.new(0, 310, 0, 5)
                  Textbox.Size = UDim2.new(0, 140, 0, 20)
                  Textbox.Font = Enum.Font.Gotham
                  Textbox.Text = holder
                  Textbox.TextColor3 = Color3.fromRGB(225, 225, 225)
                  Textbox.TextSize = 11.000
      
                  Textbox.FocusLost:Connect(function()
                      if #Textbox.Text > 0 then
                          callback(Textbox.Text)
                      end
                      if disappear then
                          Textbox.Text = ""
                      else
                          Textbox.Text = holder
                      end
                  end)
      
                  TextboxCorner.Name = "TextboxCorner"
                  TextboxCorner.CornerRadius = UDim.new(0, 5)
                  TextboxCorner.Parent = Textbox
              end
      
              function main:AddDropdown(text,table,callback)
                  local Dropdown = Instance.new("Frame")
                  local UICorner = Instance.new("UICorner")
                  local DropButton = Instance.new("TextButton")
                  local Droptitle = Instance.new("TextLabel")
                  local DropScroll = Instance.new("ScrollingFrame")
                  local DropdownList = Instance.new("UIListLayout")
                  local DropdownPadding = Instance.new("UIPadding")
                  local DropImage = Instance.new("ImageLabel")
                  
                  Dropdown.Name = "Dropdown"
                  Dropdown.Parent = ScrollTab
                  Dropdown.Active = true
                  Dropdown.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
                  Dropdown.ClipsDescendants = true
                  Dropdown.Size = UDim2.new(0, 455, 0, 30)
                  
                  UICorner.CornerRadius = UDim.new(0, 5)
                  UICorner.Parent = Dropdown
                  
                  DropButton.Name = "DropButton"
                  DropButton.Parent = Dropdown
                  DropButton.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
                  DropButton.BackgroundTransparency = 1.000
                  DropButton.Size = UDim2.new(0, 455, 0, 30)
                  DropButton.Font = Enum.Font.SourceSans
                  DropButton.Text = ""
                  DropButton.TextColor3 = Color3.fromRGB(0, 0, 0)
                  DropButton.TextSize = 14.000
                  
                  Droptitle.Name = "Droptitle"
                  Droptitle.Parent = Dropdown
                  Droptitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  Droptitle.BackgroundTransparency = 1.000
                  Droptitle.Position = UDim2.new(0.0281690136, 0, 0, 0)
                  Droptitle.Size = UDim2.new(0, 410, 0, 30)
                  Droptitle.Font = Enum.Font.Gotham
                  Droptitle.Text = text.." : "
                  Droptitle.TextColor3 = Color3.fromRGB(225, 225, 225)
                  Droptitle.TextSize = 11.000
                  Droptitle.TextXAlignment = Enum.TextXAlignment.Left
      
                  DropImage.Name = "DropImage"
                  DropImage.Parent = Dropdown
                  DropImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  DropImage.BackgroundTransparency = 1.000
                  DropImage.Position = UDim2.new(0, 425, 0, 5)
                  DropImage.Rotation = 0
                  DropImage.Size = UDim2.new(0, 20, 0, 20)
                  DropImage.Image = "rbxassetid://5012539403"
                  
                  DropScroll.Name = "DropScroll"
                  DropScroll.Parent = Droptitle
                  DropScroll.Active = true
                  DropScroll.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  DropScroll.BackgroundTransparency = 1.000
                  DropScroll.BorderSizePixel = 0
                  DropScroll.Position = UDim2.new(-0.0317460336, 0, 1, 0)
                  DropScroll.Size = UDim2.new(0, 455, 0, 70)
                  DropScroll.CanvasSize = UDim2.new(0, 0, 0, 2)
                  DropScroll.ScrollBarThickness = 2
                  
                  DropdownList.Name = "DropdownList"
                  DropdownList.Parent = DropScroll
                  DropdownList.SortOrder = Enum.SortOrder.LayoutOrder
                  DropdownList.Padding = UDim.new(0, 5)
                  
                  DropdownPadding.Name = "DropdownPadding"
                  DropdownPadding.Parent = DropScroll
                  DropdownPadding.PaddingTop = UDim.new(0, 5)
      
                  local isdropping = false
      
                  for i,v in next,table do
                      local DropButton2 = Instance.new("TextButton")
      
                      DropButton2.Name = "DropButton2"
                      DropButton2.Parent = DropScroll
                      DropButton2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                      DropButton2.BackgroundTransparency = 1.000
                      DropButton2.Size = UDim2.new(0, 455, 0, 30)
                      DropButton2.AutoButtonColor = false
                      DropButton2.Font = Enum.Font.Gotham
                      DropButton2.TextColor3 = Color3.fromRGB(225, 225, 225)
                      DropButton2.TextSize = 11.000
                      DropButton2.Text = tostring(v)
      
                      DropButton2.MouseEnter:Connect(function()
                          TweenService:Create(
                              DropButton2,
                              TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {TextColor3 = Color3.fromRGB(255,0,0)}
                          ):Play()
                      end)
                      DropButton2.MouseLeave:Connect(function()
                          TweenService:Create(
                              DropButton2,
                              TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {TextColor3 = Color3.fromRGB(225, 225, 225)}
                          ):Play()
                      end)
      
                      DropButton2.MouseButton1Click:Connect(function()
                          TweenService:Create(
                              Dropdown,
                              TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {Size = UDim2.new(0, 455, 0, 30)}
                          ):Play()
                          TweenService:Create(
                              DropImage,
                              TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),
                              {Rotation = 0}
                          ):Play()
                          Droptitle.Text =  text.." : "..tostring(v)
                          callback(v)
                          isdropping = not isdropping
                          DropScroll.CanvasSize = UDim2.new(0,0,0,DropdownList.AbsoluteContentSize.Y + 10)
                      end)
                  end
      
                  DropButton.MouseButton1Click:Connect(function()
                      if isdropping == false then
                          isdropping = true
                          TweenService:Create(
                              Dropdown,
                              TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {Size = UDim2.new(0, 455, 0, 100)}
                          ):Play()
                          TweenService:Create(
                              DropImage,
                              TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {Rotation = -180}
                          ):Play()
                          DropScroll.CanvasSize = UDim2.new(0,0,0,DropdownList.AbsoluteContentSize.Y + 10)
                      else
                          isdropping = false
                          TweenService:Create(
                              Dropdown,
                              TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {Size = UDim2.new(0, 455, 0, 30)}
                          ):Play()
                          TweenService:Create(
                              DropImage,
                              TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {Rotation = 0}
                          ):Play()
                          DropScroll.CanvasSize = UDim2.new(0,0,0,DropdownList.AbsoluteContentSize.Y + 10)
                      end
                  end)
                  DropScroll.CanvasSize = UDim2.new(0,0,0,DropdownList.AbsoluteContentSize.Y + 10)
      
                  local drop = {}
      
                  function drop:Clear()
                      Droptitle.Text = tostring(text).." :"
                      TweenService:Create(
                          Dropdown,
                          TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                          {Size = UDim2.new(0, 455, 0, 30)} 
                      ):Play()
                      isdropping = false
                      for i, v in next, DropScroll:GetChildren() do
                          if v:IsA("TextButton") then
                              v:Destroy()
                          end
                      end
                  end
                  function drop:Add(t)
                      local DropButton2 = Instance.new("TextButton")
      
                      DropButton2.Name = "DropButton2"
                      DropButton2.Parent = DropScroll
                      DropButton2.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
                      DropButton2.BackgroundTransparency = 1.000
                      DropButton2.Size = UDim2.new(0, 455, 0, 30)
                      DropButton2.AutoButtonColor = false
                      DropButton2.Font = Enum.Font.Gotham
                      DropButton2.TextColor3 = Color3.fromRGB(0, 45, 255)
                      DropButton2.TextSize = 11.000
                      DropButton2.Text = tostring(t)
      
                      DropButton2.MouseButton1Click:Connect(function()
                          TweenService:Create(
                              Dropdown,
                              TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                              {Size = UDim2.new(0, 455, 0, 30)}
                          ):Play()
                          TweenService:Create(
                              DropImage,
                              TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),
                              {Rotation = 0}
                          ):Play()
                          Droptitle.Text =  text.." : "..tostring(t)
                          callback(t)
                          isdropping = not isdropping
                          DropScroll.CanvasSize = UDim2.new(0,0,0,DropdownList.AbsoluteContentSize.Y + 10)
                      end)
                  end
                  return drop
              end
      
              function main:AddSlider(text,min,max,set,callback)
                  set = (math.clamp(set,min,max))
                  if set > max then set = max end
      
                  local Slider = Instance.new("Frame")
                  local UICorner = Instance.new("UICorner")
                  local SliderTitle = Instance.new("TextLabel")
                  local SliderValue = Instance.new("TextLabel")
                  local SliderButton = Instance.new("TextButton")
                  local Bar1 = Instance.new("Frame")
                  local Bar = Instance.new("Frame")
                  local UICorner_2 = Instance.new("UICorner")
                  local CircleBar = Instance.new("Frame")
                  local UICorner_3 = Instance.new("UICorner")
                  local UICorner_4 = Instance.new("UICorner")
      
                  Slider.Name = "Slider"
                  Slider.Parent = ScrollTab
                  Slider.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
                  Slider.Size = UDim2.new(0, 455, 0, 40)
      
                  UICorner.CornerRadius = UDim.new(0, 5)
                  UICorner.Parent = Slider
      
                  SliderTitle.Name = "SliderTitle"
                  SliderTitle.Parent = Slider
                  SliderTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  SliderTitle.BackgroundTransparency = 1.000
                  SliderTitle.Position = UDim2.new(0.0283286124, 0, 0, 0)
                  SliderTitle.Size = UDim2.new(0, 290, 0, 20)
                  SliderTitle.Font = Enum.Font.Gotham
                  SliderTitle.Text = text
                  SliderTitle.TextColor3 = Color3.fromRGB(225, 225, 225)
                  SliderTitle.TextSize = 11.000
                  SliderTitle.TextXAlignment = Enum.TextXAlignment.Left
      
                  SliderValue.Name = "SliderValue"
                  SliderValue.Parent = Slider
                  SliderValue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  SliderValue.BackgroundTransparency = 1.000
                  SliderValue.Position = UDim2.new(0.887778878, 0, 0, 0)
                  SliderValue.Size = UDim2.new(0, 40, 0, 20)
                  SliderValue.Font = Enum.Font.Gotham
                  SliderValue.Text =  tostring(set and math.floor( (set / max) * (max - min) + min) or 0)
                  SliderValue.TextColor3 = Color3.fromRGB(225, 225, 225)
                  SliderValue.TextSize = 11.000
      
                  SliderButton.Name = "SliderButton"
                  SliderButton.Parent = Slider
                  SliderButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  SliderButton.BackgroundTransparency = 1.000
                  SliderButton.Position = UDim2.new(0, 10, 0, 25)
                  SliderButton.Size = UDim2.new(0, 435, 0, 5)
                  SliderButton.AutoButtonColor = false
                  SliderButton.Font = Enum.Font.SourceSans
                  SliderButton.Text = ""
                  SliderButton.TextColor3 = Color3.fromRGB(0, 0, 0)
                  SliderButton.TextSize = 14.000
      
                  Bar1.Name = "Bar1"
                  Bar1.Parent = SliderButton
                  Bar1.BackgroundColor3 = Color3.fromRGB(30, 28, 39)
                  Bar1.Size = UDim2.new(0, 435, 0, 5)
      
                  Bar.Name = "Bar"
                   Bar.Parent = Bar1
                  Bar.BackgroundColor3 = Color3.fromRGB(255,0,0)
                  Bar.Size = UDim2.new(set/max, 0, 0, 5)
      
                  UICorner_2.CornerRadius = UDim.new(0, 100)
                  UICorner_2.Parent = Bar
      
                  CircleBar.Name = "CircleBar"
                  CircleBar.Parent = Bar
                  CircleBar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  CircleBar.Position = UDim2.new(1, -2, 0, -2)
                  CircleBar.AnchorPoint = Vector2.new(0, 0.1)
                  CircleBar.Size = UDim2.new(0, 10, 0, 10)
      
                  UICorner_3.CornerRadius = UDim.new(0, 100)
                  UICorner_3.Parent = CircleBar
      
                  UICorner_4.CornerRadius = UDim.new(0, 100)
                  UICorner_4.Parent = Bar1
                  
                  local mouse = game.Players.LocalPlayer:GetMouse()
                  local uis = game:GetService("UserInputService")
      
                  if Value == nil then
                      Value = set
                      pcall(function()
                          callback(Value)
                      end)
                  end
                  
                  SliderButton.MouseButton1Down:Connect(function()
                      Value = math.floor((((tonumber(max) - tonumber(min)) / 435) * Bar.AbsoluteSize.X) + tonumber(min)) or 0
                      pcall(function()
                          callback(Value)
                      end)
                      Bar.Size = UDim2.new(0, math.clamp(mouse.X - Bar.AbsolutePosition.X, 0, 435), 0, 5)
                      CircleBar.Position = UDim2.new(0, math.clamp(mouse.X - Bar.AbsolutePosition.X - 2, 0, 425), 0, -2)
                      moveconnection = mouse.Move:Connect(function()
                          SliderValue.Text = Value
                          Value = math.floor((((tonumber(max) - tonumber(min)) / 435) * Bar.AbsoluteSize.X) + tonumber(min))
                          pcall(function()
                              callback(Value)
                          end)
                          Bar.Size = UDim2.new(0, math.clamp(mouse.X - Bar.AbsolutePosition.X, 0, 435), 0, 5)
                          CircleBar.Position = UDim2.new(0, math.clamp(mouse.X - Bar.AbsolutePosition.X - 2, 0, 425), 0, -2)
                      end)
                      releaseconnection = uis.InputEnded:Connect(function(Mouse)
                          if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                              Value = math.floor((((tonumber(max) - tonumber(min)) / 435) * Bar.AbsoluteSize.X) + tonumber(min))
                              pcall(function()
                                  callback(Value)
                              end)
                              Bar.Size = UDim2.new(0, math.clamp(mouse.X - Bar.AbsolutePosition.X, 0, 435), 0, 5)
                              CircleBar.Position = UDim2.new(0, math.clamp(mouse.X - Bar.AbsolutePosition.X - 2, 0, 425), 0, -2)
                              moveconnection:Disconnect()
                              releaseconnection:Disconnect()
                          end
                      end)
                  end)
                  releaseconnection = uis.InputEnded:Connect(function(Mouse)
                      if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                          Value = math.floor((((tonumber(max) - tonumber(min)) / 435) * Bar.AbsoluteSize.X) + tonumber(min))
                          SliderValue.Text = Value
                      end
                  end)
              end
              function main:AddSeperator(text)
                  local Seperator = Instance.new("Frame")
                  local Sep1 = Instance.new("Frame")
                  local SepLabel = Instance.new("TextLabel")
                  local Sep2 = Instance.new("Frame")
      
                  Seperator.Name = "Seperator"
                  Seperator.Parent = ScrollTab
                  Seperator.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  Seperator.BackgroundTransparency = 1.000
                  Seperator.ClipsDescendants = true
                  Seperator.Size = UDim2.new(0, 455, 0, 20)
      
                  Sep1.Name = "Sep1"
                  Sep1.Parent = Seperator
                  Sep1.BackgroundColor3 = Color3.fromRGB(255,0,0)
                  Sep1.BorderSizePixel = 0
                  Sep1.Position = UDim2.new(0, 0, 0, 10)
                  Sep1.Size = UDim2.new(0, 150, 0, 1)
      
                  SepLabel.Name = "SepLabel"
                  SepLabel.Parent = Seperator
                  SepLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  SepLabel.BackgroundTransparency = 1.000
                  SepLabel.Position = UDim2.new(0, 95, 0, 0)
                  SepLabel.Size = UDim2.new(0, 255, 0, 20)
                  SepLabel.Font = Enum.Font.Gotham
                  SepLabel.Text = text
                  SepLabel.TextColor3 = Color3.fromRGB(225,225,225)
                  SepLabel.TextSize = 11.000
      
                  Sep2.Name = "Sep2"
                  Sep2.Parent = Seperator
                  Sep2.BackgroundColor3 = Color3.fromRGB(255,0,0)
                  Sep2.BorderSizePixel = 0
                  Sep2.Position = UDim2.new(0, 305, 0, 10)
                  Sep2.Size = UDim2.new(0, 150, 0, 1)
              end
              function main:AddLine()
                  local Line = Instance.new("Frame")
                  local Linee = Instance.new("Frame")
      
                  Line.Name = "Line"
                  Line.Parent = ScrollTab
                  Line.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  Line.BackgroundTransparency = 1.000
                  Line.ClipsDescendants = true
                  Line.Size = UDim2.new(0, 455, 0, 20)
      
                  Linee.Name = "Linee"
                  Linee.Parent = Line
                  Linee.BackgroundColor3 = Color3.fromRGB(255,0,0)
                  Linee.BorderSizePixel = 0
                  Linee.Position = UDim2.new(0, 0, 0, 10)
                  Linee.Size = UDim2.new(0, 455, 0, 1)
              end
              function main:AddLabel(text)
                  local Label = Instance.new("TextLabel")
                  local PaddingLabel = Instance.new("UIPadding")
                  local labell = {}
          
                  Label.Name = "Label"
                  Label.Parent = ScrollTab
                  Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                  Label.BackgroundTransparency = 1.000
                  Label.Size = UDim2.new(0, 455, 0, 20)
                  Label.Font = Enum.Font.Gotham
                  Label.TextColor3 = Color3.fromRGB(225, 225, 225)
                  Label.TextSize = 11.000
                  Label.Text = text
                  Label.TextXAlignment = Enum.TextXAlignment.Left
      
                  PaddingLabel.PaddingLeft = UDim.new(0,10)
                  PaddingLabel.Parent = Label
                  PaddingLabel.Name = "PaddingLabel"
          
                  function labell:Set(newtext)
                      Label.Text = newtext
                  end
      
                  return labell
              end
              
              return main
          end
          return uitab
      end
      
      local ScreenGui = Instance.new("ScreenGui")
      local Toggle = Instance.new("TextButton")
      
      ScreenGui.Name = "ScreenGui"
      ScreenGui.Parent = game.CoreGui
      
      Toggle.Name = "Toggle"
      Toggle.Parent = ScreenGui
      Toggle.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
      Toggle.Position = UDim2.new(0.11, 0, 0.2, 0)
      Toggle.Size = UDim2.new(0, 50, 0, 50)
      Toggle.Font = Enum.Font.Code
      Toggle.Text = "Sx"
      Toggle.TextColor3 = Color3.fromRGB(0, 48, 255)
      Toggle.TextScaled = true
      Toggle.MouseButton1Down:connect(function()
          game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
          game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
      end)
      
      if game.PlaceId == 4520749081 then
         First_Sea = true
      elseif game.PlaceId == 6381829480 then
         Second_Sea = true
      elseif game.PlaceId == 5931540094 then
         Dungeon_Sea = true
      end
      function CheckQuest()
          QUEST = {}
          LVLREAL = {}
          local MyLevel = game.Players.LocalPlayer.PlayerStats.lvl.Value
          for i,v in pairs(game:GetService("Workspace").AntiTPNPC:GetChildren()) do 
              if string.find(v.Name,"QuestLvl") then
                  table.insert(QUEST,v.Name)
              end
          end
          for i,v in pairs(game:GetService("ReplicatedStorage").MAP:GetChildren()) do 
              if string.find(v.Name,"QuestLvl") then
                  table.insert(QUEST,v.Name)
              end
          end
          for i,v in pairs(QUEST) do
              values = v:split("QuestLvl")
              LVL = values[2]
              if MyLevel >= tonumber(LVL) then
                  table.insert(LVLREAL,LVL)
              end
          end
          LevelQuest = math.max(unpack(LVLREAL))
      end
      
      function fly()
          local mouse=game.Players.LocalPlayer:GetMouse''
          localplayer=game.Players.LocalPlayer
          game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart")
          local torso = game.Players.LocalPlayer.Character.HumanoidRootPart
          local speedSET=25
          local keys={a=false,d=false,w=false,s=false}
          local e1
          local e2
          local function start()
              local pos = Instance.new("BodyPosition",torso)
              local gyro = Instance.new("BodyGyro",torso)
              pos.Name="EPIXPOS"
              pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
              pos.position = torso.Position
              gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
              gyro.CFrame = torso.CFrame
              repeat
                      wait()
                      localplayer.Character.Humanoid.PlatformStand=true
                      local new=gyro.CFrame - gyro.CFrame.p + pos.position
                      if not keys.w and not keys.s and not keys.a and not keys.d then
                      speed=1
                      end
                      if keys.w then
                      new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                      speed=speed+speedSET
                      end
                      if keys.s then
                      new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                      speed=speed+speedSET
                      end
                      if keys.d then
                      new = new * CFrame.new(speed,0,0)
                      speed=speed+speedSET
                      end
                      if keys.a then
                      new = new * CFrame.new(-speed,0,0)
                      speed=speed+speedSET
                      end
                      if speed>speedSET then
                      speed=speedSET
                      end
                      pos.position=new.p
                      if keys.w then
                      gyro.CFrame = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(-math.rad(speed*15),0,0)
                      elseif keys.s then
                      gyro.CFrame = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(math.rad(speed*15),0,0)
                      else
                      gyro.CFrame = workspace.CurrentCamera.CoordinateFrame
                      end
              until not Fly
              if gyro then 
                      gyro:Destroy() 
              end
              if pos then 
                      pos:Destroy() 
              end
              flying=false
              localplayer.Character.Humanoid.PlatformStand=false
              speed=0
          end
          e1=mouse.KeyDown:connect(function(key)
              if not torso or not torso.Parent then 
                      flying=false e1:disconnect() e2:disconnect() return 
              end
              if key=="w" then
                  keys.w=true
              elseif key=="s" then
                  keys.s=true
              elseif key=="a" then
                  keys.a=true
              elseif key=="d" then
                  keys.d=true
              end
          end)
          e2=mouse.KeyUp:connect(function(key)
              if key=="w" then
                  keys.w=false
              elseif key=="s" then
                  keys.s=false
              elseif key=="a" then
                  keys.a=false
              elseif key=="d" then
                  keys.d=false
              end
          end)
          start()
      end
      
      function isnil(thing)
          return (thing == nil)
      end
      local function round(n)
          return math.floor(tonumber(n) + 0.5)
      end
      Number = math.random(1, 1000000)
      function UpdateEspPlayer()
          if ESPPlayer then
              pcall(function()
                  for i,v in pairs(game.Players:GetPlayers()) do
                      if not isnil(v.Character) then
                          if not v.Character.Head:FindFirstChild('NameEsp'..v.Name) then
                              local BillboardGui = Instance.new("BillboardGui")
                              local ESP = Instance.new("TextLabel")
                              local HealthESP = Instance.new("TextLabel")
                              BillboardGui.Parent = v.Character.Head
                              BillboardGui.Name = 'NameEsp'..v.Name
                              BillboardGui.ExtentsOffset = Vector3.new(0, 1, 0)
                              BillboardGui.Size = UDim2.new(1,200,1,30)
                              BillboardGui.Adornee = v.Character.Head
                              BillboardGui.AlwaysOnTop = true
                              ESP.Name = "ESP"
                              ESP.Parent = BillboardGui
                              ESP.TextTransparency = 0
                              ESP.BackgroundTransparency = 1
                              ESP.Size = UDim2.new(0, 200, 0, 30)
                              ESP.Position = UDim2.new(0,25,0,0)
                              ESP.Font = Enum.Font.Gotham
                              ESP.Text = (v.Name ..' '.."[ "..round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M'.." ]")
                              ESP.TextColor3 = Color3.new(0, 255, 255)
                              ESP.TextSize = 14
                              ESP.TextStrokeTransparency = 0.500
                              ESP.TextWrapped = true
                              HealthESP.Name = "HealthESP"
                              HealthESP.Parent = ESP
                              HealthESP.TextTransparency = 0
                              HealthESP.BackgroundTransparency = 1
                              HealthESP.Position = ESP.Position + UDim2.new(0, -25, 0, 15)
                              HealthESP.Size = UDim2.new(0, 200, 0, 30)
                              HealthESP.Font = Enum.Font.Gotham
                              HealthESP.TextColor3 = Color3.fromRGB(80, 255, 245)
                              HealthESP.TextSize = 14
                              HealthESP.TextStrokeTransparency = 0.500
                              HealthESP.TextWrapped = true
                              HealthESP.Text = "Health "..math.floor(v.Character.Humanoid.Health).."/"..math.floor(v.Character.Humanoid.MaxHealth)
                          else
                              v.Character.Head['NameEsp'..v.Name].ESP.Text = (v.Name ..' '..round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
                              v.Character.Head['NameEsp'..v.Name].ESP.HealthESP.Text = "Health "..math.floor(v.Character.Humanoid.Health).."/"..math.floor(v.Character.Humanoid.MaxHealth)
                              v.Character.Head:FindFirstChild('NameEsp'..v.Name).ESP.TextTransparency = 0
                              v.Character.Head:FindFirstChild('NameEsp'..v.Name).ESP.HealthESP.TextTransparency = 0
                          end
                      end
                  end
              end)
          else
              for i,v in pairs(game.Players:GetPlayers()) do
                  if v.Character.Head:FindFirstChild('NameEsp'..v.Name) then
                      pcall(function()
                          v.Character.Head:FindFirstChild('NameEsp'..v.Name):Destroy()
                      end)
                  end
              end
          end     
      end
      
      function UpdateBfEsp() 
          for i,v in pairs(game.Workspace:GetChildren()) do
              pcall(function()
                  if DevilFruitESP then
                      if string.find(v.Name, "Fruit") then   
                          if not v.Handle:FindFirstChild('NameEsp'..Number) then
                              local bill = Instance.new('BillboardGui',v.Handle)
                              bill.Name = 'NameEsp'..Number
                              bill.ExtentsOffset = Vector3.new(0, 1, 0)
                              bill.Size = UDim2.new(1,200,1,30)
                              bill.Adornee = v.Handle
                              bill.AlwaysOnTop = true
                              local name = Instance.new('TextLabel',bill)
                              name.Font = "GothamBold"
                              name.FontSize = "Size14"
                              name.TextWrapped = true
                              name.Size = UDim2.new(1,0,1,0)
                              name.TextYAlignment = 'Top'
                              name.BackgroundTransparency = 1
                              name.TextStrokeTransparency = 0.5
                              name.TextColor3 = Color3.fromRGB(255, 0, 0)
                              name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
                          else
                              v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
                          end
                      end
                  else
                      if v.Handle:FindFirstChild('NameEsp'..Number) then
                          v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
                      end
                  end
              end)
          end
      end
      
      function Hop()
          local PlaceID = game.PlaceId
          local AllIDs = {}
          local foundAnything = ""
          local actualHour = os.date("!*t").hour
          local Deleted = false
          function TPReturner()
              local Site;
              if foundAnything == "" then
                  Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
              else
                  Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
              end
              local ID = ""
              if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
                  foundAnything = Site.nextPageCursor
              end
              local num = 0;
              for i,v in pairs(Site.data) do
                  local Possible = true
                  ID = tostring(v.id)
                  if tonumber(v.maxPlayers) > tonumber(v.playing) then
                      for _,Existing in pairs(AllIDs) do
                          if num ~= 0 then
                              if ID == tostring(Existing) then
                                  Possible = false
                              end
                          else
                              if tonumber(actualHour) ~= tonumber(Existing) then
                                  local delFile = pcall(function()
                                      AllIDs = {}
                                      table.insert(AllIDs, actualHour)
                                  end)
                              end
                          end
                          num = num + 1
                      end
                      if Possible == true then
                          table.insert(AllIDs, ID)
                          wait()
                          pcall(function()
                              wait()
                              game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                          end)
                          wait(4)
                      end
                  end
              end
          end
          function Teleport() 
              while wait() do
                  pcall(function()
                      TPReturner()
                      if foundAnything ~= "" then
                          TPReturner()
                      end
                  end)
              end
          end
          Teleport()
      end
      
      spawn(function()
          game:GetService("RunService").RenderStepped:Connect(function()
              if _G.AutoGhostShip or _G.AutoSantaEvents or _G.AutoSecondSea or _G.AutoXmas or _G.AutoSeaking or _G.AutoBigMomBlade or _G.AutoBigMomBoss or _G.AutoKaido or _G.AutoSaber or _G.AutoKillply or _G.AutoFarm or _G.AutoBisento or _G.AutoFarmDungeon or _G.AutoKillply or _G.AutoEnma then
                  if not game:GetService("Workspace"):FindFirstChild("TaiFoot") then
                      local Part = Instance.new("Part")
                      Part.Name = "TaiFoot"
                      Part.Parent = game.Workspace
                      Part.Anchored = true
                      Part.Transparency = 1
                      Part.Size = Vector3.new(30,0.5,30)
                  elseif game:GetService("Workspace"):FindFirstChild("TaiFoot") then
                      game.Workspace["TaiFoot"].CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Y - 3.92,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
                  end
              else
                  if game:GetService("Workspace"):FindFirstChild("TaiFoot") then
                      game:GetService("Workspace"):FindFirstChild("TaiFoot"):Destroy()
                  end
              end
          end)
      end)
      
      spawn(function()
          while wait() do
              if _G.AutoGhostShip or _G.AutoSantaEvents or _G.AutoSecondSea or _G.AutoXmas or _G.AutoSeaking or _G.AutoBigMomBlade or _G.AutoBigMomBoss or _G.AutoKaido or _G.AutoSaber or _G.AutoKillply or _G.AutoFarm or _G.AutoBisento or _G.AutoFarmDungeon or _G.AutoKillply or _G.AutoEnma then
                  pcall(function()
                      game:GetService("Players").LocalPlayer.Character.Services.Client.KenEvent:InvokeServer(true)
                  end)
              end
          end
      end)
      
      spawn(function()
          pcall(function()
              game:GetService("RunService").Stepped:Connect(function()
                  if _G.AutoSantaEvents or _G.AutoSecondSea or _G.AutoXmas or _G.AutoSeaking or _G.AutoBigMomBlade or _G.AutoBigMomBoss or _G.AutoKaido or _G.AutoSaber or _G.AutoKillply or _G.AutoFarm or _G.AutoBisento or _G.AutoFarmDungeon or _G.AutoKillply or _G.AutoEnma or _G.NoClip then
                      for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                          if v:IsA("BasePart") then
                              v.CanCollide = false    
                          end
                      end
                  end
              end)
          end)
      end)
      
      function UseSkill(skill)
          Tool = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool")
          game:GetService("VirtualInputManager"):SendKeyEvent(true,skill,false,game)
          task.wait()
          game:GetService("VirtualInputManager"):SendKeyEvent(false,skill,false,game)
      end
      
      function TP(pos)
          game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = pos
      end
      
      game:GetService("Players").LocalPlayer.Idled:connect(function()
          game:GetService("VirtualUser"):Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
          wait(1)
          game:GetService("VirtualUser"):Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
      end)
      
      function EquipWeapon(ToolSe)
          if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
              getgenv().tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
              wait()
              game.Players.LocalPlayer.Character.Humanoid:EquipTool(tool)
          end
      end
      
      function Click()
          game:GetService'VirtualUser':Button1Down(Vector2.new(0.9,0.9))
          game:GetService'VirtualUser':Button1Up(Vector2.new(0.9,0.9))
      end
      
      function StopNoClip(Config)
          if Config == false then
              if game:GetService("Workspace"):FindFirstChild("TaiFoot") then
                  game:GetService("Workspace"):FindFirstChild("TaiFoot"):Destroy()
              end
          end
      end
      
      function AutoHaki()
          pcall(function()
              if game.Players.LocalPlayer.Character.Haki.Value ~= 1 then
                  game:GetService("Players").LocalPlayer.Character.Services.Client.Armament:FireServer()
                  wait(1.5)
              end
          end)
      end
      --
      local RenUi = library:AddWindow("Biel | King Legacy",Enum.KeyCode.RightControl)
      --
      local Main = RenUi:AddTab("Main","6026568198")
      local Stats = RenUi:AddTab("Stats","7040410130")
      local Combat = RenUi:AddTab("Combat","7251993295")
      local Teleport = RenUi:AddTab("Teleport","7044226690")
      local Dungeon = RenUi:AddTab("Dungeon","7044284832")
      local Misc = RenUi:AddTab("Misc","6034900727")
      local Settings = RenUi:AddTab("Settings","6034509993")
      --
      Main:AddSeperator("Main")
      
      Time = Main:AddLabel("Server Time")
      
      function UpdateTime()
          local GameTime = math.floor(workspace.DistributedGameTime+0.5)
          local Hour = math.floor(GameTime/(60^2))%24
          local Minute = math.floor(GameTime/(60^1))%60
          local Second = math.floor(GameTime/(60^0))%60
          Time:Set("Hr(s) : "..Hour.." Min(s) : "..Minute.." Sec(s) : "..Second)
      end
      
  
      
      
      Main:AddToggle("Auto Farm Level",_G.AutoFarm,function(value)
          _G.AutoFarm = value
          StopNoClip(_G.AutoFarm)
      end)
      
      local LocalPlayer = game:GetService("Players").LocalPlayer
      local VirtualUser = game:GetService('VirtualUser')
      spawn(function()
          while wait() do
              if _G.AutoFarm then
                  pcall(function()
                      CheckQuest()
                      if game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == false then
                          if not game:GetService("Workspace").AntiTPNPC:FindFirstChild("QuestLvl"..LevelQuest) then
                              TP(game:GetService("ReplicatedStorage").MAP["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,0,-3))
                          else 
                              TP(game:GetService("Workspace").AntiTPNPC["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,0,-3))
                          end
                          Click()
                          wait(.5)
                          for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                              if v.Name == "Dialogue" then
                                  v.Accept.Size = UDim2.new(0, 10000, 0, 10000)
                                  v.Accept.Position = UDim2.new(-2, 0, -5, 0)
                                  v.Accept.ImageTransparency = 1
                                  game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer()
                              end
                          end
                      elseif game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == true then
                          Mon = string.sub(game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text,5,#game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.QuestCount.Text)
                          if game:GetService("Workspace").Monster.Mon:FindFirstChild(Mon) then
                              for i,v in pairs(game:GetService("Workspace").Monster.Mon:GetChildren()) do
                                  if v.Name == Mon then
                                      if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                          repeat task.wait()
                                              AutoHaki()
                                              EquipWeapon(_G.SelectWeapon)
                                              VirtualUser:CaptureController()
                                              VirtualUser:ClickButton1(Vector2.new(1280, 672))
                                              TP(v.HumanoidRootPart.CFrame * MethodFarm)
                                              if _G.AutoSkill then 
                                                  UseSkill("Z")
                                                  UseSkill("X")
                                                  UseSkill("C")
                                                  UseSkill("V")
                                              end
                                          until not v.Parent or v.Humanoid.Health <= 0 or _G.AutoFarm == false or game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == false
                                      else
                                          UseSkill("E")
                                          if Second_Sea and game.Players.LocalPlayer.PlayerStats.lvl.Value >= 3275 then
                                              TP(CFrame.new(30272.3203125, 65.4236068725586, 93207.0234375))
                                          else
                                              if not game:GetService("Workspace").AntiTPNPC:FindFirstChild("QuestLvl"..LevelQuest) then
                                                  TP(game:GetService("ReplicatedStorage").MAP["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,500,0))
                                              else 
                                                  TP(game:GetService("Workspace").AntiTPNPC["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,500,0))
                                              end
                                          end
                                      end
                                  end
                              end
                          elseif game:GetService("Workspace").Monster.Boss:FindFirstChild(Mon) then
                              for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                  if v.Name == Mon then
                                      if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                          repeat task.wait()
                                              AutoHaki()
                                              EquipWeapon(_G.SelectWeapon)
                                              VirtualUser:CaptureController()
                                              VirtualUser:ClickButton1(Vector2.new(1280, 672))
                                              TP(v.HumanoidRootPart.CFrame * MethodFarm)
                                              if _G.AutoSkill then 
                                                  UseSkill("Z")
                                                  UseSkill("X")
                                                  UseSkill("C")
                                                  UseSkill("V")
                                              end
                                          until not v.Parent or v.Humanoid.Health <= 0 or _G.AutoFarm == false or game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == false
                                      else
                                          UseSkill("E")
                                          if Second_Sea and game.Players.LocalPlayer.PlayerStats.lvl.Value >= 3275 then
                                              TP(CFrame.new(30272.3203125, 65.4236068725586, 93207.0234375))
                                          else
                                              if not game:GetService("Workspace").AntiTPNPC:FindFirstChild("QuestLvl"..LevelQuest) then
                                                  TP(game:GetService("ReplicatedStorage").MAP["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,500,0))
                                              else 
                                                  TP(game:GetService("Workspace").AntiTPNPC["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,500,0))
                                              end
                                          end
                                      end
                                  end
                              end
                          else 
                              UseSkill("E")
                              if Second_Sea and game.Players.LocalPlayer.PlayerStats.lvl.Value >= 3275 then
                                  TP(CFrame.new(30272.3203125, 65.4236068725586, 93207.0234375))
                              else
                                  if not game:GetService("Workspace").AntiTPNPC:FindFirstChild("QuestLvl"..LevelQuest) then
                                      TP(game:GetService("ReplicatedStorage").MAP["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,500,0))
                                  else 
                                      TP(game:GetService("Workspace").AntiTPNPC["QuestLvl"..LevelQuest].HumanoidRootPart.CFrame * CFrame.new(0,500,0))
                                  end
                              end
                          end
                      end
                  end)
              end
          end
      end)
      
      Main:AddToggle("Auto Second Sea",_G.AutoSecondSea,function(value)
          _G.AutoSecondSea = value
      end)
      
      spawn(function()
          while wait() do
              pcall(function()
                  if _G.AutoSecondSea and First_Sea then
                      if game.Players.LocalPlayer.PlayerStats.IsSecondSea == Yes then
                          TP(CFrame.new(1798.5653076171875, 16.172266006469727, -1475.4083251953125))
                          Click()
                          wait(.5)
                          for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                              if v.Name == "Dialogue" then
                                  v.Accept.Size = UDim2.new(0, 10000, 0, 10000)
                                  v.Accept.Position = UDim2.new(-2, 0, -5, 0)
                                  v.Accept.ImageTransparency = 1
                                  game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer()
                              end
                          end
                      else
                          if game.Players.LocalPlayer.PlayerStats.lvl.Value >= 1500 then
                              _G.AutoFarm = false
                              if game.Players.LocalPlayer.Character:FindFirstChild("Map") or game.Players.LocalPlayer.Backpack:FindFirstChild("Map") then
                                  TP(CFrame.new(6806.78662109375, 211.32806396484375, 1077.6700439453125))
                                  Click()
                                  wait(.5)
                                  for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                                      if v.Name == "Dialogue" then
                                          v.Accept.Size = UDim2.new(0, 10000, 0, 10000)
                                          v.Accept.Position = UDim2.new(-2, 0, -5, 0)
                                          v.Accept.ImageTransparency = 1
                                          game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer()
                                      end
                                  end
                              else
                                  if game:GetService("Players").LocalPlayer.PlayerGui.Quest.QuestBoard.Visible == false then
                                      TP(CFrame.new(6806.78662109375, 211.32806396484375, 1077.6700439453125))
                                      Click()
                                      wait(.5)
                                      for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                                          if v.Name == "Dialogue" then
                                              v.Accept.Size = UDim2.new(0, 10000, 0, 10000)
                                              v.Accept.Position = UDim2.new(-2, 0, -5, 0)
                                              v.Accept.ImageTransparency = 1
                                              game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer()
                                          end
                                      end
                                  else
                                      if game:GetService("Workspace").Monster.Boss:FindFirstChild("Seasoned Fishman [Lv. 2200]") then
                                          for i,v in pairs(game:GetService("Workspace").Monster.Boss:GetChildren()) do
                                              if v.Name == "Seasoned Fishman [Lv. 2200]" and v.Humanoid.Health > 0 then
                                                  repeat task.wait()
                                                      AutoHaki()
                                                      EquipWeapon(_G.SelectWeapon)
                                                      TP(v.HumanoidRootPart.CFrame * MethodFarm)
                                                      if _G.AutoSkill then 
                                                          UseSkill("Z")
                                                          UseSkill("X")
                                                          UseSkill("C")
                                                          UseSkill("V")
                                                      end
                                                      VirtualUser:CaptureController()
                                                      VirtualUser:ClickButton1(Vector2.new(1280, 672))
                                                  until v.Humanoid.Health <= 0 or not _G.AutoSecondSea or game.Players.LocalPlayer.Character:FindFirstChild("Map") or game.Players.LocalPlayer.Backpack:FindFirstChild("Map")
                                              end
                                        
                                        end

                                                   end)
                      end
                  end
              end
          end)
      
          spawn(function()
              while wait() do
                  pcall(function()
                      if _G.AutoFarmDungeon then
                          if game.Players.LocalPlayer.Character.Humanoid.Health > game.Players.LocalPlayer.Character.Humanoid.MaxHealth / 100 * _G.SaveAt then 
                              AutoFarmMobDungeon = true
                              AutoSaveModeDungeon = false
                          else
                              AutoFarmMobDungeon = false
                              AutoSaveModeDungeon = true
                          end
                      end
                  end)
              end
          end)
      
          spawn(function()
              while wait() do
                  if _G.AutoFarmDungeon and AutoFarmMobDungeon then
                      pcall(function()
                          if game.Players.LocalPlayer.Character.Humanoid.Health > game.Players.LocalPlayer.Character.Humanoid.MaxHealth / 100 * _G.SaveAt then
                              for i,v in pairs(game:GetService("Workspace").MOB:GetChildren()) do
                                  if v:FindFirstChild("HumanoidRootPart") then
                                      repeat task.wait()
                                          _G.NotEquip = false
                                          AutoHaki()
                                          TP(v.HumanoidRootPart.CFrame * CFrame.new(0,0,DistanceDungeon))
                                          UseSkill("Z")
                                          UseSkill("X")
                                          UseSkill("C")
                                          UseSkill("V")
                                      until v.Humanoid.Health <= 0 or not _G.AutoFarmDungeon or not AutoFarmMobDungeon or game.Players.LocalPlayer.Character.Humanoid.Health <= game.Players.LocalPlayer.Character.Humanoid.MaxHealth / 100 * _G.SaveAt
                                  end
                              end
                          end
                      end)
                  end
              end
          end)
          
          spawn(function()
              while wait() do
                  if _G.AutoFarmDungeon and AutoSaveModeDungeon then
                      pcall(function()
                          if game.Players.LocalPlayer.Character.Humanoid.Health <= game.Players.LocalPlayer.Character.Humanoid.MaxHealth / 100 * _G.SaveAt then                                                     
                              repeat task.wait()
                                  _G.NotEquip = true
                                  if game:GetService("Workspace").Island:FindFirstChild("Arena1") then
                                      TP(CFrame.new(-9.393295288085938, 201.8232879638672, 16.94792366027832))
                                  else
                                      TP(CFrame.new(-19.639192581176758, 182.88330078125, 6.57674503326416))
                                  end
                                  for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do 
                                      if v:IsA("Tool") then
                                          if v.ToolTip == "Combat" then
                                              EquipWeapon(v.Name)
                                          end
                                      end
                                  end
                                  for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do 
                                      if v:IsA("Tool") then
                                          if v.ToolTip == "Combat" then
                                              EquipWeapon(v.Name)
                                          end
                                      end
                                  end   
                                  game:GetService("VirtualInputManager"):SendKeyEvent(true,"E",false,game.Players.LocalPlayer.Character.HumanoidRootPart)
                              until game.Players.LocalPlayer.Character.Humanoid.Health == game.Players.LocalPlayer.Character.Humanoid.MaxHealth or not AutoSaveModeDungeon or not _G.AutoFarmDungeon
                              _G.NotEquip = false
                              game:GetService("VirtualInputManager"):SendKeyEvent(false,"E",false,game.Players.LocalPlayer.Character.HumanoidRootPart)
                          end
                      end)
                  end
              end
          end)
      end
      
      Misc:AddSeperator("Server")
      
      Misc:AddButton("Rejoin Server",function()
          game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
      end)
      
      Misc:AddButton("Server Hop",function()
          Hop()
      end)
      
      Misc:AddButton("Hop To Lower Player",function()
          getgenv().AutoTeleport = true
          getgenv().DontTeleportTheSameNumber = true 
          getgenv().CopytoClipboard = false
          if not game:IsLoaded() then
              print("Game is loading waiting...")
          end
          local maxplayers = math.huge
          local serversmaxplayer;
          local goodserver;
          local gamelink = "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100" 
          function serversearch()
              for _, v in pairs(game:GetService("HttpService"):JSONDecode(game:HttpGetAsync(gamelink)).data) do
                  if type(v) == "table" and v.playing ~= nil and maxplayers > v.playing then
                      serversmaxplayer = v.maxPlayers
                      maxplayers = v.playing
                      goodserver = v.id
                  end
              end       
          end
          function getservers()
              serversearch()
              for i,v in pairs(game:GetService("HttpService"):JSONDecode(game:HttpGetAsync(gamelink))) do
                  if i == "nextPageCursor" then
                      if gamelink:find("&cursor=") then
                          local a = gamelink:find("&cursor=")
                          local b = gamelink:sub(a)
                          gamelink = gamelink:gsub(b, "")
                      end
                      gamelink = gamelink .. "&cursor=" ..v
                      getservers()
                  end
              end
          end 
          getservers()
          if AutoTeleport then
              if DontTeleportTheSameNumber then 
                  if #game:GetService("Players"):GetPlayers() - 4  == maxplayers then
                      return warn("It has same number of players (except you)")
                  elseif goodserver == game.JobId then
                      return warn("Your current server is the most empty server atm") 
                  end
              end
              game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, goodserver)
          end
      end)
      
      Misc:AddSeperator("Devil Fruits")
      
      Misc:AddToggle("Auto Random Fruit Beli",_G.AutoRandomFruitBeli,function(value)
          _G.AutoRandomFruitBeli = value
      end)
      
      spawn(function()
          while wait() do
              if _G.AutoRandomFruitBeli then
                  pcall(function()
                      if First_Sea then
                          TP(CFrame.new(2027.9697265625, 48.14053726196289, -1737.6326904296875))
                      elseif Second_Sea then
                          TP(CFrame.new(2362.600341796875, 57.83930969238281, 259.5265808105469))
                      end
                      wait(.5)
                      game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer(workspace.AntiTPNPC.ARandomFruit)
                      if game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Beli.Visible == true then
                          Click()
                          wait(.1)
                          for i, v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                              if v.Name == "Dialogue" then
                                  v.Beli.Size = UDim2.new(0, 10000, 0, 10000)
                                  v.Beli.Position = UDim2.new(-2, 0, -5, 0)
                                  v.Beli.ImageTransparency = 1
                              end
                          end
                      end
                  end)
              end
          end
      end)
      
      Misc:AddToggle("Auto Random Fruit Gem",_G.AutoRandomFruitGem,function(value)
          _G.AutoRandomFruitGem = value
      end)
      
      spawn(function()
          while wait() do
              if _G.AutoRandomFruitGem then
                  pcall(function()
                      if First_Sea then
                          TP(CFrame.new(2027.9697265625, 48.14053726196289, -1737.6326904296875))
                      elseif Second_Sea then
                          TP(CFrame.new(2362.600341796875, 57.83930969238281, 259.5265808105469))
                      end
                      wait(.5)
                      game:GetService("ReplicatedStorage").Remotes.Functions.CheckQuest:InvokeServer(workspace.AntiTPNPC.ARandomFruit)
                      if game:GetService("Players").LocalPlayer.PlayerGui.ARandomFruit.Dialogue.Gem.Visible == true then
                          Click()
                          wait(.1)
                          for i, v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
                              if v.Name == "Dialogue" then
                                  v.Gem.Size = UDim2.new(0, 10000, 0, 10000)
                                  v.Gem.Position = UDim2.new(-2, 0, -5, 0)
                                  v.Gem.ImageTransparency = 1
                              end
                          end
                      end
                  end)
              end
          end
      end)
      
      Misc:AddToggle("Bring Fruit",_G.BringFruit,function(value)
          _G.BringFruit = value
      end)
      
      spawn(function()
          while wait() do
              if _G.BringFruit then
                  pcall(function()
                      for i,v in pairs(game.Workspace:GetChildren()) do
                          if v:IsA("Tool") then
                              v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
                          end
                      end	
                  end)
              end
          end
      end)
      
      Misc:AddSeperator("Abilities")
      
      OldCanGeppo = game.Players.LocalPlayer.Backpack.GeppoNew.cds.Value
      Misc:AddToggle("Inf Geppo",false,function(value)
          if value == true then
              game.Players.LocalPlayer.Backpack.GeppoNew.cds.Value = 1000000000000000000
          elseif value == false then
              game.Players.LocalPlayer.Backpack.GeppoNew.cds.Value = OldCanGeppo
          end
      end)
      
      Misc:AddToggle("Fly",false,function(value)
          Fly = value
      end)
      
      spawn(function()
          while wait() do
              pcall(function()
                  if Fly then
                      fly()
                  end
              end)
          end
      end)
      
      Misc:AddToggle("No Clip",false,function(value)
          _G.NoClip = value
      end)
      
      Misc:AddSeperator("ESP")
      
      Misc:AddToggle("Player ESP",ESPPlayer,function(value)
          ESPPlayer = value
          while ESPPlayer do wait()
              UpdateEspPlayer()
          end
      end)
      
      Misc:AddToggle("Devil Fruit ESP",DevilFruitESP,function(value)
          DevilFruitESP = value
          while DevilFruitESP do wait()
              UpdateBfEsp() 
          end
      end)
      
      Settings:AddSeperator("Ui")
      
      Settings:AddButton("Destroy Ui",function()
          if game.CoreGui:FindFirstChild("UlLib") then
              game.CoreGui:FindFirstChild("UlLib"):Destroy()
          end
      end)
      
      Settings:AddTextbox("Level","",true,function(value)
          _G.LockAt = value
      end)
      
      Settings:AddToggle("Lock Level",_G.LockLevel,function(value)
          _G.LockLevel = value
      end)
      
      spawn(function()
          while wait() do 
              if _G.LockLevel then
                  pcall(function()
                      if game.Players.LocalPlayer.PlayerStats.lvl.Value >= tonumber(_G.LockAt) then
                          game.Players.LocalPlayer:Kick("\nSuccessfully Farm!")
                      end
                  end)
              end
          end
      end)
  else
  game.Players.LocalPlayer:kick("No Support lol Eror Code 555+")
  end
                  
 
