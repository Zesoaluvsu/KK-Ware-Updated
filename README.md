
game.StarterGui:SetCore("SendNotification",  {
 Title = "Executed.";
 Text = "Made By KKxz";
 Icon = "http://www.roblox.com/asset/?id=951528747";
 Duration = 98083905839058095809389034;
 Button1 = "Close";
 Button2 = "W";
 Button3 = "W";
 Callback = NotificationBindable;
}
)
local UILibrary = loadstring(game:HttpGet("https://pastebin.com/raw/V1ca2q9s"))()

local MainUI = UILibrary.Load("KK Ware")
local FirstPage = MainUI.AddPage("Aiming")
local SecondPage = MainUI.AddPage("DONT USE")
local ThirdPage = MainUI.AddPage("Become Rich 💰")
local FourthPage = MainUI.AddPage("Anims")
local FifthPage = MainUI.AddPage("Combat")
local x = MainUI.AddPage("Auto Buy")
local y = MainUI.AddPage("Fun Menu")


local FirstLabel = FirstPage.AddLabel("Locks")
local FirstLabel = ThirdPage.AddLabel("Become Rich | CS")
local FirstLabel = FourthPage.AddLabel("Animations FE")
local FirstLabel = FifthPage.AddLabel("Combat")
local FirstButton = FirstPage.AddButton("Cam lock (Q)", function()
getgenv().AimPart = "HumanoidRootPart"
	local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://413861777"
	sound.Parent = game:GetService("SoundService")
	sound:Play()
	getgenv().AimlockKey = "q"
	getgenv().AimRadius = 45
	getgenv().ThirdPerson = true
	getgenv().FirstPerson = true
	getgenv().TeamCheck = false
	getgenv().PredictMovement = true
	getgenv().PredictionVelocity = 9
	local L_27_, L_28_, L_29_, L_30_ =
            game:GetService "Players",
            game:GetService "UserInputService",
            game:GetService "RunService",
            game:GetService "StarterGui"
	local L_31_, L_32_, L_33_, L_34_, L_35_, L_36_, L_37_ =
            L_27_.LocalPlayer,
            L_27_.LocalPlayer:GetMouse(),
            workspace.CurrentCamera,
            CFrame.new,
            Ray.new,
            Vector3.new,
            Vector2.new
	local L_38_, L_39_, L_40_ = true, false, false
	local L_41_
	getgenv().CiazwareUniversalAimbotLoaded = true
	getgenv().WorldToViewportPoint = function(L_42_arg0)
		return L_33_:WorldToViewportPoint(L_42_arg0)
	end
	getgenv().WorldToScreenPoint = function(L_43_arg0)
		return L_33_.WorldToScreenPoint(L_33_, L_43_arg0)
	end
	getgenv().GetObscuringObjects = function(L_44_arg0)
		if L_44_arg0 and L_44_arg0:FindFirstChild(getgenv().AimPart) and L_31_ and L_31_.Character:FindFirstChild("Head") then
			local L_45_ = workspace:FindPartOnRay(L_35_(L_44_arg0[getgenv().AimPart].Position, L_31_.Character.Head.Position))
			if L_45_ then
				return L_45_:IsDescendantOf(L_44_arg0)
			end
		end
	end
	getgenv().GetNearestTarget = function()
		local L_46_ = {}
		local L_47_ = {}
		local L_48_ = {}
		for L_50_forvar0, L_51_forvar1 in pairs(L_27_:GetPlayers()) do
			if L_51_forvar1 ~= L_31_ then
				table.insert(L_46_, L_51_forvar1)
			end
		end
		for L_52_forvar0, L_53_forvar1 in pairs(L_46_) do
			if L_53_forvar1.Character ~= nil then
				local L_54_ = L_53_forvar1.Character:FindFirstChild("Head")
				if getgenv().TeamCheck == true and L_53_forvar1.Team ~= L_31_.Team then
					local L_55_ =
                            (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
					local L_56_ =
                            Ray.new(
                            game.Workspace.CurrentCamera.CFrame.p,
                            (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_55_
                        )
					local L_57_, L_58_ = game.Workspace:FindPartOnRay(L_56_, game.Workspace)
					local L_59_ = math.floor((L_58_ - L_54_.Position).magnitude)
					L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
					L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_55_
					L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
					L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_59_
					table.insert(L_48_, L_59_)
				elseif getgenv().TeamCheck == false and L_53_forvar1.Team == L_31_.Team then
					local L_60_ =
                            (L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
					local L_61_ =
                            Ray.new(
                            game.Workspace.CurrentCamera.CFrame.p,
                            (L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_60_
                        )
					local L_62_, L_63_ = game.Workspace:FindPartOnRay(L_61_, game.Workspace)
					local L_64_ = math.floor((L_63_ - L_54_.Position).magnitude)
					L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
					L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_60_
					L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
					L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_64_
					table.insert(L_48_, L_64_)
				end
			end
		end
		if unpack(L_48_) == nil then
			return nil
		end
		local L_49_ = math.floor(math.min(unpack(L_48_)))
		if L_49_ > getgenv().AimRadius then
			return nil
		end
		for L_65_forvar0, L_66_forvar1 in pairs(L_47_) do
			if L_66_forvar1.diff == L_49_ then
				return L_66_forvar1.plr
			end
		end
		return nil
	end
	L_32_.KeyDown:Connect(
            function(L_67_arg0)
		if L_67_arg0 == AimlockKey and L_41_ == nil then
			pcall(
                        function()
				if L_39_ ~= true then
					L_39_ = true
				end
				local L_68_
				L_68_ = GetNearestTarget()
				if L_68_ ~= nil then
					L_41_ = L_68_
				end
			end
                    )
		elseif L_67_arg0 == AimlockKey and L_41_ ~= nil then
			if L_41_ ~= nil then
				L_41_ = nil
			end
			if L_39_ ~= false then
				L_39_ = false
			end
		end
	end
        )
	L_29_.RenderStepped:Connect(
            function()
		if getgenv().ThirdPerson == true and getgenv().FirstPerson == true then
			if
                        (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 or
                            (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1
                     then
				L_40_ = true
			else
				L_40_ = false
			end
		elseif getgenv().ThirdPerson == true and getgenv().FirstPerson == false then
			if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 then
				L_40_ = true
			else
				L_40_ = false
			end
		elseif getgenv().ThirdPerson == false and getgenv().FirstPerson == true then
			if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1 then
				L_40_ = true
			else
				L_40_ = false
			end
		end
		if L_38_ == true and L_39_ == true then
			if L_41_ and L_41_.Character and L_41_.Character:FindFirstChild(getgenv().AimPart) then
				if getgenv().FirstPerson == true then
					if L_40_ == true then
						if getgenv().PredictMovement == true then
							L_33_.CFrame =
                                        L_34_(
                                        L_33_.CFrame.p,
                                        L_41_.Character[getgenv().AimPart].Position +
                                            L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                    )
						elseif getgenv().PredictMovement == false then
							L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
						end
					end
				elseif getgenv().ThirdPerson == true then
					if L_40_ == true then
						if getgenv().PredictMovement == true then
							L_33_.CFrame =
                                        L_34_(
                                        L_33_.CFrame.p,
                                        L_41_.Character[getgenv().AimPart].Position +
                                            L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
                                    )
						elseif getgenv().PredictMovement == false then
							L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
						end
					end
				end
			end
		end
	end
        )
end)
local FirstButton = FirstPage.AddButton("Silent Aim Stuff", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/PewPewBoy/Silent-Aim-Tho/main/Silent%20Aim%20stuff",true))()
end)
local FirstButton = FirstPage.AddButton("Cam Lock (Made by tenaki)", function()
getgenv().RecurringPoint = "UpperTorso"
getgenv().Hitbox = "UpperTorso"
getgenv().Keybind = "q"
getgenv().AimbotStrengthAmount = 0.02969
getgenv().PredictionAmount = 10
getgenv().Radius = 25
getgenv().UsePrediction = true
getgenv().AimbotStrength = true
getgenv().FirstPerson = true
getgenv().ThirdPerson = true
getgenv().TeamCheck = false
getgenv().Enabled = true


-- // main script  / / -- 

loadstring(game:HttpGet("https://raw.githubusercontent.com/tenaaki/GenericAimbot/main/v1.0.0"))()
end)
local FirstButton = FirstPage.AddButton("Dot Lock (e)", function()
local Settings = {
    rewrittenmain = {
        Enabled = true,
        Key = "e",
        DOT = true,
        AIRSHOT = true,
        NOTIF = false,
        AUTOPRED = false,
        FOV = math.huge,
        RESOVLER = false
    }
}

local SelectedPart = "Head"
local Prediction = true
local PredictionValue = 0.12467245219812


    local AnchorCount = 0
    local MaxAnchor = 50

    local CC = game:GetService"Workspace".CurrentCamera
    local Plr;
    local enabled = false
    local accomidationfactor = 0.1234772452176
    local mouse = game.Players.LocalPlayer:GetMouse()
    local placemarker = Instance.new("Part", game.Workspace)

    function makemarker(Parent, Adornee, Color, Size, Size2)
        local e = Instance.new("BillboardGui", Parent)
        e.Name = "PP"
        e.Adornee = Adornee
        e.Size = UDim2.new(Size, Size2, Size, Size2)
        e.AlwaysOnTop = Settings.rewrittenmain.DOT
        local a = Instance.new("Frame", e)
        if Settings.rewrittenmain.DOT == true then
        a.Size = UDim2.new(1, 0, 1, 0)
        else
        a.Size = UDim2.new(0, 0, 0, 0)
        end
        if Settings.rewrittenmain.DOT == true then
        a.Transparency = 0
        a.BackgroundTransparency = 0
        else
        a.Transparency = 1
        a.BackgroundTransparency = 1
        end
        a.BackgroundColor3 = Color
        local g = Instance.new("UICorner", a)
        if Settings.rewrittenmain.DOT == false then
        g.CornerRadius = UDim.new(0, 0)
        else
        g.CornerRadius = UDim.new(1, 1) 
        end
        return(e)
    end

    
    local data = game.Players:GetPlayers()
    function noob(player)
        local character
        repeat wait() until player.Character
        local handler = makemarker(guimain, player.Character:WaitForChild(SelectedPart), Color3.fromRGB(107, 184, 255), 0.3, 3)
        handler.Name = player.Name
        player.CharacterAdded:connect(function(Char) handler.Adornee = Char:WaitForChild(SelectedPart) end)


        spawn(function()
            while wait() do
                if player.Character then
                end
            end
        end)
    end

    for i = 1, #data do
        if data[i] ~= game.Players.LocalPlayer then
            noob(data[i])
        end
    end

    game.Players.PlayerAdded:connect(function(Player)
        noob(Player)
    end)

    spawn(function()
        placemarker.Anchored = true
        placemarker.CanCollide = false
        if Settings.rewrittenmain.DOT == true then
        placemarker.Size = Vector3.new(8, 8, 8)
        else
        placemarker.Size = Vector3.new(0, 0, 0)
        end
        placemarker.Transparency = 0.75
        if Settings.rewrittenmain.DOT then
        makemarker(placemarker, placemarker, Color3.fromRGB(232, 186, 200), 0.40, 0)
        end
    end)

    game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(k)
        if k == Settings.rewrittenmain.Key and Settings.rewrittenmain.Enabled then
            if enabled == true then
                enabled = false
                if Settings.rewrittenmain.NOTIF == true then
                    Plr = getClosestPlayerToCursor()
                game.StarterGui:SetCore("SendNotification", {
						Title = "Locking Alert",
						Text = "Unlocked",
						Icon = "http://www.roblox.com/asset/?id=8850953349",
						Duration = 1,
})
            end
            else
                Plr = getClosestPlayerToCursor()
                enabled = true
                if Settings.rewrittenmain.NOTIF == true then

                    game.StarterGui:SetCore("SendNotification", {
						Title = "Locking Alert",
						Text = "Locked on :"..tostring(Plr.Name);
						Icon = "http://www.roblox.com/asset/?id=8850953349",
						Duration = 1,
})

                end
            end
        end
    end)



    function getClosestPlayerToCursor()
        local closestPlayer
        local shortestDistance = Settings.rewrittenmain.FOV

        for i, v in pairs(game.Players:GetPlayers()) do
            if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then
                local pos = CC:WorldToViewportPoint(v.Character.PrimaryPart.Position)
                local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(mouse.X, mouse.Y)).magnitude
                if magnitude < shortestDistance then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end
        return closestPlayer
    end

    local pingvalue = nil;
    local split = nil;
    local ping = nil;

    game:GetService"RunService".Stepped:connect(function()
        if enabled and Plr.Character ~= nil and Plr.Character:FindFirstChild("HumanoidRootPart") then
            placemarker.CFrame = CFrame.new(Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor))
        else
            placemarker.CFrame = CFrame.new(0, 9999, 0)
        end
        if Settings.rewrittenmain.AUTOPRED == true then
             pingvalue = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
             split = string.split(pingvalue,'(')
             ping = tonumber(split[1])
            if ping < 130 then
                PredictionValue = 0.151
            elseif ping < 125 then
                PredictionValue = 0.149
            elseif ping < 110 then
                PredictionValue = 0.146
            elseif ping < 105 then
                PredictionValue = 0.138
            elseif ping < 90 then
                PredictionValue = 0.136
            elseif ping < 80 then
                PredictionValue = 0.134
            elseif ping < 70 then
                PredictionValue = 0.131
            elseif ping < 60 then
                PredictionValue = 0.1229
            elseif ping < 50 then
                PredictionValue = 0.1225
            elseif ping < 40 then
                PredictionValue = 0.1256
            end
        end
    end)

    local mt = getrawmetatable(game)
    local old = mt.__namecall
    setreadonly(mt, false)
    mt.__namecall = newcclosure(function(...)
        local args = {...}
        if enabled and getnamecallmethod() == "FireServer" and args[2] == "UpdateMousePos" and Settings.rewrittenmain.Enabled and Plr.Character ~= nil then

            -- args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor)
            --[[
            if Settings.rewrittenmain.AIRSHOT == true then
                if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
                    
                    --// Airshot
                    args[3] = Plr.Character.LeftFoot.Position+(Plr.Character.LeftFoot.Velocity*PredictionValue)

                else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)

                end
            else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)
            end
            ]]
            if Prediction == true then
                
            args[3] = Plr.Character[SelectedPart].Position+(Plr.Character[SelectedPart].Velocity*PredictionValue)

            else

            args[3] = Plr.Character[SelectedPart].Position

            end

            return old(unpack(args))
        end
        return old(...)
    end)

    game:GetService("RunService").RenderStepped:Connect(function()
        if Settings.rewrittenmain.RESOVLER == true and Plr.Character ~= nil and enabled and Settings.rewrittenmain.Enabled then
        if Settings.rewrittenmain.AIRSHOT == true and enabled and Plr.Character ~= nil then
            
            if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
                
                --// Airshot

                --// Anchor Check

                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end

                SelectedPart = "LeftFoot"

            else
                --// Anchor Check

                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end

                SelectedPart = "HumanoidRootPart"

            end
            else

                --// Anchor Check

                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end

                SelectedPart = "HumanoidRootPart"
            end

        else
                SelectedPart = "HumanoidRootPart"
        end
    end)

end)
local FirstButton = ThirdPage.AddButton("Headless CS", function()
getgenv().game.Players.LocalPlayer.Character.Head.Transparency = 1
    getgenv().game.Players.LocalPlayer.Character.Head.face:Destroy()
    getgenv().game.Players.LocalPlayer.Character.Head.face:Destroy()
end)
local FirstButton = ThirdPage.AddButton("Korblox (RL)", function()
local ply = game.Players.LocalPlayer
	local chr = ply.Character
	chr.RightLowerLeg.MeshId = "902942093"
	chr.RightLowerLeg.Transparency = "1"
	chr.RightUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
	chr.RightUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
	chr.RightFoot.MeshId = "902942089"
	chr.RightFoot.Transparency = "1"
end)
local FirstButton = ThirdPage.AddButton("Korblox (LL)", function()
local ply = game.Players.LocalPlayer
local chr = ply.Character
chr.LeftLowerLeg.MeshId = "101851582"
chr.LeftLowerLeg.Transparency = "1"
chr.LeftUpperLeg.MeshId = "http://www.roblox.com/asset/?id=101851582"
chr.LeftUpperLeg.TextureID = "http://roblox.com/asset/?id=101851582"
chr.LeftFoot.MeshId = "101851582"
chr.LeftFoot.Transparency = "1"
end)
local FirstButton = ThirdPage.AddButton("Sshf CS", function()
local L_409_ = game.Players.LocalPlayer.Character
	local L_410_ = L_409_:WaitForChild("Head")
	local L_411_ = L_410_:WaitForChild("face")
	L_411_.Texture = "rbxassetid://494290547"
end)
local FirstButton = ThirdPage.AddButton("Beast Mode CS", function()
	local L_412_ = game.Players.LocalPlayer.Character
	local L_413_ = L_412_:WaitForChild("Head")
	local L_414_ = L_413_:WaitForChild("face")
	L_414_.Texture = "rbxassetid://127959433"
end)
local FirstButton = ThirdPage.AddButton("Playful Vamp CS", function()
    local L_415_ = game.Players.LocalPlayer.Character
	local L_416_ = L_415_:WaitForChild("Head")
	local L_417_ = L_416_:WaitForChild("face")
	L_417_.Texture = "rbxassetid://2409281591"
end)
local FirstButton = FourthPage.AddButton("Asstronaut", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=891621366"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=891633237"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=891636393"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=891636393"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=891627522"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=891609353"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=891617961"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Oldschool", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=5319828216"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=5319828216"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=5319844329"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=5319844329"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=5319841935"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=5319816685"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=5319839762"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Toy", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=782841498"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=782841498"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=782842708"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=782842708"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=782847020"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=782843869"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=782846423"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Stylish", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616136790"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616136790"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616140816"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616140816"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616139451"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616133594"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616134815"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Robot", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616088211"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616088211"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616091570"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616091570"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616090535"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616086039"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616087089"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Zombie", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616158929"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616158929"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616163682"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616163682"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616161997"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616156119"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616157476"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Bubbly", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=910004836"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=910004836"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616163682"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=910025107"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=910016857"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616156119"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=910001910"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Ninja", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=656117400"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=656117400"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=656118852"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=656118852"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=656117878"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=656114359"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=656115606"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Cartoony", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=742637544"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=742637544"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=742638842"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=742638842"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=742637942"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=742636889"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=742637151"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FirstButton = FourthPage.AddButton("Mage", function()
local Animate = game.Players.LocalPlayer.Character.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=707742142"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=707742142"
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=707861613"
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=707861613"
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=707853694"
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=707826056"
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=707829716"
    game.Players.LocalPlayer.Character.Humanoid.Jump = false
    wait(1)
end)
local FifthButton = FifthPage.AddButton("Fly", function()
	local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://413861777"
	sound.Parent = game:GetService("SoundService")
	sound:Play()
loadstring(game:HttpGet("https://pastebin.com/raw/sUA9m6M6"))()
end)
local FifthButton = FifthPage.AddButton("Speed Script (T)", function()
	local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://413861777"
	sound.Parent = game:GetService("SoundService")
	sound:Play()
loadstring(game:HttpGet("https://raw.githubusercontent.com/coolmanstrongsuperman/lol/main/SpeedWare%20T%20to%20speed"))()
end)
local FifthButton = FifthPage.AddButton("Force Reset (-)", function()
	local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://413861777"
	sound.Parent = game:GetService("SoundService")
	sound:Play()
local Tool = script.Parent
local mouse = game.Players.LocalPlayer:GetMouse()

function onKeyDown(key)
 if (key~=nil) then
  key = key:lower()
  if (key=="-")  then
   game.Players.LocalPlayer.Character.Humanoid.Health = 0
  end
 end
end

mouse.KeyDown:connect(onKeyDown)
end)
local FifthButton = FifthPage.AddButton("Long Fists (Q)", function()
	local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://413861777"
	sound.Parent = game:GetService("SoundService")
	sound:Play()

	wait()
	game.StarterGui:SetCore("SendNotification", {
		Title = "wsg"; -- the title (ofc)
		Text = "hey daddy"; -- what the text says (ofc)
		Duration = 5; -- how long the notification should in secounds
	})
	local localPlayer       = game:GetService("Players").LocalPlayer;
	local localCharacter    = localPlayer.Character
	local Mouse             = localPlayer:GetMouse();
	local FistControl       = false
	local LeftFist          = localCharacter.LeftHand;
	local RightFist         = localCharacter.RightHand;

	-- // Services
	local uis = game:GetService("UserInputService");

	-- // Coroutine Loop + Functions
	local loopFunction = function()
		LeftFist.CFrame  = CFrame.new(Mouse.Hit.p);
		RightFist.CFrame = CFrame.new(Mouse.Hit.p);
	end;

	local Loop

	local Start = function()
		Loop = game:GetService("RunService").Heartbeat:Connect(loopFunction);
	end;

	local Pause = function()
		Loop:Disconnect()
	end;

	-- // Hotkeys
	uis.InputBegan:connect(function(Key)
		if (Key.KeyCode == Enum.KeyCode.Q) then
			if (FistControl == false) then
				FistControl = true;
				Start();
				pcall(function()
					localCharacter.RightHand.RightWrist:Remove();
					localCharacter.LeftHand.LeftWrist:Remove();
				end);
			elseif (FistControl == true) then
				FistControl = false;
				Pause();
				local rightwrist  = Instance.new("Motor6D");
				rightwrist.Name   = "RightWrist";
				rightwrist.Parent = localCharacter.RightHand;
				rightwrist.C0     = CFrame.new(1.18422506e-07, -0.5009287, -6.81715525e-18, 1, 0, 0, 0, 1, 0, 0, 0, 1);
				rightwrist.C1     = CFrame.new(3.55267503e-07, 0.125045404, 5.92112528e-08, 1, 0, 0, 0, 1, 0, 0, 0, 1);
				rightwrist.Part0  = localCharacter.RightLowerArm;
				rightwrist.Part1  = localCharacter.RightHand;

				local leftwrist   = Instance.new("Motor6D");
				leftwrist.Name    = "LeftWrist";
				leftwrist.Parent  = localCharacter.LeftHand;
				leftwrist.C0      = CFrame.new(0.000475466368, -0.5009287, 7.59417072e-20, 1, 0, 0, 0, 1, 0, 0, 0, 1);
				leftwrist.C1      = CFrame.new(0.000475821638, 0.125045404, 5.92112528e-08, 1, 0, 0, 0, 1, 0, 0, 0, 1);
				leftwrist.Part0   = localCharacter.LeftLowerArm;
				leftwrist.Part1   = localCharacter.LeftHand;
			end;
		end;
	end);
end)
local FifthButton = FifthPage.AddButton("Reach", function()
local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://413861777"
	sound.Parent = game:GetService("SoundService")
	sound:Play()

	wait()
	game.StarterGui:SetCore("SendNotification", {
		Title = "hi"; -- the title (ofc)
		Text = "Fist Reach Successly!"; -- what the text says (ofc)
		Duration = 5; -- how long the notification should in secounds
	})
	LP = game.Players.LocalPlayer
	for i,v in ipairs(LP.Character:GetDescendants()) do
		if v:IsA("MeshPart") then v.Massless = true
			v.CanCollide = false
			v.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0, 0, 0)

		end
	end

	for i,v in ipairs(game.workspace:GetDescendants()) do
		if v:IsA("Seat") then 
			v.Disabled = true
		end
	end
	x = 40
	y = 40
	z = 40


	penis = Vector3.new(x,y,z)

	LP.Character.RightHand.Size = penis

	LP.Character.RightHand.Transparency = 1
	local selectionBox = Instance.new("SelectionBox",LP.Character.RightHand)
	selectionBox.Adornee = LP.Character.RightHand
	selectionBox.Color3 = Color3.new(0, 0, 0)
