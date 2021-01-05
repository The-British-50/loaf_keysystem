# loaf_keysystem
Key system for ESX. 

This is a resource that is going to be used by some of the resources I make.
You are free to do whatever you want with this resource, however, **you are not allowed to sell this resource**. You are allowed to modify the resource and upload on other sites, but you are not allowed to profit off of this resource, or claim that it is yours.

## ALPHA
Please note that this resource is in alpha. Expect bugs and issues. 
If you find any issues, please report them to me on discord @Loaf Scripts#7785, or open an issue here on GitHub.

## Usage for resource developers
This guide is not finished. This resource is a W.I.P.

You can only generate keys from server side code (security reasons). To generate a key, do like this:
```lua
TriggerEvent("generateKey", source, key_id, key_label, eventtype --[[server or client or false]], eventname --[[the event name to trigger upon usage, or false]], function()
  print("key has been generated")
end)
```
If you have stated an event to trigger upon usage, it will send the key_data to the event. This is what you can get from the key data:
Key | Value
--- | ---
key_id | the key id
unique_id | the unique id of the key
name | the label of the key
eventtype | the event type specified
eventname | the event name specified

To get a list of all keys, do like this:
```lua
TriggerEvent("getKeys", source, function(keys)
  if keys then
    for k, v in pairs(keys) do
      local key_id = v.key_id
      local unique_id = v.unique_id
    end
  else
    print("Couldn't get keys")
  end
end)
```

To remove a key, do like this:
```lua
TriggerEvent("removeKey", source, unique_id, function(removed)
  if removed then
    print("Key removed!")
  else
    print("Key couldn't be removed :/")
  end
end)
```

To set the usage of a key, do like this (client side)
```lua
TriggerEvent("loaf_keysystem:setUsage", key_id, function(key_id)
  print("Used key: " .. key)
end)
```