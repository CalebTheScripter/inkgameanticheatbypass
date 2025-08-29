local success1,err1=pcall(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/wefwef127382/inkgames.github.io/refs/heads/main/ringta.lua"))() end)
local success2,err2=pcall(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/CalebTheScripter/AlchemistWare/refs/heads/main/src.lua"))() end)
if not(success1 and success2) then game.Players.LocalPlayer:Kick("u r either stoopid or I broke somethin XD either way gtfo") return end
task.spawn(function()
local AliveNotifications,NotificationUI={},nil
local function CreateNotificationUI() if NotificationUI then return NotificationUI end NotificationUI=Instance.new("ScreenGui") NotificationUI.Name,NotificationUI.ZIndexBehavior,NotificationUI.Parent="NotificationUI",Enum.ZIndexBehavior.Sibling,game:GetService("CoreGui") return NotificationUI end
local function MakeNotif(title,message,duration,color)
local ui=CreateNotificationUI() title,message,duration,color=title or "Notification",message or "",duration or 5,color or Color3.fromRGB(255,200,0)
local notification=Instance.new("Frame") notification.Size,notification.Position,notification.BackgroundColor3,notification.BorderSizePixel,notification.Parent=UDim2.new(0,250,0,80),UDim2.new(1,50,1,10),Color3.fromRGB(30,30,30),0,ui
Instance.new("UICorner",notification).CornerRadius=UDim.new(0,8)
local titleLabel=Instance.new("TextLabel") titleLabel.Size,titleLabel.Position,titleLabel.Font,titleLabel.Text,titleLabel.TextSize,titleLabel.TextColor3,titleLabel.BackgroundTransparency,titleLabel.TextXAlignment,titleLabel.Parent=UDim2.new(1,-25,0,25),UDim2.new(0,15,0,5),Enum.Font.SourceSansBold,title,18,color,1,Enum.TextXAlignment.Left,notification
local messageLabel=Instance.new("TextLabel") messageLabel.Size,messageLabel.Position,messageLabel.Font,messageLabel.Text,messageLabel.TextSize,messageLabel.TextColor3,messageLabel.BackgroundTransparency,messageLabel.TextXAlignment,messageLabel.TextWrapped,messageLabel.Parent=UDim2.new(1,-25,0,50),UDim2.new(0,15,0,30),Enum.Font.SourceSans,message,16,Color3.new(1,1,1),1,Enum.TextXAlignment.Left,true,notification
local colorBar=Instance.new("Frame") colorBar.Size,colorBar.BackgroundColor3,colorBar.BorderSizePixel,colorBar.Parent=UDim2.new(0,5,1,0),color,0,notification
Instance.new("UICorner",colorBar).CornerRadius=UDim.new(0,8)
local offsit=0 for _,n in pairs(AliveNotifications) do if n.Instance and n.Instance.Parent then offsit=offsit+n.Instance.Size.Y.Offset+10 end end
local targetPos=UDim2.new(1,-270,1,-90-offsit)
table.insert(AliveNotifications,{Instance=notification,ExpireTime=os.time()+duration})
game:GetService("TweenService"):Create(notification,TweenInfo.new(0.5,Enum.EasingStyle.Quint),{Position=targetPos}):Play()
task.spawn(function() task.wait(duration) local tweenOut=game:GetService("TweenService"):Create(notification,TweenInfo.new(0.5,Enum.EasingStyle.Quint),{Position=UDim2.new(1,50,targetPos.Y.Scale,targetPos.Y.Offset)}) tweenOut:Play() tweenOut.Completed:Wait() for i,n in pairs(AliveNotifications) do if n.Instance==notification then table.remove(AliveNotifications,i) break end end notification:Destroy() end)
end
local function IsMobile() local uis=game:GetService("UserInputService") return uis.TouchEnabled and not uis.KeyboardEnabled end
if IsMobile() then MakeNotif("lol r u on a phone?","grooooooss. I guess u can join my discord https://discord.gg/xB6V95aXjg.",8,Color3.fromRGB(0,255,0)) end
end)
