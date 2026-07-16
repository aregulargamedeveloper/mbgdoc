# How to : Use value modifiers

Value modifiers are an integral part of the mbg system.

Using them is similar to script signals, they are reusable types.

Value modifiers are numbers, you can add to them, multiply them, divide them, subtract from them, min/max them, and exponentiate them. Each "Modification" applied to your modifier has a operator and a value, the operator is the "action" to apply to the value modifier, so for example "\*" for multiplication, or "min" for clamping the number under \<VALUE>.&#x20;



sample code:<br>

```lua
local ValueModifiers = require(<PATH_TO_MODULE>)

local speedmodifier = ValueModifiers.new(16)

speedmodifier.ValueRefreshed:Connect(function(val)
    print(`The new value is: {val}`)
    --character.Humanoid.WalkSpeed = val
    --^ EXAMPLE
end)

local modification_1 = speedmodifier:AddModifier({},"+",1) -- adds one to the speed
local modification_2 = speedmodifier:AddModifier({},"*",2) --.. then multiplies it by 2

task.wait(5)

modification_1:RemoveModifier() -- removes the extra one from it

task.wait(3)

modification_2:RemoveModifier() -- now removes the *2 modification

-- the value goes back to 16 here...
```



Heres the methods:\
`module.new(defaultvalue:number,autorefresh:boolean) -> valuemodifier`

`export type ValueModifier = {`\
&#x20;`operator: string, -- "+", "-", "*", "/", "^","min","max"`\
&#x20;`value: number, -- the numeric value`\
&#x20;`tags: {string}, -- list of tags`\
&#x20;`parentModification: any?,-- reference to the parent modifier object`\
&#x20;`RemoveModifier: (self: ValueModifier) -> (),`\
&#x20;`ChangeModifierValue: (self: ValueModifier,NewValue : number) -> ()`\
`}`

`export type ModifierCollection = {`\
&#x20;`Modifiers: {ValueModifier},`\
&#x20;`DefaultValue: number,`\
&#x20;`AutoRefresh: boolean,`\
&#x20;`ValueRefreshed: scriptsignal.scriptsignal,`\
&#x20;`AddModifier: (self: ModifierCollection, tags: {string}, modifiertype: string, value:  number, index: number?) -> ValueModifier,`\
&#x20;`RemoveModifier: (self: ModifierCollection, modifiertag: string) -> (),`\
&#x20;`FindModifiers: (self: ModifierCollection, modifiertag: string) -> {ValueModifier},`\
&#x20;`GetAllModifiers: (self: ModifierCollection) -> {ValueModifier},`\
&#x20;`Refresh: (self: ModifierCollection) -> number`\
`}`<br>