end)
local FifthButton = FifthPage.AddButton("Anti Stomp", function()
pcall(function() if tostring(game.PlaceId) == "2788229376" then local corepackages = game:GetService"CorePackages" local localplayer = game:GetService"Players".LocalPlayer local run = game:GetService"RunService" run:BindToRenderStep("rrrrrrrrrrr",2000,function() pcall(function() if localplayer.Character.Humanoid.Health <= 30 then localplayer.Character.Humanoid:UnequipTools() localplayer.Character.Humanoid:Destroy() workspace.CurrentCamera.CameraSubject = localplayer.Character wait() local prt = Instance.new("Model", corepackages); Instance.new("Part", prt).Name="Torso"; Instance.new("Part", prt).Name="Head"; Instance.new("Humanoid", prt).Name="Humanoid"; localplayer.Character=prt end end) pcall(function() if localplayer.Character.Humanoid.FloorMaterial == "Plastic" then ReplicatedStorage:FireServer("Stomp") end end) end) loadstring(game:HttpGet("https://pastebin.com/qtxv1qZV", true))() end end)   
end)
local FirstButton = FifthPage.AddButton("Anti Grab", function()
			local player = game.Players.LocalPlayer
			local GC = game:GetService("Workspace").Players:WaitForChild(player.Name):FindFirstChild("GRABBING_CONSTRAINT")
			if GC then
				GC:Destroy()
				wait(0.04)
				player.character.Humanoid.Sit = true
				wait(0.04)
				game.Players.LocalPlayer.Character.Humanoid:ChangeState(3)
			end
end)
local FirstButton = FifthPage.AddButton("Infinte Jump", function()
local player = game.Players.LocalPlayer
		local spacedown = false
		staminup = true
		game:GetService('UserInputService').InputBegan:Connect(function(key,b)
			if key.KeyCode == Enum.KeyCode.Space and not b then
				if staminup == true then
					spacedown = true
					while spacedown == true do
						wait()
						player.Character:FindFirstChildWhichIsA('Humanoid').JumpPower = 50
						player.Character:FindFirstChildWhichIsA('Humanoid').Jump = true
						player.Character:FindFirstChildWhichIsA('Humanoid').JumpPower = 50
					end
				end
			end
		end)
		game:GetService('UserInputService').InputEnded:Connect(function(key,b)
			if key.KeyCode == Enum.KeyCode.Space and not b then
				if staminup == true then
					spacedown = false
				end
			end
		end)
end)
local FirstButton = FifthPage.AddButton("No Recoil", function()
		local player = game.Players.LocalPlayer
		for i,v in pairs(game:GetService('Workspace'):GetChildren()) do
			if v:IsA('Camera') then
				v:Destroy()
			end
		end
		local newcam = Instance.new('Camera')
		newcam.Parent = game:GetService('Workspace')
		newcam.Name = 'Camera'
		newcam.CameraType = 'Custom'
		newcam.CameraSubject = player.Character:FindFirstChildWhichIsA('Humanoid')
		newcam.HeadLocked = true
		newcam.HeadScale = 1 
end)
local FirstButton = x.AddButton("Double Barrel [fixing]", function()
local Workspace = game:GetService("Workspace")
local Players = game.Players.LocalPlayer

local Character = Players.Character

function Buy(Object)
    local Object = Object
    local LockPicker = Workspace.Ignored.Shop[Object]
    Character.HumanoidRootPart.CFrame = LockPicker.Head.CFrame + Vector3.new(0, 3, 0)
    wait(0.5)
    fireclickdetector(LockPicker.ClickDetector)
    fireclickdetector(LockPicker.ClickDetector)
end

Buy("[Double-Barrel SG] - $1400")

wait(0.5)

game.ReplicatedStorage:FindFirstChild(".gg/untitledhood"):FireServer(
    "Reload",
    {
        Name = "[Double-Barrel SG]", --// reminder: [Double-Barrel SG] or [Revolver] works for any gun but i put it here so i can just copy and paste whenever i want to
        Parent = Game.Players.LocalPlayer.Backpack,
        ClassName = "Tool",
        Ammo = {Value = math.huge*9e9},
        MaxAmmo = {Value = 0},
        GunScript = game:GetService("Players").LocalPlayer.Backpack["[Double-Barrel SG]"].GunScript,
        Handle = game:GetService("Players").LocalPlayer.Backpack["[Double-Barrel SG]"].Handle
    }
)

wait(2)
end)
local FirstButton = x.AddButton("Revolver [fixing]", function()
local Workspace = game:GetService("Workspace")
local Players = game.Players.LocalPlayer

local Character = Players.Character

function Buy(Object)
    local Object = Object
    local LockPicker = Workspace.Ignored.Shop[Object]
    Character.HumanoidRootPart.CFrame = LockPicker.Head.CFrame + Vector3.new(0, 3, 0)
    wait(0.5)
    fireclickdetector(LockPicker.ClickDetector)
    fireclickdetector(LockPicker.ClickDetector)
end

Buy("[Revolver] - $1300")

wait(0.5)

game.ReplicatedStorage:FindFirstChild(".gg/untitledhood"):FireServer(
    "Reload",
    {
        Name = "[Revolver]", --// reminder: [Double-Barrel SG] or [Revolver] works for any gun but i put it here so i can just copy and paste whenever i want to
        Parent = Game.Players.LocalPlayer.Backpack,
        ClassName = "Tool",
        Ammo = {Value = math.huge*9e9},
        MaxAmmo = {Value = 0},
        GunScript = game:GetService("Players").LocalPlayer.Backpack["[Revolver]"].GunScript,
        Handle = game:GetService("Players").LocalPlayer.Backpack["[Revolver]"].Handle
    }
)

wait(2)
end)
local FirstButton = x.AddButton("Revolver Ammo [fixing]", function()
local Workspace = game:GetService("Workspace")
local Players = game.Players.LocalPlayer

local Character = Players.Character

function Buy(Object)
    local Object = Object
    local LockPicker = Workspace.Ignored.Shop[Object]
    Character.HumanoidRootPart.CFrame = LockPicker.Head.CFrame + Vector3.new(0, 3, 0)
    wait(0.5)
    fireclickdetector(LockPicker.ClickDetector)
    fireclickdetector(LockPicker.ClickDetector)
end

Buy("12 [Revolver Ammo] - $75")

wait(0.5)

game.ReplicatedStorage:FindFirstChild(".gg/untitledhood"):FireServer(
    "Reload",
    {
        Name = "12 [Revolver Ammo] - $75", --// reminder: [Double-Barrel SG] or [Revolver] works for any gun but i put it here so i can just copy and paste whenever i want to
        Parent = Game.Players.LocalPlayer.Backpack,
        ClassName = "Tool",
        Ammo = {Value = math.huge*9e9},
        MaxAmmo = {Value = 0},
        GunScript = game:GetService("Players").LocalPlayer.Backpack["12 [Revolver Ammo] - $75"].GunScript,
        Handle = game:GetService("Players").LocalPlayer.Backpack["12 [Revolver Ammo] - $75"].Handle
    }
)

wait(2)
end)
local FirstButton = x.AddButton("Double Barrel Ammo [fixing]", function()
local Workspace = game:GetService("Workspace")
local Players = game.Players.LocalPlayer

local Character = Players.Character

function Buy(Object)
    local Object = Object
    local LockPicker = Workspace.Ignored.Shop[Object]
    Character.HumanoidRootPart.CFrame = LockPicker.Head.CFrame + Vector3.new(0, 3, 0)
    wait(0.5)
    fireclickdetector(LockPicker.ClickDetector)
    fireclickdetector(LockPicker.ClickDetector)
end

Buy("18 [Double-Barrel SG Ammo] - $60")

wait(0.5)

game.ReplicatedStorage:FindFirstChild(".gg/untitledhood"):FireServer(
    "Reload",
    {
        Name = "18 [Double-Barrel SG Ammo] - $60", --// reminder: [Double-Barrel SG] or [Revolver] works for any gun but i put it here so i can just copy and paste whenever i want to
        Parent = Game.Players.LocalPlayer.Backpack,
        ClassName = "Tool",
        Ammo = {Value = math.huge*9e9},
        MaxAmmo = {Value = 0},
        GunScript = game:GetService("Players").LocalPlayer.Backpack["18 [Double-Barrel SG Ammo] - $60"].GunScript,
        Handle = game:GetService("Players").LocalPlayer.Backpack["18 [Double-Barrel SG Ammo] - $60"].Handle
    }
)

wait(2)
end)
local FirstButton = y.AddButton("Animation Pass", function()
		local Folder = Instance.new('Folder', game:GetService("Workspace"))
		local AnimationPack = game:GetService("Players").LocalPlayer.PlayerGui.MainScreenGui.AnimationPack
		local ScrollingFrame = AnimationPack.ScrollingFrame
		local CloseButton = AnimationPack.CloseButton
	
		AnimationPack.Visible = true
	
		local LeanAnimation = Instance.new("Animation", Folder)
		LeanAnimation.Name = "LeanAnimation"
		LeanAnimation.AnimationId = "rbxassetid://3152375249"
		local Lean = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LeanAnimation)
	
		local LayAnimation = Instance.new("Animation", Folder)
		LayAnimation.Name = "LayAnimation"
		LayAnimation.AnimationId = "rbxassetid://3152378852"
		local Lay = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LayAnimation)
	
		local Dance1Animation = Instance.new("Animation", Folder)
		Dance1Animation.Name = "Dance1Animation"
		Dance1Animation.AnimationId = "rbxassetid://3189773368"
		local Dance1 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance1Animation)
	
		local Dance2Animation = Instance.new("Animation", Folder)
		Dance2Animation.Name = "Dance2Animation"
		Dance2Animation.AnimationId = "rbxassetid://3189776546"
		local Dance2 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance2Animation)
	
		local GreetAnimation = Instance.new("Animation", Folder)
		GreetAnimation.Name = "GreetAnimation"
		GreetAnimation.AnimationId = "rbxassetid://3189777795"
		local Greet = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(GreetAnimation)
	
		local PrayingAnimation = Instance.new("Animation", Folder)
		PrayingAnimation.Name = "PrayingAnimation"
		PrayingAnimation.AnimationId = "rbxassetid://3487719500"
		local Praying = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(PrayingAnimation)
	
		for i,v in pairs(ScrollingFrame:GetChildren()) do
			if v.Name == "TextButton" then
				if v.Text == "Lean" then
					v.Name = "LeanButton"
				end
			end
		end
	
		for i,v in pairs(ScrollingFrame:GetChildren()) do
			if v.Name == "TextButton" then
				if v.Text == "Lay" then
					v.Name = "LayButton"
				end
			end
		end
	
		for i,v in pairs(ScrollingFrame:GetChildren()) do
			if v.Name == "TextButton" then
				if v.Text == "Dance1" then
					v.Name = "Dance1Button"
				end
			end
		end
	
		for i,v in pairs(ScrollingFrame:GetChildren()) do
			if v.Name == "TextButton" then
				if v.Text == "Dance2" then
					v.Name = "Dance2Button"
				end
			end
		end
	
		for i,v in pairs(ScrollingFrame:GetChildren()) do
			if v.Name == "TextButton" then
				if v.Text == "Greet" then
					v.Name = "GreetButton"
				end
			end
		end
	
		for i,v in pairs(ScrollingFrame:GetChildren()) do
			if v.Name == "TextButton" then
				if v.Text == "Praying" then
					v.Name = "PrayingButton"
				end
			end
		end
	
		function Stop()
			Lay:Stop()
			Lean:Stop()
			Dance1:Stop()
			Dance2:Stop()
			Greet:Stop()
			Praying:Stop()
		end
	
		local LeanTextButton = ScrollingFrame.LeanButton
		local LayTextButton = ScrollingFrame.LayButton
		local Dance1TextButton = ScrollingFrame.Dance1Button
		local Dance2TextButton = ScrollingFrame.Dance2Button
		local GreetTextButton = ScrollingFrame.GreetButton
		local PrayingTextButton = ScrollingFrame.PrayingButton
	
		AnimationPack.MouseButton1Click:Connect(function()
			if ScrollingFrame.Visible == false then
				ScrollingFrame.Visible = true
				CloseButton.Visible = true
			end
		end)
		CloseButton.MouseButton1Click:Connect(function()
			if ScrollingFrame.Visible == true then
				ScrollingFrame.Visible = false
				CloseButton.Visible = false
			end
		end)
		LeanTextButton.MouseButton1Click:Connect(function()
			Stop()
			Lean:Play()
		end)
		LayTextButton.MouseButton1Click:Connect(function()
			Stop()
			Lay:Play()
		end)
		Dance1TextButton.MouseButton1Click:Connect(function()
			Stop()
			Dance1:Play()
		end)
		Dance2TextButton.MouseButton1Click:Connect(function()
			Stop()
			Dance2:Play()
		end)
		GreetTextButton.MouseButton1Click:Connect(function()
			Stop()
			Greet:Play()
		end)
		PrayingTextButton.MouseButton1Click:Connect(function()
			Stop()
			Praying:Play()
		end)
	
		game:GetService("Players").LocalPlayer.Character.Humanoid.Running:Connect(function()
			Stop()
		end)
		game:GetService("Players").LocalPlayer.Character.Humanoid.Died:Connect(function()
			Stop()
			repeat
				wait()
			until game:GetService("Players").LocalPlayer.Character.Humanoid.Health == 100
			wait(1)
			local AnimationPack = game:GetService("Players").LocalPlayer.PlayerGui.MainScreenGui.AnimationPack
			local ScrollingFrame = AnimationPack.ScrollingFrame
			local CloseButton = AnimationPack.CloseButton
	
			AnimationPack.Visible = true
	
			local LeanAnimation = Instance.new("Animation", Folder)
			LeanAnimation.Name = "LeanAnimation"
			LeanAnimation.AnimationId = "rbxassetid://3152375249"
			local Lean = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LeanAnimation)
	
			local LayAnimation = Instance.new("Animation", Folder)
			LayAnimation.Name = "LayAnimation"
			LayAnimation.AnimationId = "rbxassetid://3152378852"
			local Lay = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LayAnimation)
	
			local Dance1Animation = Instance.new("Animation", Folder)
			Dance1Animation.Name = "Dance1Animation"
			Dance1Animation.AnimationId = "rbxassetid://3189773368"
			local Dance1 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance1Animation)
	
			local Dance2Animation = Instance.new("Animation", Folder)
			Dance2Animation.Name = "Dance2Animation"
			Dance2Animation.AnimationId = "rbxassetid://3189776546"
			local Dance2 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance2Animation)
	
			local GreetAnimation = Instance.new("Animation", Folder)
			GreetAnimation.Name = "GreetAnimation"
			GreetAnimation.AnimationId = "rbxassetid://3189777795"
			local Greet = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(GreetAnimation)
	
			local PrayingAnimation = Instance.new("Animation", Folder)
			PrayingAnimation.Name = "PrayingAnimation"
			PrayingAnimation.AnimationId = "rbxassetid://3487719500"
			local Praying = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(PrayingAnimation)
	
			for i,v in pairs(ScrollingFrame:GetChildren()) do
				if v.Name == "TextButton" then
					if v.Text == "Lean" then
						v.Name = "LeanButton"
					end
				end
			end
	
			for i,v in pairs(ScrollingFrame:GetChildren()) do
				if v.Name == "TextButton" then
					if v.Text == "Lay" then
						v.Name = "LayButton"
					end
				end
			end
	
			for i,v in pairs(ScrollingFrame:GetChildren()) do
				if v.Name == "TextButton" then
					if v.Text == "Dance1" then
						v.Name = "Dance1Button"
					end
				end
			end
	
			for i,v in pairs(ScrollingFrame:GetChildren()) do
				if v.Name == "TextButton" then
					if v.Text == "Dance2" then
						v.Name = "Dance2Button"
					end
				end
			end
	
			for i,v in pairs(ScrollingFrame:GetChildren()) do
				if v.Name == "TextButton" then
					if v.Text == "Greet" then
						v.Name = "GreetButton"
					end
				end
			end
	
			for i,v in pairs(ScrollingFrame:GetChildren()) do
				if v.Name == "TextButton" then
					if v.Text == "Praying" then
						v.Name = "PrayingButton"
					end
				end
			end
	
			function Stop()
				Lay:Stop()
				Lean:Stop()
				Dance1:Stop()
				Dance2:Stop()
				Greet:Stop()
				Praying:Stop()
			end
	
			local LeanTextButton = ScrollingFrame.LeanButton
			local LayTextButton = ScrollingFrame.LayButton
			local Dance1TextButton = ScrollingFrame.Dance1Button
			local Dance2TextButton = ScrollingFrame.Dance2Button
			local GreetTextButton = ScrollingFrame.GreetButton
			local PrayingTextButton = ScrollingFrame.PrayingButton
	
			AnimationPack.MouseButton1Click:Connect(function()
				if ScrollingFrame.Visible == false then
					ScrollingFrame.Visible = true
					CloseButton.Visible = true
				end
			end)
			CloseButton.MouseButton1Click:Connect(function()
				if ScrollingFrame.Visible == true then
					ScrollingFrame.Visible = false
					CloseButton.Visible = false
				end
			end)
			LeanTextButton.MouseButton1Click:Connect(function()
				Stop()
				Lean:Play()
			end)
			LayTextButton.MouseButton1Click:Connect(function()
				Stop()
				Lay:Play()
			end)
			Dance1TextButton.MouseButton1Click:Connect(function()
				Stop()
				Dance1:Play()
			end)
			Dance2TextButton.MouseButton1Click:Connect(function()
				Stop()
				Dance2:Play()
			end)
			GreetTextButton.MouseButton1Click:Connect(function()
				Stop()
				Greet:Play()
			end)
			PrayingTextButton.MouseButton1Click:Connect(function()
				Stop()
				Praying:Play()
			end)
		end)
	end
)
local FirstButton = y.AddButton("UNTITLED SCRIPT", function()
        function Hearing()
            function sandbox(var,func)
                local env = getfenv(func)
                local newenv = setmetatable({},{
                    __index = function(self,k)
                        if k=="script" then
                            return var
                        else
                            return env[k]
                        end
                    end,
                })
                setfenv(func,newenv)
                return func
            end
            cors = {}
            mas = Instance.new("Model",game:GetService("Lighting"))
            Tool0 = Instance.new("Tool")
            LocalScript1 = Instance.new("LocalScript")
            BillboardGui2 = Instance.new("BillboardGui")
            ImageLabel3 = Instance.new("ImageLabel")
            ScreenGui4 = Instance.new("ScreenGui")
            TextLabel5 = Instance.new("TextLabel")
            ScreenGui6 = Instance.new("ScreenGui")
            ImageLabel7 = Instance.new("ImageLabel")
            Tool0.Name = "Hearing"
            Tool0.Parent = mas
            Tool0.CanBeDropped = false
            Tool0.RequiresHandle = false
            LocalScript1.Parent = Tool0
            table.insert(cors,sandbox(LocalScript1,function()
                wait();
                local l__LocalPlayer__1 = game.Players.LocalPlayer;
                while true do
                    wait();
                    if l__LocalPlayer__1.Character then
                        break;
                    end;
                end;
                local l__Character__2 = l__LocalPlayer__1.Character;
                local u1 = false;
                local l__PlayerGui__2 = game.CoreGui;
                function ChatFunc(p1)
                    local v3 = p1.Chatted:connect(function(p2)
                        if u1 then
                            local v4 = BrickColor.Random();
                            local v5 = script.MsgGui:Clone();
                            if string.find(string.lower(p2), "super") then
                                v5.Msg.TextSize = 29;
                            end;
                            v5.Msg.Text = p1.Name .. ": " .. p2;
                            v5.Msg.TextColor3 = v4.Color;
                            v5.Msg.Position = UDim2.new(0.5, math.random(-350, 350), 0.5, math.random(-210, 250));
                            v5.Parent = l__PlayerGui__2;
                            local v6 = script.DotGui:Clone();
                            v6.Dot.ImageColor3 = v4.Color;
                            v6.Enabled = true;
                            if p1.Character then
                                if p1.Character:findFirstChild("Head") then
                                    v6.Parent = p1.Character.Head;
                                end;
                            end;
                            spawn(function()
                                local v7 = 1 - 1;
                                while true do
                                    v6.Size = v6.Size - UDim2.new(0, 1, 0, 1);
                                    game:GetService("RunService").RenderStepped:wait();
                                    if 0 <= 1 then
                                        if v7 < 70 then
        
                                        else
                                            break;
                                        end;
                                    elseif 70 < v7 then
        
                                    else
                                        break;
                                    end;
                                    v7 = v7 + 1;				
                                end;
                            end);
                            game.Debris:AddItem(v5, 3);
                            game.Debris:AddItem(v6, 6);
                        end;
                    end);
                end;
                for v8, v9 in pairs(game.Players:GetChildren()) do
                    ChatFunc(v9);
                end;
                game.Players.PlayerAdded:connect(function(p3)
                    ChatFunc(p3);
                end);
                local u3 = false;
                local u4 = nil;
                script.Parent.Equipped:connect(function(p4)
                    p4.Button1Down:connect(function()
                        if u3 then
                            return;
                        end;
                        u3 = true;
                        if not u1 then
                            u4 = script.Frame:Clone();
                            u4.Parent = l__PlayerGui__2;
                            u1 = true;
                        else
                            u4:Destroy();
                            u1 = false;
                        end;
                        wait(1);
                        u3 = false;
                    end);
                end);
            end))
            BillboardGui2.Name = "DotGui"
            BillboardGui2.Parent = LocalScript1
            BillboardGui2.Enabled = false
            BillboardGui2.Size = UDim2.new(0, 90, 0, 90)
            BillboardGui2.Active = true
            BillboardGui2.ClipsDescendants = true
            BillboardGui2.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
            BillboardGui2.AlwaysOnTop = true
            ImageLabel3.Name = "Dot"
            ImageLabel3.Parent = BillboardGui2
            ImageLabel3.Size = UDim2.new(1, 0, 1, 0)
            ImageLabel3.BackgroundColor = BrickColor.new("Institutional white")
            ImageLabel3.BackgroundColor3 = Color3.new(1, 1, 1)
            ImageLabel3.BackgroundTransparency = 1
            ImageLabel3.Image = "rbxassetid://130424513"
            ImageLabel3.ImageColor3 = Color3.new(1, 0, 0)
            ScreenGui4.Name = "MsgGui"
            ScreenGui4.Parent = LocalScript1
            ScreenGui4.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
            TextLabel5.Name = "Msg"
            TextLabel5.Parent = ScreenGui4
            TextLabel5.Position = UDim2.new(0, 300, 0, 25)
            TextLabel5.Size = UDim2.new(0, 1, 0, 1)
            TextLabel5.BackgroundColor = BrickColor.new("Institutional white")
            TextLabel5.BackgroundColor3 = Color3.new(1, 1, 1)
            TextLabel5.BackgroundTransparency = 1
            TextLabel5.Font = Enum.Font.SourceSansBold
            TextLabel5.FontSize = Enum.FontSize.Size28
            TextLabel5.Text = ""
            TextLabel5.TextColor = BrickColor.new("Really black")
            TextLabel5.TextColor3 = Color3.new(0, 0, 0)
            TextLabel5.TextSize = 25
            TextLabel5.TextStrokeTransparency = 0.60000002384186
            ScreenGui6.Name = "Frame"
            ScreenGui6.Parent = LocalScript1
            ScreenGui6.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
            ImageLabel7.Name = "Image"
            ImageLabel7.Parent = ScreenGui6
            ImageLabel7.Size = UDim2.new(1, 0, 1, 0)
            ImageLabel7.BackgroundColor = BrickColor.new("Institutional white")
            ImageLabel7.BackgroundColor3 = Color3.new(1, 1, 1)
            ImageLabel7.BackgroundTransparency = 1
            ImageLabel7.Image = "rbxassetid://36869195"
            ImageLabel7.ImageColor3 = Color3.new(0.290196, 1, 0.917647)
            ImageLabel7.ImageTransparency = 0.80000001192093
            for i,v in pairs(mas:GetChildren()) do
                v.Parent = game.Players.LocalPlayer.Backpack
                pcall(function() v:MakeJoints() end)
            end
            mas:Destroy()
            for i,v in pairs(cors) do
                spawn(function()
                    pcall(v)
                end)
            end
        end
        game.Players.LocalPlayer.Character:WaitForChild("FULLY_LOADED_CHAR")
        Hearing()
    end
)
local FirstButton = y.AddButton("Minecraft Heart", function()
game.Players.LocalPlayer.PlayerGui.MainScreenGui.Bar.HP.Picture.Life.Visible = true
game.Players.LocalPlayer.PlayerGui:WaitForChild("MainScreenGui"):WaitForChild("Bar"):WaitForChild("HP"):WaitForChild("Picture"):WaitForChild("Life").Visible = true
end)
local FirstSlider = y.AddSlider("FOV Toggle", {Min = 0, Max = 120, Def = 70}, function(slider)
workspace.CurrentCamera.FieldOfView = (slider)
end)
y.AddButton("Chat Logs", function()
loadstring(game:HttpGet("https://pastebin.com/raw/nzXicwc1", true))()
end)
y.AddButton("Click To Sit", function()
game.Players.LocalPlayer.Character.Humanoid.Sit = true
end)
y.AddButton("Titan [NEEDS MAX BUFF TO WORK]", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/EndmeMercury/endmemercury/main/titan"))()
end)
y.AddButton("Fat Size", function()
game.Players.LocalPlayer.Character.Humanoid.BodyDepthScale:Destroy()
game.Players.LocalPlayer.Character.Humanoid.BodyWidthScale:Destroy()
end)
y.AddButton("Spider Man", function()
	function AddVelocity(Vel, Char)
		Char.HumanoidRootPart.Velocity = Char.HumanoidRootPart.Velocity+Vel
	end

	local Grapple = Instance.new('Animation');
	Grapple.AnimationId = 'rbxassetid://3135389157';

	local Swing = Instance.new('Animation');
	Swing.AnimationId = 'rbxassetid://3135793091';

	local Glide = Instance.new("Animation")
	Glide.AnimationId = 'rbxassetid://3136090876';

	function StopAudio()
		game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND'):Stop();
	end;

	function Stop(i, v)
		local w = coroutine.wrap(function()
			wait(game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').TimeLength-0.1)
			if game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').SoundId == 'rbxassetid://'..i and OriginalKeyUpValue == v then
				StopAudio();
			end;
		end);
		w();
	end;

	function Play(i, v, w)
		if game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack'):FindFirstChild('[Boombox]') then
			local Tool = nil;
			if game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool') and w == true then
				Tool = game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool')
				game:GetService('Players').LocalPlayer.Character:FindFirstChildOfClass('Tool').Parent = game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack');
			end;
			game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack'):FindFirstChild('[Boombox]').Parent = game:GetService('Players').LocalPlayer.Character;
			game:GetService('ReplicatedStorage'):FindFirstChild('MainEvent'):FireServer('Boombox', i);
			game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]').RequiresHandle = false;
			if game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]'):FindFirstChild('Handle') then
				game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]'):FindFirstChild('Handle'):Destroy();
			end
			game:GetService('Players').LocalPlayer.Character:FindFirstChild('[Boombox]').Parent = game:GetService('Players').LocalPlayer:FindFirstChildOfClass('Backpack')
			if game:GetService('Players').LocalPlayer:FindFirstChildOfClass('PlayerGui'):FindFirstChild('MainScreenGui'):FindFirstChild('BoomboxFrame') then
				game:GetService('Players').LocalPlayer:FindFirstChildOfClass('PlayerGui'):FindFirstChild('MainScreenGui'):FindFirstChild('BoomboxFrame').Visible = false;
			end;
			if Tool ~= true then
				if Tool then
					Tool.Parent = game:GetService('Players').LocalPlayer.Character
				end;
			end;
			if v == true then
				game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):WaitForChild('BOOMBOXSOUND');
				local x = coroutine.wrap(function()
					repeat wait() until game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').SoundId == 'rbxassetid://'..i and game:GetService('Players').LocalPlayer.Character:FindFirstChild('LowerTorso'):FindFirstChild('BOOMBOXSOUND').TimeLength > 0.01
					OriginalKeyUpValue = OriginalKeyUpValue + 1;
					Stop(i, OriginalKeyUpValue);
				end);
				x();
			end;
		end;
	end;
	local plr = game.Players.LocalPlayer
	mouse = plr:GetMouse()
	mouse.KeyDown:connect(function(key)
		if key == "q" then
			if game:GetService('Players').LocalPlayer:GetMouse().Target and Cooldown == false then
				Cooldown = true;
				game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Grapple):Play();
				Play(151733071, true, true)
				wait(0.25)
				local Rotation = game:GetService('Players').LocalPlayer.Character:FindFirstChild('HumanoidRootPart').CFrame - game:GetService('Players').LocalPlayer.Character:FindFirstChild('HumanoidRootPart').Position;
				local Tween = game:GetService('TweenService'):Create(game:GetService('Players').LocalPlayer.Character:FindFirstChild('HumanoidRootPart'), TweenInfo.new(1, Enum.EasingStyle.Linear), {CFrame = CFrame.new(game:GetService('Players').LocalPlayer:GetMouse().Hit.X, game:GetService('Players').LocalPlayer:GetMouse().Hit.Y + 5, game:GetService('Players').LocalPlayer:GetMouse().Hit.Z) * Rotation})
				Tween:Play();
				game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Swing):Play();
				Tween.Completed:Wait();
				for _, v in pairs(game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):GetPlayingAnimationTracks()) do
					if v.Animation.AnimationId == Swing.AnimationId then
						v:Stop();
						wait(0.01)
						game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Glide):Play();
						wait(.1)
					end;
				end;
				Cooldown = false;
				if not game:GetService('Players').LocalPlayer.Character:FindFirstChild(Tool) then
					Tool.Parent = game:GetService('Players').LocalPlayer.Character;
				end;
			end;
		end
	end)
