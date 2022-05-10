 local L_1_ = true;
        local L_2_ = game.Players.LocalPlayer.Character.HumanoidRootPart;
        local L_3_ = L_2_.Position - Vector3.new(5, 0, 0)
        
        game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(L_4_arg1)
            if L_4_arg1 == 'f' then
                L_1_ = not L_1_
            end;
            if L_4_arg1 == 'r' then
                L_2_ = game.Players.LocalPlayer.Character.HumanoidRootPart;
                L_3_ = L_2_.Position - Vector3.new(5, 0, 0)
            end
        end)
        
        for L_5_forvar1, L_6_forvar2 in pairs(game.Players:GetPlayers()) do
            if L_6_forvar2 == game.Players.LocalPlayer then
            else
                local L_7_ = coroutine.create(function()
                    game:GetService('RunService').RenderStepped:Connect(function()
                        local L_8_, L_9_ = pcall(function()
                            local L_10_ = L_6_forvar2.Character;
                            if L_10_ then
                                if L_10_:FindFirstChild("HumanoidRootPart") then
                                    if L_1_ then
                                        L_6_forvar2.Backpack:ClearAllChildren()
                                        for L_11_forvar1, L_12_forvar2 in pairs(L_10_:GetChildren()) do
                                            if L_12_forvar2:IsA("Tool") then
                                                L_12_forvar2:Destroy()
                                            end
                                        end;
                                        L_10_.HumanoidRootPart.CFrame = CFrame.new(L_3_)
                                    end
                                end
                            end
                        end)
                        if L_8_ then
                        else
                            warn("Unnormal error: "..L_9_)
                        end
                    end)
                end)
                coroutine.resume(L_7_)
            end
        end;
