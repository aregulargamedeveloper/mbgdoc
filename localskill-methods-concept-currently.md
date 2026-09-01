---
icon: arrow-progress
---

# LocalSkill Methods (CONCEPT CURRENTLY)

### Hiding/Showing (:Visible)

Each `SkillInstance` object contains a Skill property linking to the actual skill data as well as a Visible property and Cooldown property. A **GLOBAL** skill object can have a Group property, Here's the basic/default groupings you can add to a skill:

```
Awakening,
Base
```

to hide by group:

```lua
for _,skill in Hdata:filterLocalSkillsByGlobalProperty("Group","Awakening") do
    Skill:Visible(false)
end

-- or:

-- CONCEPT
Hdata:QuickVisibleSkillByGroup("Awakening",false)
```

### Removing Skills (:Destroy)

```lua
local myskill = Hdata:filterLocalSkillsByGlobalProperty("Name","MySkill")[1]
if not myskill then
    warn("this skill doesnt exist")
    return
end

myskill:Destroy()
```
