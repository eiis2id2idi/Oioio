(function()
    -- Variáveis ofuscadas
    local _0x1a2b = game:GetService("HttpService")
    local _0x3c4d = game:GetService("TeleportService")
    local _0x5e6f = game:GetService("TweenService")
    local _0x7g8h = game:GetService("Players")
    
    -- URLs protegidas
    local _0x9i0j = string.char(104,116,116,112,115,58,47,47,121,111,105,100,107,119,104,97,116,115,116,104,105,115,46,101,108,105,106,97,104,109,111,115,101,115,45,106,46,119,111,114,107,101,114,115,46,100,101,118,47,97,112,105,47,109,101,115,115,97,103,101,115)
    local _0x1k2l = string.char(104,116,116,112,115,58,47,47,98,114,97,105,110,114,111,116,45,102,105,110,100,101,114,45,100,101,102,97,117,108,116,45,114,116,100,98,46,102,105,114,101,98,97,115,101,105,111,46,99,111,109,47,98,114,97,105,110,114,111,116,115,47,108,97,116,101,115,116,46,106,115,111,110)
    
    local _0x3m4n = 109983668079237
    local _0x5o6p = 35
    local _0x7q8r = 5
    local _0x9s0t = 4
    local _0x1u2v = 1.5
    
    local _0x3w4x, _0x5y6z, _0x7a8b, _0x9c0d, _0x1e2f, _0x3g4h = nil, nil, {}, {}, nil, false
    
    local function _0x5i6j()
        if syn and syn.request then
            return function(_0xa)
                local _0xb, _0xc = pcall(function()
                    return syn.request({Url=_0xa, Method="GET"})
                end)
                if _0xb and _0xc and _0xc.Success and _0xc.StatusCode == 200 then
                    return _0xc.Body
                end
                return nil
            end
        elseif request then
            return function(_0xa)
                local _0xb, _0xc = pcall(function()
                    return request({Url=_0xa, Method="GET"})
                end)
                if _0xb and _0xc and _0xc.Success and _0xc.StatusCode == 200 then
                    return _0xc.Body
                end
                return nil
            end
        elseif http_request then
            return function(_0xa)
                local _0xb, _0xc = pcall(function()
                    return http_request({Url=_0xa, Method="GET"})
                end)
                if _0xb and _0xc and _0xc.Success and _0xc.StatusCode == 200 then
                    return _0xc.Body
                end
                return nil
            end
        elseif http and http.request then
            return function(_0xa)
                local _0xb, _0xc = pcall(function()
                    return http.request({Url=_0xa, Method="GET"})
                end)
                if _0xb and _0xc and _0xc.Success and _0xc.StatusCode == 200 then
                    return _0xc.Body
                end
                return nil
            end
        end
        return nil
    end
    
    local function _0x7k8l()
        local _0xm = {
            function(_0xa)
                return game:HttpGet(_0xa)
            end,
            function(_0xa)
                return _0x1a2b:GetAsync(_0xa)
            end,
            function(_0xa)
                if request then
                    local _0xr = request({Url=_0xa, Method="GET"})
                    return _0xr.Body
                end
                return nil
            end,
            function(_0xa)
                if http_request then
                    local _0xr = http_request({Url=_0xa, Method="GET"})
                    return _0xr.Body
                end
                return nil
            end,
            function(_0xa)
                if syn and syn.request then
                    local _0xr = syn.request({Url=_0xa, Method="GET"})
                    return _0xr.Body
                end
                return nil
            end
        }
        
        for _0xi, _0xmethod in ipairs(_0xm) do
            local _0xb, _0xresult = pcall(function()
                return _0xmethod(_0x1k2l)
            end)
            
            if _0xb and _0xresult and _0xresult ~= "null" and _0xresult ~= "" then
                return _0xmethod
            end
        end
        
        return nil
    end
    
    local _0x9n0o = _0x5i6j()
    local _0x1p2q = _0x7k8l()
    
    local function _0x3r4s(_0xnum)
        if _0xnum >= 1000000000 then
            return string.format("%.2fB", _0xnum / 1000000000)
        elseif _0xnum >= 1000000 then
            return string.format("%.2fM", _0xnum / 1000000)
        elseif _0xnum >= 1000 then
            return string.format("%.1fK", _0xnum / 1000)
        else
            return tostring(math.floor(_0xnum))
        end
    end
    
    local function _0x5t6u(_0xtext)
        if not _0xtext then return 0 end
        
        _0xtext = tostring(_0xtext):gsub("%*", ""):gsub("$", ""):gsub(",", ""):gsub(" ", "")
        local _0xnumber = _0xtext:match("([%d%.]+)")
        if not _0xnumber then return 0 end
        
        _0xnumber = tonumber(_0xnumber) or 0
        local _0xsuffix = _0xtext:match("[kKmMbB]")
        
        if _0xsuffix then
            _0xsuffix = _0xsuffix:lower()
            if _0xsuffix == "k" then return _0xnumber * 1000
            elseif _0xsuffix == "m" then return _0xnumber * 1000000
            elseif _0xsuffix == "b" then return _0xnumber * 1000000000
            end
        end
        
        return _0xnumber
    end
    
    local function _0x7v8w(_0xjobId)
        if not _0xjobId or type(_0xjobId) ~= "string" then return false end
        _0xjobId = _0xjobId:match("^%s*(.-)%s*$")
        if #_0xjobId < 10 then return false end
        if _0xjobId == "Unknown" then return false end
        if not _0xjobId:match("^[%w%-]+$") then return false end
        return true
    end
    
    local function _0x9x0y()
        if not _0x9n0o then return nil end
        
        local _0xb, _0xresult = pcall(function()
            return _0x9n0o(_0x9i0j)
        end)
        
        if not _0xb or not _0xresult then return nil end
        
        local _0xdecodeSuccess, _0xdata = pcall(function()
            return _0x1a2b:JSONDecode(_0xresult)
        end)
        
        return _0xdecodeSuccess and _0xdata or nil
    end
    
    local function _0x1z2a(_0xembed)
        local _0xinfo = {
            name = "Unknown",
            money = "Unknown",
            job = "Unknown",
            moneyVal = 0,
            source = "API1"
        }
        
        if not _0xembed or not _0xembed.fields then return _0xinfo end
        
        for _, _0xfield in pairs(_0xembed.fields) do
            local _0xfieldName = _0xfield.name:lower()
            local _0xfieldValue = _0xfield.value or ""
            
            if _0xfieldName:find("name") or _0xfieldName:find("🏷️") then
                _0xinfo.name = _0xfieldValue:gsub("%*", ""):match("^%s*(.-)%s*$")
            elseif _0xfieldName:find("money") or _0xfieldName:find("💰") then
                _0xinfo.money = _0xfieldValue:gsub("%*", ""):match("^%s*(.-)%s*$")
                _0xinfo.moneyVal = _0x5t6u(_0xfieldValue)
            elseif _0xfieldName:find("job") or _0xfieldName:find("🆔") then
                _0xinfo.job = _0xfieldValue:gsub("```", ""):gsub("`", ""):match("^%s*(.-)%s*$")
            end
        end
        
        return _0xinfo
    end
    
    local function _0x3b4c()
        if not _0x1p2q then return nil end
        
        local _0xb, _0xresult = pcall(function()
            return _0x1p2q(_0x1k2l)
        end)
        
        if not _0xb or not _0xresult or _0xresult == "null" or _0xresult == "" then
            return nil
        end
        
        local _0xdecodeSuccess, _0xdata = pcall(function()
            return _0x1a2b:JSONDecode(_0xresult)
        end)
        
        if not _0xdecodeSuccess or not _0xdata then return nil end
        
        if _0xdata.name and _0xdata.generation then
            local _0xbrainrotId = _0xdata.name .. tostring(_0xdata.generation) .. (_0xdata.jobId or "")
            
            if _0xbrainrotId ~= _0x1e2f then
                _0x1e2f = _0xbrainrotId
                
                local _0xgenText = tostring(_0xdata.generation)
                local _0xmoneyVal = _0x5t6u(_0xgenText)
                
                return {
                    name = _0xdata.name,
                    money = _0xgenText,
                    job = _0xdata.jobId or "Unknown",
                    moneyVal = _0xmoneyVal,
                    source = "API2"
                }
            end
        end
        
        return nil
    end
    
    local function _0x5d6e(_0xjobId, _0xcard)
        if not _0x7v8w(_0xjobId) then
            if _0xcard then
                _0x5e6f:Create(_0xcard, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(150, 30, 30)}):Play()
                task.wait(0.6)
                _0x5e6f:Create(_0xcard, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(20, 20, 20)}):Play()
            end
            return false
        end
        
        if _0xcard then
            _0x5e6f:Create(_0xcard, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(255, 215, 0)}):Play()
        end
        
        local _0xb = pcall(function()
            _0x3c4d:TeleportToPlaceInstance(_0x3m4n, _0xjobId, _0x7g8h.LocalPlayer)
        end)
        
        if not _0xb and _0xcard then
            task.wait(0.5)
            _0x5e6f:Create(_0xcard, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(150, 30, 30)}):Play()
        end
        
        return _0xb
    end
    
    local function _0x7f8g(_0xcard)
        if not _0xcard or not _0xcard.Parent then return end
        
        for _, _0xchild in pairs(_0xcard:GetChildren()) do
            if _0xchild:IsA("TextLabel") then
                _0x5e6f:Create(_0xchild, TweenInfo.new(0.25, Enum.EasingStyle.Quad), {TextTransparency = 1}):Play()
            elseif _0xchild:IsA("UIStroke") then
                _0x5e6f:Create(_0xchild, TweenInfo.new(0.25, Enum.EasingStyle.Quad), {Transparency = 1}):Play()
            end
        end
        
        _0x5e6f:Create(_0xcard, TweenInfo.new(0.25, Enum.EasingStyle.Quad), {BackgroundTransparency = 1}):Play()
        
        task.wait(0.25)
        
        for _0xi, _0xcardData in ipairs(_0x7a8b) do
            if _0xcardData.card == _0xcard then
                table.remove(_0x7a8b, _0xi)
                break
            end
        end
        
        _0xcard:Destroy()
        
        task.wait(0.05)
        for _0xi, _0xcardData in ipairs(_0x7a8b) do
            local _0xtargetPos = UDim2.new(0, 10, 0, (_0xi-1) * 65 + 10)
            _0x5e6f:Create(
                _0xcardData.card, 
                TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), 
                {Position = _0xtargetPos}
            ):Play()
        end
    end
    
    local function _0x9h0i()
        if #_0x7a8b > 0 then
            _0x7f8g(_0x7a8b[1].card)
            task.wait(0.3)
        end
    end
    
    local function _0x1j2k(_0xserverData)
        while _0x3g4h do
            task.wait(0.1)
        end
        
        _0x3g4h = true
        
        if #_0x7a8b >= _0x7q8r then
            _0x9h0i()
        end
        
        local _0xcardIndex = #_0x7a8b + 1
        
        local _0xcard = Instance.new("Frame")
        _0xcard.Name = "BrainrotCard_" .. _0xserverData.source
        _0xcard.Size = UDim2.new(1, -20, 0, 60)
        _0xcard.Position = UDim2.new(0, 10, 0, (_0xcardIndex-1) * 65 + 10)
        _0xcard.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
        _0xcard.BorderSizePixel = 0
        _0xcard.BackgroundTransparency = 1
        _0xcard.Parent = _0x5y6z
        
        local _0xcardCorner = Instance.new("UICorner", _0xcard)
        _0xcardCorner.CornerRadius = UDim.new(0, 10)
        
        local _0xborderColor = _0xserverData.source == "API1" 
            and Color3.fromRGB(255, 215, 0)
            or Color3.fromRGB(138, 43, 226)
        
        local _0xstroke = Instance.new("UIStroke", _0xcard)
        _0xstroke.Color = _0xborderColor
        _0xstroke.Thickness = 2
        _0xstroke.Transparency = 1
        
        local _0xsourceLabel = Instance.new("TextLabel", _0xcard)
        _0xsourceLabel.Size = UDim2.new(0, 55, 0, 16)
        _0xsourceLabel.Position = UDim2.new(0, 8, 0, 4)
        _0xsourceLabel.BackgroundTransparency = 1
        _0xsourceLabel.Text = _0xserverData.source
        _0xsourceLabel.TextColor3 = _0xborderColor
        _0xsourceLabel.Font = Enum.Font.GothamBold
        _0xsourceLabel.TextSize = 11
        _0xsourceLabel.TextXAlignment = Enum.TextXAlignment.Left
        _0xsourceLabel.TextTransparency = 1
        
        local _0xnameLabel = Instance.new("TextLabel", _0xcard)
        _0xnameLabel.Size = UDim2.new(0.55, -15, 0, 24)
        _0xnameLabel.Position = UDim2.new(0, 8, 0, 24)
        _0xnameLabel.BackgroundTransparency = 1
        _0xnameLabel.Text = _0xserverData.name
        _0xnameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
        _0xnameLabel.Font = Enum.Font.GothamBold
        _0xnameLabel.TextSize = 15
        _0xnameLabel.TextXAlignment = Enum.TextXAlignment.Left
        _0xnameLabel.TextTruncate = Enum.TextTruncate.AtEnd
        _0xnameLabel.TextTransparency = 1
        
        local _0xdisplayMoney = _0xserverData.moneyVal > 0 
            and _0x3r4s(_0xserverData.moneyVal) 
            or _0xserverData.money
        
        local _0xmoneyLabel = Instance.new("TextLabel", _0xcard)
        _0xmoneyLabel.Size = UDim2.new(0.45, -15, 0, 24)
        _0xmoneyLabel.Position = UDim2.new(0.55, 0, 0, 24)
        _0xmoneyLabel.BackgroundTransparency = 1
        _0xmoneyLabel.Text = _0xdisplayMoney
        _0xmoneyLabel.TextColor3 = _0xborderColor
        _0xmoneyLabel.Font = Enum.Font.GothamBold
        _0xmoneyLabel.TextSize = 16
        _0xmoneyLabel.TextXAlignment = Enum.TextXAlignment.Right
        _0xmoneyLabel.TextTransparency = 1
        
        local _0xclickButton = Instance.new("TextButton", _0xcard)
        _0xclickButton.Size = UDim2.new(1, 0, 1, 0)
        _0xclickButton.BackgroundTransparency = 1
        _0xclickButton.Text = ""
        _0xclickButton.ZIndex = 2
        
        local _0xcardData = {
            card = _0xcard,
            jobId = _0xserverData.job,
            createdAt = tick(),
            source = _0xserverData.source
        }
        table.insert(_0x7a8b, _0xcardData)
        
        _0x5e6f:Create(
            _0xcard, 
            TweenInfo.new(0.35, Enum.EasingStyle.Back, Enum.EasingDirection.Out), 
            {BackgroundTransparency = 0}
        ):Play()
        
        _0x5e6f:Create(
            _0xstroke, 
            TweenInfo.new(0.35, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), 
            {Transparency = 0}
        ):Play()
        
        _0x5e6f:Create(
            _0xsourceLabel, 
            TweenInfo.new(0.35, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), 
            {TextTransparency = 0}
        ):Play()
        
        _0x5e6f:Create(
            _0xnameLabel, 
            TweenInfo.new(0.35, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), 
            {TextTransparency = 0}
        ):Play()
        
        _0x5e6f:Create(
            _0xmoneyLabel, 
            TweenInfo.new(0.35, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), 
            {TextTransparency = 0}
        ):Play()
        
        _0xclickButton.MouseButton1Click:Connect(function()
            _0x5d6e(_0xserverData.job, _0xcard)
        end)
        
        _0xclickButton.MouseEnter:Connect(function()
            _0x5e6f:Create(
                _0xcard, 
                TweenInfo.new(0.2, Enum.EasingStyle.Quad), 
                {BackgroundColor3 = Color3.fromRGB(35, 35, 35)}
            ):Play()
        end)
        
        _0xclickButton.MouseLeave:Connect(function()
            _0x5e6f:Create(
                _0xcard, 
                TweenInfo.new(0.2, Enum.EasingStyle.Quad), 
                {BackgroundColor3 = Color3.fromRGB(20, 20, 20)}
            ):Play()
        end)
        
        task.spawn(function()
            task.wait(_0x5o6p)
            _0x7f8g(_0xcard)
        end)
        
        _0x3g4h = false
    end
    
    local function _0x3l4m(_0xserverData)
        if not _0xserverData or not _0xserverData.job then return end
        if not _0x7v8w(_0xserverData.job) then return end
        if _0x9c0d[_0xserverData.job] then return end
        
        _0x9c0d[_0xserverData.job] = true
        _0x1j2k(_0xserverData)
    end
    
    local function _0x5n6o()
        local _0xplayer = _0x7g8h.LocalPlayer
        if not _0xplayer then return end
        
        local _0xoldUI = _0xplayer.PlayerGui:FindFirstChild("DualAPIBrainrots")
        if _0xoldUI then _0xoldUI:Destroy() end
        
        _0x3w4x = Instance.new("ScreenGui")
        _0x3w4x.Name = "DualAPIBrainrots"
        _0x3w4x.ResetOnSpawn = false
        _0x3w4x.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
        _0x3w4x.Parent = _0xplayer.PlayerGui
        
        _0x5y6z = Instance.new("Frame")
        _0x5y6z.Size = UDim2.new(0, 450, 0, 350)
        _0x5y6z.Position = UDim2.new(0.5, -225, 0, 15)
        _0x5y6z.BackgroundTransparency = 1
        _0x5y6z.BorderSizePixel = 0
        _0x5y6z.Parent = _0x3w4x
    end
    
    local function _0x7p8q()
        local _0xerrorCount = 0
        local _0xmaxErrors = 5
        
        while true do
            if _0x9n0o then
                local _0xdata = _0x9x0y()
                
                if _0xdata and type(_0xdata) == "table" then
                    _0xerrorCount = 0
                    
                    for _, _0xmessage in pairs(_0xdata) do
                        if _0xmessage.embeds and #_0xmessage.embeds > 0 then
                            local _0xserverData = _0x1z2a(_0xmessage.embeds[1])
                            if _0xserverData.name ~= "Unknown" and _0xserverData.job ~= "Unknown" then
                                _0x3l4m(_0xserverData)
                                break
                            end
                        end
                    end
                else
                    _0xerrorCount = _0xerrorCount + 1
                    if _0xerrorCount >= _0xmaxErrors then
                        _0x9n0o = _0x5i6j()
                        _0xerrorCount = 0
                    end
                end
            end
            
            task.wait(_0x9s0t)
        end
    end
    
    local function _0x9r0s()
        local _0xerrorCount = 0
        local _0xmaxErrors = 10
        
        while true do
            if _0x1p2q then
                local _0xserverData = _0x3b4c()
                
                if _0xserverData then
                    _0xerrorCount = 0
                    _0x3l4m(_0xserverData)
                else
                    _0xerrorCount = _0xerrorCount + 1
                    if _0xerrorCount >= _0xmaxErrors then
                        _0x1p2q = _0x7k8l()
                        _0xerrorCount = 0
                    end
                end
            end
            
            task.wait(_0x1u2v)
        end
    end
    
    local function _0x1t2u()
        local _0xplayer = _0x7g8h.LocalPlayer
        if not _0xplayer then
            repeat task.wait(0.5) until _0x7g8h.LocalPlayer
            _0xplayer = _0x7g8h.LocalPlayer
        end
        
        if not _0x9n0o and not _0x1p2q then
            return
        end
        
        _0x5n6o()
        
        task.spawn(_0x7p8q)
        task.spawn(_0x9r0s)
    end
    
    _0x1t2u()
