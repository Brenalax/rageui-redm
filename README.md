# RageUI For RedM

Exemple menu : 

```
local IsOpen = false

function OpenMenu()
    local main = RageUI.CreateMenu("Exemple Menu", "Main")
    main.Closed = function()
        IsOpen = false
    end
    if IsOpen then
        IsOpen = false #optimization
        RageUI.Visible(main, false)
        return
    else
        IsOpen = true
        RageUI.Visible(main, true)
        CreateThread(function()
            while IsOpen do
                main:IsVisible(function(Items)
                    --Items:Heritage(1, 2)
                    Items:AddSeparator("↓ Test ! ↓")
                    Items:AddButton("Button 1", nil, { IsDisable = false }, function(onSelected)
                      if onSelected then
                        --GiveMoney() for exemple
                      end
                    end)
                end, function()
                end)
                Wait(1)
            end
        end)
    end
end
```
> Default version made by Dylan and this edition made by Brenalax with 💖
###### Credit Brenalax
