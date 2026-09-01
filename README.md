---
icon: comment-question
---

# How to : Counters

Counters are moves that punish your opponent if youre hit during its effect (and often punishing you if youre not hit during its effect)\
\
Counters in mbg use IFrames (hdata.data.invincibility)

to change invincibility, you use the hdata.invincibilitymodifier value modifier. if you dont know how to use value modifiers, read the [README (2).md](<README (2).md> "mention") page.

Make sure to use skillutils:AddValueModifier, since counters are skills.

Now to detect when theyre hit during the counter, use the hdata.hitwhileunstoppable script signal

Heres some sample code:

```lua
-- hdata/"plr" and skillutils passed in here.....

-- apply slowness here maybe?

local modifier = skillutils:AddValueModifier(hdata.invincibilitymodifier,{},"max",15)
local hitbox = hdata.hitwhileunstoppable:Wait(.75) -- script signals in mbg have a custom timeout time

if not hitbox then
    print("The counter was missed!")
    task.wait(3)
    -- cancel the slowness?
    return
end

local hdata = hitbox.hdata

if not hdata then
    warn("No hdata linked to this hitbox!")
    return
end
    
    -- do your counter logic here
end))

```

