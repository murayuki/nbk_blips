**Credits:**
Negbook

**installtion :** 
server.cfg
```
start nbk_blips 
```

**exports :** 
```
exports.nbk_blips:GetBlips() 
exports.nbk_blips:GetClosestBlip()
exports.nbk_blips:GetClosestBlip(ped)
exports.nbk_blips:GetClosestBlipByCoords(coords)
exports.nbk_blips:GetOnScreenBlips()
exports.nbk_blips:GetOnScreenClosestBlip()
exports.nbk_blips:GetBlipsBySprite(spriteid)
exports.nbk_blips:GetClosestBlipBySprite(spriteid)
exports.nbk_blips:GetClosestBlipBySprite(spriteid,ped)
exports.nbk_blips:GetOnScreenBlipsBySprite(spriteid)
exports.nbk_blips:GetOnScreenClosestBlipBySprite(spriteid)
exports.nbk_blips:GetOnScreenClosestBlipBySpriteByCoords(spriteid,coords)
```

**example :** 
```
Citizen.CreateThread(function()
    while true do 
        local blips = exports.nbk_blips:GetClosestBlipBySprite(277)
        local coords = GetBlipCoords(blips) 
        print("The Closest ATM Blips:"..blips.." x:".. coords.x  .. "y:"..coords.y  .."z:"..coords.z )
        Citizen.Wait(330)
    end 
end)
```

**example2:**
```
CurrentBlip = nil 

Citizen.CreateThread(function()
    while true do 
        local blip = exports.nbk_blips:GetOnScreenClosestBlipBySprite(434)
        local coords = GetBlipCoords(blip) 
        local x = coords.x 
        local y = coords.y 
        local z = coords.z 
        CurrentBlip = {x=x,y=y,z=z}
        TriggerEvent('localmessage',"The OnScreen Closest ATM Blips:"..blip.."x:".. x .. "y:"..y .."z:"..z)
        Citizen.Wait(330)
    end 
end)

Citizen.CreateThread(function()
    while true do 
        if CurrentBlip then 
        DrawMarker(1, CurrentBlip.x, CurrentBlip.y, CurrentBlip.z-1.0, 0.0, 0.0, 0.0, 0, 0.0, 0.0, 1.0, 1.0, 1.0, 0, 0, 255, 100, false, false, 2, true--[[旋轉]], false--[[dict]], false--[[txd]], false)
        end 
        Citizen.Wait(0)
    end 
end )
```

> Github: [nbk_blips](https://github.com/negbook/nbk_blips)