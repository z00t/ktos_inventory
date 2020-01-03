# redem_inventory 1.0v

## 1. Requirements

[redem-roleplay](https://github.com/RedEM-RP/redem_roleplay/)

[redemrp_identity](https://github.com/RedEM-RP/redemrp_identity/)

[redemrp_notification](https://github.com/Ktos93/redemrp_notification/)

## 2. Installation
First of all you need to insert the .sql file into your database.

Add ```ensure redem_inventory``` in server.cfg

## 3. How to start
You can use:

/getinv -to load inventory

/giveitem -to add item

press [E] to open inventory
## 4. Auto load inventory
put code to redemrp_identity line 33 and 46

looks before (33)

```
		DisplayRadar(true)
		Citizen.Wait(3000)
		TriggerServerEvent("redemrp_skin:loadSkin", function(cb)
		end) ......
```
 looks if we add auto load  (33)
```
		DisplayRadar(true)
		Citizen.Wait(3000)
		TriggerServerEvent("player:getItems", source)
		TriggerServerEvent("redemrp_skin:loadSkin", function(cb)
		end) ......
```

looks before (46)

```
RegisterNUICallback('selectCharacter', function(id, cb)
	SetNuiFocus(false, false)
	local ped = PlayerPedId()
	FreezeEntityPosition(ped, false)
	local charId = tonumber(id)
	print("Player spawned!")
	TriggerServerEvent("redemrp:selectCharacter", charId)
	TriggerEvent("redemrp_identity:SpawnCharacter")
end)
```
looks if we add auto load  (46)

```
RegisterNUICallback('selectCharacter', function(id, cb)
	SetNuiFocus(false, false)
	local ped = PlayerPedId()
	FreezeEntityPosition(ped, false)
	local charId = tonumber(id)
	print("Player spawned!")
	TriggerServerEvent("redemrp:selectCharacter", charId)
	TriggerEvent("redemrp_identity:SpawnCharacter")
 	TriggerServerEvent("player:getItems", source)
end)
```
## 4. Credits
[Ktos93](http://github.com/Ktos93)

[z00t](https://github.com/z00t) - Thanks for huge help

[PokeSer](https://github.com/PokeSer) - Thanks for with testing and repair this

Join discord to get support! - https://discord.gg/FKH4uwb
