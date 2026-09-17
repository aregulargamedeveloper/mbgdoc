---
icon: comment-question
---

# How to : Counters

Counters are moves that punish your opponent if youre hit during its effect (and often punishing you if youre not hit during its effect)\
\
Counters in mbg use IFrames (hdata.data.invincibility)

to change invincibility, you use the hdata.invincibilityModifier value modifier. if you dont know how to use value modifiers, read the [README (2) (1).md](<README (2) (1).md> "mention") page.

Make sure to use skillutils:addValueModifier, since counters are skills.

Now to detect when theyre hit during the counter, use the hdata.hitWhileUnstoppable script signal with a promise

Here's some sample code:

```luau
const ServerStorage = game:GetService("ServerStorage")
const Packages = ServerStorage.Packages
const Promise = require(Packages.Promise) -- < put your path to promise
const Knit = require(Packages.Knit)

-----------------

-- hdata/"plr" and skillutils passed in here.....

-- apply slowness here maybe?

local modifier = skillutils:addValueModifier(hdata.invincibilitymodifier,{},"max",15)
local success,hitbox = promise.fromEvent(hdata.hitwhileunstoppable):timeout(0.75*SkillUtils.speed):andThen(function(hitbox)
    return true,hitbox
end):catch(function()
    return false
end):expect()

if not success then
    print "The counter was missed!"
    skillUtils:wait(3)
    -- cancel the slowness?
    return
end

local hdata = hitbox.hdata

if not hdata then
    warn "No hdata linked to this hitbox!" -- use fwarn if your module has it!
    return
end
    
-- do your counter logic here

```

