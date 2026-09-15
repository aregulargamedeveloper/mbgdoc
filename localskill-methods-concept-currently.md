---
icon: arrow-progress
---

# LocalSkill Methods (CONCEPT CURRENTLY)

### How skills are organized



```luau
type skill = {} -- blah blah

type hdata = {
      skills : {
        { -- localskill object
        cooldown : number,
        skill : skill, -- skill "module"
        slot : number,
        visible : boolean,
        
        }
    }
}
```



### Hiding/Showing (:visible)

Each `SkillInstance` object contains a Skill property linking to the actual skill data as well as a Visible property and Cooldown property. A **GLOBAL** skill object can have a group property, Here's the basic/default groupings you can add to a skill:

```
Awakening,
Base
```

to hide by group:

```lua
for _,skill in Hdata:filterLocalSkillsByGlobalProperty("group","awakening") do
    Skill:visible(false)
end

-- or:

-- CONCEPT
Hdata:quickVisibleSkillByGroup("awakening",false)
```

### Removing Skills (:destroy)

```lua
local myskill = Hdata:filterLocalSkillsByGlobalProperty("name","MySkill")[1]
if not myskill then
    warn "this skill doesnt exist"
    return
end

myskill:destroy()
```

