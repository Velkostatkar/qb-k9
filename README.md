# Police K9 for QB Framework by Hashisx Discord: hashisx#3447

# You must add this to QB Inventory.

AddEventHandler("inventory:server:SearchLocalVehicleInventory", function(plate, list, cb)
    
    local TRUNK = Trunks[plate]
    local GLOVEBOX = Gloveboxes[plate]
    local RESULT = false

    if TRUNK ~= nil then
        for k, v in pairs(TRUNK.items) do
            local ITEM = TRUNK.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        TRUNK = GetOwnedVehicleItems(plate)

        for k, v in pairs(TRUNK) do

            local ITEM = TRUNK[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end

    end

    if GLOVEBOX ~= nil then
        for k, v in pairs(GLOVEBOX.items) do

            local ITEM = GLOVEBOX.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        GLOVEBOX = GetOwnedVehicleGloveboxItems(plate)

        for k, v in pairs(GLOVEBOX) do
            local ITEM = GLOVEBOX[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    end
    print(tostring(RESULT))
    cb(RESULT)
end)

function HasItem(list, item)

    for i = 1, #list do

        if item == list[i] then
            print('true')
            return true
        end
    end

    return false
end



I did not create the K9 ped. All Credit goes to https://www.lcpdfr.com/downloads/gta5mods/character/19996-german-shepherd-malinois-k9-dog/