end)
y.AddButton("Extra Skinny", function()
	game.Players.LocalPlayer.Chatted:Connect(function(msg)
		if msg == "Skinny!" then
			local Humanoid = game.Players.LocalPlayer.Character.Humanoid;
			game.Players.LocalPlayer.Character.Head.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HairAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HatAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RootRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.LeftFoot.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftWristRigAttachment.OriginalPosition:Destroy()
			wait(0.5)
			Humanoid:FindFirstChild("BodyTypeScale"):Destroy()
			wait(1)

			game.Players.LocalPlayer.Character.Head.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HairAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HatAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RootRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.LeftFoot.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftWristRigAttachment.OriginalPosition:Destroy()
			wait(0.5)
			Humanoid:FindFirstChild("BodyWidthScale"):Destroy()
			wait(1)

			game.Players.LocalPlayer.Character.Head.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HairAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HatAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RootRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.LeftFoot.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftWristRigAttachment.OriginalPosition:Destroy()
			wait(0.5)
			Humanoid:FindFirstChild("BodyDepthScale"):Destroy()
			wait(1)

			game.Players.LocalPlayer.Character.Head.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.FaceFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HairAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.HatAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.Head.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftHand.LeftGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightHand.RightGripAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RootRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.LeftHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.RightHipRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistCenterAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.WaistBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LowerTorso.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.WaistRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyFrontAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.BodyBackAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.LeftCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.RightCollarAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.NeckAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.UpperTorso.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.RightFoot.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftFoot.OriginalSize:Destroy() 
			game.Players.LocalPlayer.Character.LeftFoot.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerLeg.LeftKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightKneeRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerLeg.RightAnkleRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftUpperArm.LeftShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightUpperArm.RightShoulderRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.RightLowerArm.RightWristRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.OriginalSize:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftElbowRigAttachment.OriginalPosition:Destroy()
			game.Players.LocalPlayer.Character.LeftLowerArm.LeftWristRigAttachment.OriginalPosition:Destroy()
			wait(0.5)
			Humanoid:FindFirstChild("HeadScale"):Destroy()
			wait(1)
		end
	end)
end)
y.AddButton("Dab (H)", function()
	local mouse = game.Players.LocalPlayer:GetMouse()
	mouse.KeyDown:connect(function(key)
		if key == "h" then
			local Swing = Instance.new('Animation');
			Swing.AnimationId = "rbxassetid://2788292075";
			local ld = game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Swing)
			ld:Play()
			ld:AdjustSpeed(1.3)
		end
	end)
