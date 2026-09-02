---
description: The functions that you can call on skill utils
icon: function
---

# functions

## Primary

{% hint style="info" %}
Main tools!
{% endhint %}

#### ~~:Stun~~ DEPRECATED use statuseffects

* arguments
  * Target : _humanoiddata_, the target to stun
  * Strong : _boolean_, whether to cancel running moves on selected player _(optional, true default)_
  * persistant : boolean, wether it cancels when the move does _(optional, true default)_
* returns
  * stun object: you can run :cancel on it to stop the stun

#### ~~:Ragdoll~~ DEPRECATED use statuseffects

* arguments
  * Target : _humanoiddata_, the target to ragdoll
  * Knockback : Vector3, the direction to knock the player back _(optional)_
* returns
  * ragdoll object: you can run :cancel on it to stop the ragdoll
* extra info:
  * ragdolls set iframe level to 20 if it was already below 20

#### ~~:SetIFrameValue~~ DEPRECATED use value modifiers

* arguments
  * Target : humanoiddata
  * value : number, the iframe level to set
* returns: nothing

#### :Hitbox

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
  * .Touched, scriptsignal
    * target: who was hit
  * .HitUnstoppableUser, scriptsignal
    * target: who was attempted to be hit
  * .Active, boolean, if the hitbox is active currently

## _<mark style="color:$primary;">**Placetakers**</mark>_&#x20;

{% hint style="info" %}
_**Use these instead of default roblox functions**_
{% endhint %}

#### :Wait

* arguments
  * delay: number, time to wait
* returns: nothing
* extra info:
  * _**USE THIS IN PLACE OF task.wait!!!!!!!!!!!!!!!!!**_
  * waits based on skillutils.speed value

#### :Delay

* arguments
  * delay: number, time to wait
  * function: function,  the function to run after _delay_ amount of time
* returns: nothing
* extra info:
  * _**USE THIS IN PLACE OF task.wait!!!!!!!!!!!!!!!!!**_
  * delays based on skillutils.speed value

#### :LoadAnimation

* arguments
  * Target: humanoid data, character, humanoid, or animator, which player to load the animation
  * animation: animation, a animation instance to load
* returns:&#x20;
  * animationtrack (:Play,:Cancel etc)
* extra info:
  * _**USE THIS IN PLACE OF animator:LoadAnimation!!!!!!!!!!!!!!!!!**_

#### :DealDamage

* arguments
  * Target: humanoid data, who to deal the damage to
  * amount: number, amount of damage to deal
  * clamptozero: boolean, makes sure the target doesnt die
* returns:
  * boolean, if clamptozero made a effect on the damage
    * <i class="fa-arrow-up">:arrow-up:</i>  use this for finishers
* extra info:
  * USE THIS IN PLACE OF humanoid:TakeDamage/humanoid.Health-=

#### :ApplyForce

* arguments
  * Target: humanoid data
  * direction: direction to apply the force in
  * debris: number, how long for the force to last
  * maxforce: the force's power
* returns: nothing
* extra info:
  * USE THIS IN PLACE OF ANY LINEAR FORCE APPLICATIONS
  * this isnt a simple utility because it has networking built into it

## Simple Utilities

{% hint style="info" %}
These arent unique to skills, they are simply timesaver built in functions
{% endhint %}

#### :MakeAttractForce

* arguments
  * user1: humanoiddata, first player to apply the force from&#x20;
    * <i class="fa-arrow-up">:arrow-up:</i> (usually the player using the move)
  * user2: humanoiddata, the player to apply the force on
  * offset: cframe, the offset to apply it on
* returns: LineForce (you gotta change properties of this!)

## Primarily Backend

{% hint style="info" %}
these are mostly used in backend but are able to be used in the move!
{% endhint %}

#### :SelfDestruct

* Cancels the move and runs the cancel function

#### :Abort

* Cancels the move without running the cancel function

