---
description: a reference to skillutils
icon: gear-code
---

# skillutils, and how they work

Skillutils (skill utilities) is an object passed in to every skill as the first parameter. It is used for everything skill related.

### What its used for

* saving data related to that specific move instance
* using various functionalities which are specific to skills
* getting various values related to the move
* the skill utils collects stuns, ragdolls, and other OOP objects related to your skill

## Default Values

* mainstun? :
  * a weak stun object applied to the skill
  * makes sure you cant use other moves during this skill
  * only exists if skill.usesdefaultstun is true or nil
* hitboxes :
  * &#x20;a list of hitboxes associated with the skill
* ragdolls
  * a list of ragdolls associated with the skill
* associatedanimations
  * a list of animations associated with the move
* appliedstuns
  * a list of stuns associated with the move
  * includes skillutils.mainstun
* skill
  * the table of the skill the skillutils is linked to
* plr
  * the humanoiddata the skill is linked to
* speed
  * the speed the move is running at (default 1)

