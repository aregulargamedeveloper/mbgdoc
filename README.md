---
icon: comment-question
---

# How to : Counters

Counters are moves that punish your opponent if youre hit during its effect (and often punishing you if youre not hit during its effect)\
\
Counters in mbg use IFrames (hdata.data.invincibility)

to change invincibility, you use the hdata.invincibilitymodifier value modifier. if you dont know how to use value modifiers, read the [README (2).md](<README (2).md> "mention") page.

Make sure to use skillutils:AddValueModifier, since counters are skills.

Now to detect when theyre hit during the counter, use the hdata.hitwhileunstoppable script signal with a promise

Here's some sample code:

<pre class="language-luau"><code class="lang-luau"><strong>const Promise = require() -- &#x3C; put your path to promise
</strong><strong>
</strong>-----------------

-- hdata/"plr" and skillutils passed in here.....

-- apply slowness here maybe?

local modifier = skillutils:AddValueModifier(hdata.invincibilitymodifier,{},"max",15)
local success,hitbox = promise.fromEvent(hdata.hitwhileunstoppable):timeout(0.75):andThen(function(hitbox)
    return true,hitbox
end):catch(function()
    return false
end):expect()

if not success then
    print "The counter was missed!"
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

</code></pre>