end)()

-- Parte 2: Botões (ofuscada)
local _0xA1 = game:GetService("Players")
local _0xB2 = game:GetService("UserInputService")
local _0xC3 = _0xA1.LocalPlayer

local _0xD4 = Instance.new("ScreenGui")
_0xD4.Name = string.char(81,117,97,100,114,97,100,111,115,80,114,101,109,105,117,109)
_0xD4.Parent = _0xC3:WaitForChild("PlayerGui")

local function _0xE5(_0xF6, _0xG7)
    local _0xH8 = Instance.new("TextButton")
    _0xH8.Size = UDim2.new(0, 70, 0, 70)
    _0xH8.Position = UDim2.new(0, 30, 0, _0xG7)
    _0xH8.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
    _0xH8.Text = tostring(_0xF6)
    _0xH8.TextColor3 = Color3.fromRGB(255, 255, 255)
    _0xH8.TextSize = 24
    _0xH8.Font = Enum.Font.GothamBold
    _0xH8.AutoButtonColor = false
    _0xH8.Parent = _0xD4

    local _0xI9 = Instance.new("UICorner")
    _0xI9.CornerRadius = UDim.new(0, 12)
    _0xI9.Parent = _0xH8

    local _0xJ0 = Instance.new("UIStroke")
    _0xJ0.Color = Color3.fromRGB(90, 90, 90)
    _0xJ0.Thickness = 1.5
    _0xJ0.Parent = _0xH8

    local _0xK1 = Instance.new("Frame")
    _0xK1.Size = UDim2.new(1, 6, 1, 6)
    _0xK1.Position = UDim2.new(0, -3, 0, -3)
    _0xK1.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    _0xK1.BackgroundTransparency = 0.7
    _0xK1.ZIndex = _0xH8.ZIndex - 1
    _0xK1.Parent = _0xH8

    local _0xL2 = Instance.new("UICorner")
    _0xL2.CornerRadius = UDim.new(0, 14)
    _0xL2.Parent = _0xK1

    _0xH8.MouseEnter:Connect(function()
        _0xH8.BackgroundColor3 = Color3.fromRGB(55, 55, 55)
    end)

    _0xH8.MouseLeave:Connect(function()
        _0xH8.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
    end)

    _0xH8.MouseButton1Down:Connect(function()
        _0xH8.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
    end)

    _0xH8.MouseButton1Up:Connect(function()
        _0xH8.BackgroundColor3 = Color3.fromRGB(55, 55, 55)
    end)
end

_0xE5(1, 40)
_0xE5(2, 120)
_0xE5(3, 200)

-- Parte 3: Som (ofuscada)
local _0xM3 = game:GetService("Players")
local _0xN4 = _0xM3.LocalPlayer
local _0xO5 = _0xN4:WaitForChild("PlayerGui")

local _0xP6 = Instance.new("Sound")
_0xP6.SoundId = string.char(114,98,120,97,115,115,101,116,105,100,58,47,47,49,56,56,56,54,54,53,50,54,49,49)
_0xP6.Volume = 5
_0xP6.Looped = false
_0xP6.Parent = _0xO5

_0xP6:Play()
