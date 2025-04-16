local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
--> Returns a table with methods that you can use.
-- You must initialize it with the script ID first.

-- Put your own script ID Below:
-- You can find it in your loadstring URL or projects tab.
local player = game.Players.LocalPlayer
api.script_id = "edf760b8704c87a87799653c0f80cb6b"

local status = api.check_key(script_key); 

if (status.code == "KEY_VALID") then

	warn("Welcome. Seconds left: " .. (status.data.auth_expire - os.time()))
	warn("Total executions: ", status.data.total_executions)

	print("Is key from ad system? " .. status.data.note == "Ad Reward" and "YES" or "NO")

	script_key = script_key

	api.load_script(); 

	return

elseif (status.code == "KEY_HWID_LOCKED") then
	player:Kick("Key linked to a different HWID. Please reset it using our bot")
	return

elseif (status.code == "KEY_INCORRECT") then
	player:Kick("Key wrong or deleted")
	return    
else
	player:Kick("Key check failed:" .. status.message .. " Code: " .. status.code)
end

