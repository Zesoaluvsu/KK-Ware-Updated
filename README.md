--KK WARE ON TOP
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("KK Ware.cc - KK's Script Hub", "BloodTheme")
    -- MAIN
    local Main = Window:NewTab("Main")
    local MainSection = Main:NewSection("Aimlocks")


    MainSection:NewButton("OP Aimlock", "Aimbot😍", function()
        loadstring(game:HttpGet('https://pastebin.com/raw/nRMcav1d'))()
    end)
    
        MainSection:NewButton("Blue Dot-lock", "Blue lock", function()
        loadstring(game:HttpGet('https://pastebin.com/raw/qk8fSixv'))()
    end)

    MainSection:NewButton("Silent aim", "Helps you with aim", function()
        loadstring(game:HttpGet('https://pastebin.com/raw/NfnHq619'))()
    end)

 MainSection:NewButton("KK's Personal Dot-lock", "KEYBIND = P", function()
        loadstring(game:HttpGet('https://pastebin.com/raw/ESM7wC6x'))()
 end)

     MainSection:NewButton("Valiant's Aimlock", "KEYBIND = T", function()
        loadstring(game:HttpGet('https://pastebin.com/raw/XZM3bTF5'))()
    end)

	     MainSection:NewButton("AntiLock", "Stop the lockers", function()
        loadstring(game:HttpGet('https://pastebin.com/raw/LQCj3SMV'))()
    end)




	    --LOCAL PLAYER
    local Player = Window:NewTab("Player")
    local PlayerSection = Player:NewSection("Player")

    PlayerSection:NewButton("FLY (X)", "Fly around with no limits.", function(s)
        loadstring(game:HttpGet("https://pastebin.com/raw/sUA9m6M6"))()
    end)

    PlayerSection:NewSlider("Walkspeed", "SPEED!!", 500, 16, function(s)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
    end)

    PlayerSection:NewSlider("Jumppower", "JUMP HIGH!!", 350, 50, function(s)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
    end)

    PlayerSection:NewButton("Da Mimic", "Keys: X B C T", function()
        loadstring(game:HttpGet('https://pastebin.com/raw/SV0TPjPW'))()
    end)

PlayerSection:NewButton("Skinny God Mode", "REJOIN AND EXECUTE QUICK OR IT WONT WORK.", function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/pixelheadx/godv3Polakya/main/README.md"))();
end)


PlayerSection:NewButton("Korblox", "only you can see it", function()
        local character = game.Players.LocalPlayer.Character
character.RightFoot.Transparency = "1"
character.RightUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
character.RightUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
character.RightLowerLeg.MeshId = "http://www.roblox.com/asset/?id=902942093"
character.RightLowerLeg.Transparency = "1"
end)

	    --Other
    local Other = Window:NewTab("Other")
    local OtherSection = Other:NewSection("Other")

    OtherSection:NewButton("Chat Spoofer", "Put other words in pepole's mouth", function()
        loadstring(game:HttpGet(('https://pastebin.com/raw/djBfk8Li'),true))()
    end)

    OtherSection:NewButton("Da Hood Crasher [FE]", "USE THIS IF YOU WANT TO DUPE", function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/BetterDaHood/BetterDaHoodCrasher/main/Crash'))()
    end)

	   OtherSection:NewButton("Chat Bypasser [FE]", "curse", function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/daddysyn/synergy/additional/betterbypasser",true))()
    end)
    
    	   OtherSection:NewButton("Bag All [FE]", "bag everyone up", function()
game.StarterGui:SetCore("SendNotification", {Title = "HSBC", Text = "Bag-All Activado. Solo se puede desactivar con rejoin jijijija", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "Okay!"})

local bag = true
local takingbag = true
local Plr = game.Players.LocalPlayer
repeat wait(1)
    if game.Players.LocalPlayer.Character:FindFirstChild("[BrownBag]") == nil then
        repeat
            takingbag = true
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-314.580566, 51.1788902, -727.484558)
            wait()
            fireclickdetector(workspace.Ignored.Shop["[BrownBag] - $25"].ClickDetector)
        until Plr.Backpack:FindFirstChild("[BrownBag]")
        Plr.Backpack["[BrownBag]"].Parent = Plr.Character
        takingbag = false
    end

    if takingbag == false then
        local chars
        for i, v  in pairs(game.Players:GetPlayers()) do
            if v.Character and v.Character:FindFirstChild("Christmas_Sock") == nil and v.Character:FindFirstChild("FULLY_LOADED_CHAR") and v ~= Plr then
                chars = v.Character
                if Plr.Character:FindFirstChild("[BrownBag]") then
                    Plr.Character["[BrownBag]"]:Activate()
                end
                Plr.Character.HumanoidRootPart.CFrame = v.Character.UpperTorso.CFrame * CFrame.new(0, 0, -2)
            end
            wait(0.005)
        end
        if not chars then
            bag = false
        end
    end
until bag == false
end)