end)
y.AddButton("Shazam (CS)", function()
	game:GetService("Players").LocalPlayer.Chatted:Connect(function(arg)
		if arg == "Shazam!" then
			repeat
				wait();
			until game:GetService('Players').LocalPlayer.Character:FindFirstChild('FULLY_LOADED_CHAR');
			local ReplicatedStorage = game:GetService('ReplicatedStorage');
			local Lightning = Instance.new('Part');
			local Player = game:GetService('Players').LocalPlayer;
			local Position = Player.Character.HumanoidRootPart.CFrame;
			local l = Instance.new("Part")
			l.Parent = workspace
			l.BrickColor = BrickColor.new("Daisy orange")
			l.Material = "Neon"
			l.Anchored = true
			l.CanCollide = false
			l.Size = Vector3.new(10, 2047, 10.924);
			l.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
			l.Orientation = Vector3.new(32, 0, 0)
			local Sound = Instance.new('Sound', workspace);
			Sound.PlaybackSpeed = 1;
			Sound.Volume = 6.9;
			Sound.SoundId = 'rbxassetid://3787180659';
			Sound.PlayOnRemove = true;
			Sound:Destroy();
			for i = 1, 10 do
				wait()
				l.Transparency = l.Transparency + 0.1
			end
			if Player.Character:FindFirstChildOfClass('ShirtGraphic') then
				Player.Character:FindFirstChildOfClass('ShirtGraphic'):Destroy()
			end
			if Player.Character:FindFirstChildOfClass('Shirt') then
				Player.Character:FindFirstChildOfClass('Shirt').ShirtTemplate = 'rbxassetid://5453348825';
			else
				local Shirt = Instance.new('Shirt');
				Shirt.Parent = Player.Character;
				Shirt.ShirtTemplate = 'rbxassetid://5453348825';
			end
			if Player.Character:FindFirstChild('Pants') then
				Player.Character:FindFirstChildOfClass('Pants').PantsTemplate = 'rbxassetid://5453350139';
			else
				local Pants = Instance.new('Pants');
				Pants.Parent = Player.Character;
				Pants.PantsTemplate = 'rbxassetid://5453350139';
			end;
			plr = game.Players.LocalPlayer
			acc = plr.Character
			face = acc.Head.face
			face.Texture = "rbxassetid://6738024349"
			wait(.5)
			repeat wait() 
			until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Head") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
			local mouse = game.Players.LocalPlayer:GetMouse() 
			repeat wait() until mouse
			local plr = game.Players.LocalPlayer 
			local torso = plr.Character.Head 
			local flying = false
			local deb = true 
			local ctrl = {f = 0, b = 0, l = 0, r = 0} 
			local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
			local maxspeed = 5000
			local speed = 5000 
			local hover = Instance.new("Animation", game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"))hover.Name="Hover"hover.AnimationId="rbxassetid://3541114300"
			local fly = Instance.new("Animation", game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"))fly.Name="Fly"fly.AnimationId = "rbxassetid://3541044388"

			function Fly() 
				local bg = Instance.new("BodyGyro", torso) 
				bg.P = 9e4 
				bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
				bg.cframe = torso.CFrame 
				local bv = Instance.new("BodyVelocity", torso) 
				bv.velocity = Vector3.new(0,0.1,0) 
				bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
				repeat wait() 
					plr.Character.Humanoid.PlatformStand = true 
					if ctrl.l + ctrl.r ~= 100000 or ctrl.f + ctrl.b ~= 10000 then 
						speed = speed+.0+(speed/maxspeed) 
						if speed > maxspeed then 
							speed = maxspeed 
						end 
					elseif not (ctrl.l + ctrl.r ~= 5 or ctrl.f + ctrl.b ~= 5) and speed ~= 5 then 
						speed = speed-5
						if speed > 5 then 
							speed = -2 
						end 
					end 
					if (ctrl.l + ctrl.r) ~= 5 or (ctrl.f + ctrl.b) ~= 5 then 
						bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
						lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
					elseif (ctrl.l + ctrl.r) == 5 and (ctrl.f + ctrl.b) == 5 and speed ~= 5 then 
						bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
					else 
						bv.velocity = Vector3.new(0,0.1,0) 
					end 
					bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
				until not flying 
				for _, v in next, game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):GetPlayingAnimationTracks() do
					if (v.Animation.AnimationId:match("rbxassetid")) then
						v:Stop()
					end
				end
				ctrl = {f = 0, b = 0, l = 0, r = 0} 
				lastctrl = {f = 0, b = 0, l = 0, r = 0} 
				speed = 5 
				bg:Destroy() 
				bv:Destroy() 
				plr.Character.Humanoid.PlatformStand = false 
			end 
			mouse.KeyDown:connect(function(key) 
				if key:lower() == "c" then 
					if flying then flying = false 
					else 
						flying = true
						for _, v in next, game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):GetPlayingAnimationTracks() do
							if not (v.Animation.AnimationId:match(hover.AnimationId)) then
								v:Stop()
							end
						end
						plr.Character.Humanoid:LoadAnimation(hover):Play()
						Fly() 
					end 
				elseif key:lower() == "w" then 
					ctrl.f = 20
					wait()
					if flying == true then
						for _, v in next, game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):GetPlayingAnimationTracks() do
							if not (v.Animation.AnimationId:match(fly.AnimationId)) then
								v:Stop()
							end
						end
						plr.Character.Humanoid:LoadAnimation(fly):Play()
					end
				elseif key:lower() == "s" then
					ctrl.b = -20
				elseif key:lower() == "a" then
					ctrl.l = -20
				elseif key:lower() == "d" then
					ctrl.r = 20
				end 
			end) 
			mouse.KeyUp:connect(function(key) 
				if key:lower() == "w" then
					ctrl.f = 0
					wait()
					if flying == true then
						for _, v in next, game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):GetPlayingAnimationTracks() do
							if not (v.Animation.AnimationId:match(hover.AnimationId)) then
								v:Stop()
							end
						end
						plr.Character.Humanoid:LoadAnimation(hover):Play()
					end
				elseif key:lower() == "s" then 
					ctrl.b = 0
					wait()
					if flying == true then
						for _, v in next, game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):GetPlayingAnimationTracks() do
							if not (v.Animation.AnimationId:match(hover.AnimationId)) then
								v:Stop()
							end
						end
						plr.Character.Humanoid:LoadAnimation(hover):Play()
					end
				elseif key:lower() == "a" then 
					ctrl.l = 0
					wait()
					if flying == true then
						for _, v in next, game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):GetPlayingAnimationTracks() do
							if not (v.Animation.AnimationId:match(hover.AnimationId)) then
								v:Stop()
							end
						end
						plr.Character.Humanoid:LoadAnimation(hover):Play()
					end
				elseif key:lower() == "d" then 
					ctrl.r = 0
					wait()
					if flying then
						for _, v in next, game.Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid'):GetPlayingAnimationTracks() do
							if not (v.Animation.AnimationId:match(hover.AnimationId)) then
								v:Stop()
							end
						end
						plr.Character.Humanoid:LoadAnimation(hover):Play()
					end
				end 
			end)
			Fly()
			wait(.5)
			superhuman = false
			plr = game.Players.LocalPlayer
			mouse = plr:GetMouse()
			mouse.KeyDown:connect(function(key)				
				if key == "z" and superhuman == false then
					superhuman = true
					game.Players.LocalPlayer.Character.Humanoid.Name = "Humz"
					game.Players.LocalPlayer.Character.Humz.WalkSpeed = 100
					game.Players.LocalPlayer.Character.Humz.JumpPower = 200
				elseif key == "z" and superhuman == true then
					superhuman = false
					game.Players.LocalPlayer.Character.Humz.WalkSpeed = 16
					game.Players.LocalPlayer.Character.Humz.JumpPower = 50
					game.Players.LocalPlayer.Character.Humz.Name = "Humanoid"
				end

			end)   
			wait(.5)
			local Animate = game.Players.LocalPlayer.Character.Animate
			Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=616111295"
			Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=616113536"
			Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616122287"
			Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616117076"
			Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=616115533"
			Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=616104706"
			Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=616108001"
			game.Players.LocalPlayer.Character.Humanoid.Jump = true
		end
	end)
