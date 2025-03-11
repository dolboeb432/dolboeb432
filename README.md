local U1 = game["Players"]["LocalPlayer"]
local U2 = Instance["new"]("ScreenGui")
local U3 = Instance["new"]("Frame")
local U4 = Instance["new"]("TextButton")
local U5 = Instance["new"]("TextLabel")

U2["Parent"] = U1:FindFirstChildOfClass("PlayerGui")
U2["ResetOnSpawn"] = false

U3["Size"] = UDim2["new"](0, 200, 0, 100)
U3["Position"] = UDim2["new"](0.5, -100, 0.5, -50)
U3["BackgroundColor3"] = Color3["fromRGB"](0, 0, 0)
U3["Active"] = true
U3["Draggable"] = true
U3["Parent"] = U2

U4["Size"] = UDim2["new"](0, 150, 0, 50)
U4["Position"] = UDim2["new"](0.5, -75, 0.5, -25)
U4["BackgroundColor3"] = Color3["fromRGB"](0, 255, 0)
U4["Text"] = "DRAG"
U4["Parent"] = U3

U5["Size"] = UDim2["new"](0, 200, 0, 50)
U5["Position"] = UDim2["new"](0.5, -100, 0.1, 0)
U5["BackgroundTransparency"] = 0
U5["Text"] = "Script by Vanihgol333"
U5["TextColor3"] = Color3["fromRGB"](255, 255, 255)
U5["TextScaled"] = true
U5["Parent"] = U2

local U6 = game:GetService("ReplicatedStorage")
local U7 = U6:WaitForChild("Shared"):WaitForChild("Remotes"):WaitForChild("RequestStartDrag")

local function U8()
    local V1, V2 = nil, math["huge"]
    if U1["Character"] and U1["Character"]:FindFirstChild("HumanoidRootPart") then
        local V3 = U1["Character"]["HumanoidRootPart"]["Position"]
        for _, V4 in ipairs(game["Players"]["GetPlayers"](game["Players"])) do
            if V4 ~= U1 and V4["Character"] and V4["Character"]:FindFirstChild("HumanoidRootPart") then
                local V5 = V4["Character"]["HumanoidRootPart"]
                local V6 = (V5["Position"] - V3).Magnitude
                if V6 < V2 then
                    V2 = V6
                    V1 = V4["Character"]
                end
            end
        end
    end
    return V1
end

U4.MouseButton1Click:Connect(function()
    local V7 = U8()
    if V7 then
        if not U5 or U5["Text"] ~= "Script by Vanihgol333" then
            error("Script has been modified. Unauthorized change detected!")
        end
        U7["FireServer"](U7, V7)
    end
end)

spawn(function()
    wait(3)
    U5["Visible"] = false  -- Полностью скрывает надпись без удаления
end)

local X1 = "S".."c".."r".."i".."p".."t".." by ".."V".."a".."n".."i".."h".."g".."o".."l".."3".."3".."3"
assert(X1 == "Script by Vanihgol333", "Hidden message corrupted!")
