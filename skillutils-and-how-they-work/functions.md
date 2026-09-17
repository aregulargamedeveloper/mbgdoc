---
description: The functions that you can call on skill utils
icon: function
---

# functions

## <mark style="color:$primary;">Primary</mark>

{% hint style="info" %}
Main tools!
{% endhint %}

#### ~~:stun~~ REMOVED use statuseffects

* arguments
  * Target : _humanoiddata_, the target to stun
  * Strong : _boolean_, whether to cancel running moves on selected player _(optional, true default)_
  * persistant : boolean, wether it cancels when the move does _(optional, true default)_
* returns
  * stun object: you can run :cancel on it to stop the stun

#### ~~:ragdoll~~ REMOVED use statuseffects

* arguments
  * Target : _humanoiddata_, the target to ragdoll
  * Knockback : Vector3, the direction to knock the player back _(optional)_
* returns
  * ragdoll object: you can run :cancel on it to stop the ragdoll
* extra info:
  * ragdolls set iframe level to 20 if it was already below 20

#### ~~:setIFrameValue~~ REMOVED use value modifiers

* arguments
  * Target : humanoiddata
  * value : number, the iframe level to set
* returns: nothing

#### ~~:hitbox~~ DEPRECATED, RENAMED TO :blockHitbox

*   arguments

    * hitboxparams : table:

    <pre><code>Ignored : {} | Player,
    <strong>HitboxCFrame : () -> CFrame | CFrame,-- function returning a cframe or just a cframe
    </strong><strong>HitboxSize : () -> Vector3 | Vector3, -- function returning a vector3 or just a vector3
    </strong><strong>Power : number, -- iframe bypass level
    </strong><strong>Accuracy : number, -- how many times per second the hitbox is checked
    </strong><strong>MultipleDetections : boolean, -- if the hitboxx can hit a single player multiple times
    </strong></code></pre>
* returns: hitboxobject:
  * :cancel(), stops the hitbox
  * .touched, scriptsignal
    * target: who was hit
  * .hitUnstoppableUser, scriptsignal
    * target: who was attempted to be hit
  * .active, boolean, if the hitbox is active currently

#### :sphereHitbox

*   arguments

    * hitboxparams : table:

    <pre><code>ignored : {} | Player,
    <strong>hitboxPosition : () -> Vector3 | Vector3,-- function returning a vector3 or just a vector3
    </strong><strong>hitboxRadius : () -> number | number, -- function returning a vector3 or just a vector3
    </strong><strong>power : number, -- iframe bypass level
    </strong><strong>accuracy : number, -- how many times per second the hitbox is checked
    </strong><strong>multipleDetections : boolean, -- if the hitboxx can hit a single player multiple times
    </strong></code></pre>
* returns: hitboxobject:
  * :cancel(), stops the hitbox
  * .touched, scriptsignal
    * target: who was hit
  * .hitUnstoppableUser, scriptsignal
    * target: who was attempted to be hit
  * .active, boolean, if the hitbox is active currently

## _<mark style="color:$primary;">**Placetakers**</mark>_&#x20;

{% hint style="info" %}
_**Use these instead of default roblox functions**_
{% endhint %}

#### :wait

* arguments
  * delay: number, time to wait
* returns: nothing
* extra info:
  * _**USE THIS IN PLACE OF task.wait!!!!!!!!!!!!!!!!!**_
  * waits based on skillutils.speed value

#### :delay

* arguments
  * delay: number, time to wait
  * function: function,  the function to run after _delay_ amount of time
* returns: nothing
* extra info:
  * _**USE THIS IN PLACE OF task.wait!!!!!!!!!!!!!!!!!**_
  * delays based on skillutils.speed value

#### :loadAnimation

* arguments
  * Target: humanoid data, character, humanoid, or animator, which player to load the animation
  * animation: animation, a animation instance to load
* returns:&#x20;
  * animationtrack (:Play,:Cancel etc)
* extra info:
  * _**USE THIS IN PLACE OF animator:LoadAnimation!!!!!!!!!!!!!!!!!**_

#### :dealDamage

* arguments
  * Target: humanoid data, who to deal the damage to
  * amount: number, amount of damage to deal
  * clamptozero: boolean, makes sure the target doesnt die
* returns:
  * boolean, if clamptozero made a effect on the damage
    * <i class="fa-arrow-up">:arrow-up:</i>  use this for finishers
* extra info:
  * USE THIS IN PLACE OF humanoid:TakeDamage/humanoid.Health-=

#### :applyForce

* arguments
  * Target: humanoid data
  * direction: direction to apply the force in
  * debris: number, how long for the force to last
  * maxForce: the force's power
* returns: nothing
* extra info:
  * USE THIS IN PLACE OF ANY LINEAR FORCE APPLICATIONS
  * this isn't a simple utility because it has networking built into it

## Primarily Backend

{% hint style="info" %}
these are mostly used in backend but are able to be used in the move!
{% endhint %}

#### :selfDestruct

* Cancels the move and runs the cancel function

#### :abort

* Cancels the move without running the cancel function