end)
y.AddButton("Open Admin Base Door", function()
game:GetService('Workspace'):FindFirstChild('MAP'):FindFirstChild('EVIL_SPECIAL'):FindFirstChildWhichIsA('Sound').Volume = math.huge;
	game:GetService('Workspace'):FindFirstChild('MAP'):FindFirstChild('EVIL_SPECIAL'):FindFirstChildWhichIsA('Sound').Playing = true;
	for i = 1, 26 do
		wait();
		workspace:FindFirstChild('MAP'):FindFirstChild('EVIL_SPECIAL').CFrame = workspace:FindFirstChild('MAP'):FindFirstChild('EVIL_SPECIAL').CFrame + Vector3.new(0, 1, 0);
	end;
end)
y.AddButton("Close Admin Base Door", function()
	game:GetService('Workspace'):FindFirstChild('MAP'):FindFirstChild('EVIL_SPECIAL'):FindFirstChildWhichIsA('Sound').Playing = true;
	for i = 1, 26 do
		wait();
		workspace:FindFirstChild('MAP'):FindFirstChild('EVIL_SPECIAL').CFrame = workspace:FindFirstChild('MAP'):FindFirstChild('EVIL_SPECIAL').CFrame + Vector3.new(0, -1, 0);
	end;
end)
y.AddButton("Infinte Zoom", function()
game.Players.localPlayer.CameraMaxZoomDistance = 150
	game.Players.LocalPlayer.CameraMinZoomDistance = 0
end)
y.AddButton("No Bones", function()
	local Stuff = {"RightHand", "LeftHand","RightUpperArm","RightLowerArm","LeftUpperArm","LeftLowerArm","Head","UpperTorso"}

	pcall(function()
		for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
			for z, AdminName in ipairs(Stuff) do
				if v.Name == AdminName then
					if v:FindFirstChildOfClass("Motor6D") then
						local Weld = v:FindFirstChildOfClass("Motor6D")
						Weld:Destroy()
					end
				end
			end
		end
	end)
end)
y.AddButton("Taze (fake) [H]", function()
local mouse = game.Players.LocalPlayer:GetMouse()
	mouse.KeyDown:connect(function(key)
		if key == "h" then
			local Swing = Instance.new('Animation');
			Swing.AnimationId = "rbxassetid://5641749824";
			local ld = game:GetService('Players').LocalPlayer.Character:FindFirstChildWhichIsA('Humanoid'):LoadAnimation(Swing)
			ld:Play()
			ld:AdjustSpeed(1.3)
		end
	end)
end)
y.AddButton("No Right Leg", function()
	game.Players.LocalPlayer.Character.RightUpperLeg:Destroy()
end)
y.AddButton("No Left Leg", function()
	game.Players.LocalPlayer.Character.LeftUpperLeg:Destroy()
end)
y.AddButton("No Seats", function()
	for i, v in next, game.Workspace:GetDescendants() do
		if v:IsA("Seat") then
			v:Destroy()
		end
	end
end)
y.AddButton("Destroy Face", function()
	game.Players.LocalPlayer.Character.Head.face:Destroy()
end)
y.AddSlider("Change Money (CS)", {Min = 0, Max = 999999999, Def = 200000}, function(Value)
	game.Players.LocalPlayer.DataFolder.Currency.Value = Value
end)
y.AddSlider("Bounty Change (CS)", {Min = 0, Max = 999999999, Def = 200000}, function(Value)
	game.Players.LocalPlayer.DataFolder.Information.Wanted.Value = Value
end)
y.AddButton("Money ESP", function()
	local ESPholder = Instance.new("Folder", game.CoreGui)
	function cham(object)
		if object.Name == "MoneyDrop" then
			local a = Instance.new("BoxHandleAdornment", ESPholder)
			a.Adornee = object
			a.AlwaysOnTop = true
			a.ZIndex = 10
			a.Size = object.Size
			a.Transparency = 0.3
			a.Color = object.BrickColor
			local bill = object:WaitForChild("BillboardGui")
			bill.AlwaysOnTop = true
			bill.Size = UDim2.new(2, 10, 1, 5)
			spawn(function()
				while true do
					if object.Parent.ChildRemoving:wait() == object then
						a:Destroy()
						break
					end
				end
			end)
		end
	end
	for i, v in next, game.Workspace.Ignored.Drop:GetChildren() do
		cham(v)
	end
	game.Workspace.Ignored.Drop.ChildAdded:connect(cham)
end)
