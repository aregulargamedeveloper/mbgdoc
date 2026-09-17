---
icon: lightbulb-exclamation-on
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Info

## Style guide & Ease of use

Every variable is formatted in "camelCase". .inOtherWords .everythingIsFormatted .likeThis.

**If a variable is not formatted in camelCase, Please ping me! `@not_missing`**

Every system should be in a folder. There should be NO loose modules inside ReplicatedStorage or ServerStorage.

**The exception to camel case** is service names. Services are named in Pascal case. .InOtherWords .ServicesAreFormatted .LikeThis

## Module loader

Mbg utilizes Knit by sleitnick.&#x20;

Eveything is formatted into services

For those inexperienced with a module loader, this is very important

_<mark style="color:$danger;">**DO NOT REQUIRE MODULES DIRECTLY!!!!!!!!!!!!!!!!!!!!!!!!!**</mark>_

instead, create a blank variable\
eg:<br>

```luau
local SkillService -- blank (nil) variable

-- later...

function MyService:KnitInit()
    SkillService = Knit.GetService("SkillService")
end
```

* Why?

Recursive requiring is the dilemma in Lua (and luau) that a module loader fixes. Instead of A needing B on startup And B needing A on startup (halting the game because one needs another) instead, they get eachother on KnitInit which just makes them able to talk to eachother without any issues!

## Fwarn and Fprint

Fwarn and Fprint are part of systems. They allow distinguishing of prints from systems. Put simply: fwarn just puts \[SERVICENAME] before what you warn. Same with fprint

## Promises

Knit itself utilizes promises and so does mbg. Please use them when applicable!&#x20;

Read [README (2).md](<README (2).md> "mention") to find the most common way promises are used!!

If you dont know how to use promises: Feel free to ask me how to use them or watch a tutorial.
