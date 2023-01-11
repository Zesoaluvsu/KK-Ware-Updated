
game.StarterGui:SetCore("SendNotification",  {
 Title = "Executed.";
 Text = "My Disc: 0001#4349";
 Icon = "http://www.roblox.com/asset/?id=21";
 Duration = 999999999;
 Button1 = "Close";
 Button2 = "W";
 Button3 = "W";
 Callback = NotificationBindable;
}
)
local UILibrary = loadstring(game:HttpGet("https://pastebin.com/raw/V1ca2q9s"))()

local MainUI = UILibrary.Load("KK Ware - KK's Script Hub")
local FirstPage = MainUI.AddPage("Aiming")
local SecondPage = MainUI.AddPage("IGNORE")
local ThirdPage = MainUI.AddPage("Rich Stuff")
local FourthPage = MainUI.AddPage("Anims")
local FifthPage = MainUI.AddPage("Combat")



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
local FirstButton = FirstPage.AddButton("Dot Lock (E)", function()
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
local FifthButton = FifthPage.AddButton("Force Reset (O)", function()
	local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://413861777"
	sound.Parent = game:GetService("SoundService")
	sound:Play()
local Tool = script.Parent
local mouse = game.Players.LocalPlayer:GetMouse()

function onKeyDown(key)
 if (key~=nil) then
  key = key:lower()
  if (key=="o")  then
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
local FirstButton = FifthPage.AddButton("Infinite Jump", function()
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
