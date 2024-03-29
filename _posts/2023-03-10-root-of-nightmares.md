---
title: "Root of Nightmares"
category: destiny
tags: raids
---

{% if site.data.destiny.power.min > site.data.destiny.raids.ron.max_enemy_power %}
{% assign power = site.data.destiny.power.min %}
{% else %}
{% assign power = site.data.destiny.raids.ron.max_enemy_power %}
{% endif %}

# Prereading

- This isn't a guide, this is a mechanic overview. There's many ways to handle these mechanics - do whatever's best for your raid team.
- Power for final encounter is {{power}} on Legend difficulty and {{site.data.destiny.power.max | plus: 30}} on Master difficulty.
- Enemy type for the entire raid is Shadow Legion Cabal. Final boss might be counted as Shadow Legion, but I haven't tested it.

## Ammo Generation
The DPS checks in the raid aren't tight, but if an extra kick is needed for DPS then the following options are available:
- Every encounter has several major enemies for Bricks from Beyond.
- Additionally, every encounter has several finishable minibosses.

---

# Deepsight Chest {#deepsight}

Before the first large dropdown after a couple of small packs of Cabal, there is an overgrowth on the left side of the wall with 3 flowers, each containing a glowing orb. They will either be glowing dark orange (AKA dark) or glowing light blue (AKA light). There are three side rooms in the raid that require a specific link to be made for each room (explained in the next section), respective of the left-to-right ordering in this room. When a node resolves, a text string will print in the kill feed depending on if it was successful or not:
- ```Your actions take root...``` denotes that the node was correct
- ```Your spoils are irreversibly altered...``` denotes that the node was incorrect
- ```A great harvest awaits...``` denotes that all 3 nodes are correct

## Locations
The three rooms are as follows:
- In the ship leading to the first encounter, continue to the right instead of ascending the root.
- Inside the broken ship found at a left fork during the climb to the third encounter.
- At the end of the right-side branching path before the final encounter.

---

# {{ site.data.destiny.raids.ron.encounters[0].objective }} {% include destiny/champions.md champ_type="barrier" style='width=26px' %} {#{{ site.data.destiny.raids.ron.encounters[0].area | downcase | url_encode}}}
[Encounter map can be found here.](https://i.imgur.com/Tl1w4rK.jpeg)

## Objective
The objective of the encounter is to complete all four node chains.

### TL;DR
- Shoot glowing node while standing on the plate to get {{ site.data.destiny.raids.ron.statuses.light_field.name }} and reveal next node location
- When Terror expires, raid wipes
- Activate next node with {{ site.data.destiny.raids.ron.statuses.light_field.name }} to extend chain
- Complete a node chain to stop the timer and continue to the next set
- Kill Psions to spawn Tormentors and {% include destiny/champions.md champ_type='barrier' enemy='Colossi' style='width=10px' name='true' %}
- Kill Tormentors to extend the wipe timer

## Mechanics
### Nodes / "Pots"

Nodes are the primary raid mechanic for most encounters. **Node functionality is expanded per encounter.** Descriptions within will be encounter-specific. {%capture explanation_node%}All nodes in any encounter contain a ridged plate and pointed tip. Nodes have several different states, each one can be identified by a glowing aura and/or a floating object above the tip. The nodes give hitmarkers from either a non-ranged melee attack on the plate or weapon usage on the floating object. Can be activated by attacking the node under certain conditions and requires the player who activated it to be within roughly melee distance of the tip.{%endcapture%}

#### **Node Chains** / Node Sets

This encounter has four sets of nodes, each set longer than the last one by one node. Initial node chain is five nodes long. Upon completing the node chain, {{ site.data.destiny.raids.ron.statuses.wipe_timer.name }} will be removed from all players, denoted with the killfeed line ```His hatred halts...```. When a new node chain starts, the debuff comes back with the kill log: ```His hatred blooms once more...```. When a chain is finished, a couple sets of enemies will spawn, including a Centurion.

#### **{{ site.data.destiny.raids.ron.mechanics.light_node }}** / "Light Node" / "Light Seed"

{%capture explanation_light_node%}A node with a Seed of Light floating above the tip. If the node is emitting a blue aura and becomes activated, it will grant the {{ site.data.destiny.raids.ron.statuses.light_field.name }} buff to all players inside while removing that buff from any player that has it and emits a partial blue line to a node that can be linked. The {{ site.data.destiny.raids.ron.mechanics.light_node }} containing an aura is located at two node positions back from the last node linked in the chain, or the first node in the chain otherwise. If activated by someone who shot the last {{ site.data.destiny.raids.ron.mechanics.light_node }} with an aura and currently has {{ site.data.destiny.raids.ron.statuses.light_field.name }} before activating the next {{ site.data.destiny.raids.ron.mechanics.link_node }} in its chain, the node chain becomes disrupted for roughly 15 seconds with the text ```A node of splendor has been disrupted```.{%endcapture%}{{explanation_light_node}} Small swarms of Legionaries appear to spawn from nearby doors whenever a node is activated (testing needed).

#### **{{ site.data.destiny.raids.ron.mechanics.link_node }}**

A node with a floating ball of black liquid above the tip, with a disjointed partial line to the most recently activated aura node in its chain. If the node is activated by a player with the {{ site.data.destiny.raids.ron.statuses.light_field.name }} buff, that player's buff becomes consumed and the node blooms into a {{ site.data.destiny.raids.ron.mechanics.light_node }}.

### Statuses

#### **{{ site.data.destiny.raids.ron.statuses.wipe_timer.name }}**

Lasts {{ site.data.destiny.raids.ron.statuses.wipe_timer.time }} seconds. Gained when a phase starts. When the timer times out, the raid wipes after a short delay. Removed upon node chain completion or extended upon {{ site.data.destiny.raids.ron.special_enemies.tormentor }} death.

#### **{{ site.data.destiny.raids.ron.statuses.light_field.name }}**

{% capture description_light_field %}Lasts {{ site.data.destiny.raids.ron.statuses.light_field.time }} seconds. Gained from being on a {{ site.data.destiny.raids.ron.mechanics.light_node }} when it activates. Consumed when extending the node chain by activating a {{ site.data.destiny.raids.ron.mechanics.link_node | downcase}} when it is emitting a blue line.{%endcapture%}{{ description_light_field }}

### Special Enemies
#### **Psion (Shielded)**

During each phase, two shielded elite Psions spawn with the killfeed line ```An adherent of torment has appeared```. If they are both killed, a {% include destiny/champions.md champ_type='barrier' enemy='Minigun Colossus' style='width=10px' name='true' %} and {{ site.data.destiny.raids.ron.special_enemies.tormentor }} will spawn. This can occur up to three times per phase (testing needed).

#### **{{ site.data.destiny.raids.ron.special_enemies.tormentor }}**

A recurring Tormentor boss, spawned after Psions die (log line: ```Pain calls forth a Tormentor```). Killing them extends the {{ site.data.destiny.raids.ron.statuses.wipe_timer.name }} timer by 34 seconds denoted with the killfeed line ```His hatred is momentarily delayed...```.

## Challenge: Illuminated Torment
Any time a {{ site.data.destiny.raids.ron.special_enemies.tormentor }} is slain, the final blow must be from a player with {{ site.data.destiny.raids.ron.statuses.light_field.name }}.

## Encounter Triumph: Psionic Surge
Each set of Psions must be killed within 1 second of each other.

## Master Differences
- Each Centurion from the node chain resolution spawn wave is upgraded to a {% include destiny/champions.md champ_type='barrier' enemy='Railgun Colossus' style='width=10px' name='true' %}.

## Rewards
One of the following:
- {{ site.data.destiny.raids.ron.items.auto_rifle }} (Legend only)
- {{ site.data.destiny.raids.ron.items.shotgun }} (Legend only)
- {{ site.data.destiny.raids.ron.items.heavy_grenade_launcher }} (Legend only)
- Headpiece
- Arms

If the challenge has been completed on Master:
- {{ site.data.destiny.raids.ron.items.sidearm }} {{ site.data.destiny.raids.ron.items.adept_title }}

---

# Path to {{ site.data.destiny.raids.ron.encounters[1].area }}

## Mechanics
### Jump Pads
The easiest way to kill your flawless run if you're a Warlock. They are activated by damaging a Pyramid Shard in front of it and will launch whatever's in its path. As with all physics-related nonsense in Destiny, it is tied to both angle of approach, momentum and FPS. It can and will launch you into an unrecoverable freefall without Grapple, when hit with sufficient momentum.

## Hidden Chest
While climbing the final root in the chasm with the Aspirants of {{ site.data.destiny.raids.ron.bosses[1].name }}, there is a door directly behind two Psions. Defeat the {{ site.data.destiny.raids.ron.special_enemies.tormentor }} within to spawn the chest. Note that coming back from the second encounter to grab this chest will cause enemies to not spawn and the Tormentor will be t-posing while invulnerable.

---

# {{ site.data.destiny.raids.ron.encounters[1].objective }} {% include destiny/champions.md champ_type="barrier" style='width=26px' %} {#{{ site.data.destiny.raids.ron.encounters[1].area | downcase | url_encode }}}

[Encounter map can be found here.](https://i.imgur.com/P1dxxLy.jpeg) If you accidentally make a "Refuge" buff at any time during this encounter, it is irrelevant for this encounter and can be safely ignored.

## Objective
The objective of the encounter is to grow each floor's node chains.

### TL;DR
- Complete both zig-zagging node chains to stop the wipe timer
- Kill all {{ site.data.destiny.raids.ron.special_enemies.shielded_cabal }}s by using that side's buff

## Mechanics
### Jump Pads
Same as before. There are three on each side that launch across the map, as well as a fourth one that launches to the next floor that appears when the floor is completed, excluding the final floor.

### Nodes / "Pots"
Identical to the first encounter. {{explanation_node}}

#### **Node Chains** / Node Sets
This encounter has two chains of nodes per floor, one Light and one Dark. Each node chain is six nodes long and every successive node changes sides - they are completely static and never change order. Upon completing 4 nodes of a side's color, a {% include destiny/champions.md champ_type='barrier' enemy='Minigun Colossus' style='width=10px' name='true' %} will spawn at the door closest to that side's final node. Upon completing all 12 nodes on a floor, {{ site.data.destiny.raids.ron.statuses.floor_timer.name }} will be removed from all players and print the text ```Your ascent is blocked by interlopers```, spawning several {{ site.data.destiny.raids.ron.special_enemies.shielded_cabal }}s.

##### **Encounter Softlock**
There is a presumed bug with the encounter currently that if only one side's nodes are completed and their aura is activated, it will cause the aura on the other side to not spawn on their second to last node.

#### **{{ site.data.destiny.raids.ron.mechanics.light_node }}** / "Light Node" / "Light Seed"
Identical to the first encounter. {{explanation_light_node}} Small swarms of Shadow Legion Legionaries appear to spawn from nearby doors whenever a node is activated (testing needed).

#### **{{ site.data.destiny.raids.ron.mechanics.dark_node }}** / "Dark Node" / "Dark Seed"
Mechanically similar to {{ site.data.destiny.raids.ron.mechanics.light_node }}, but Dark-themed instead of Light-themed. {%capture explanation_dark_node%}A node with a Seed of Darkness floating above the tip. If the node is emitting an orange aura and is activated, it will grant the {{ site.data.destiny.raids.ron.statuses.dark_field.name }} buff to all players inside while removing that buff from any player that has it and emits a partial orange line to a node that can be linked. containing an aura is located at two node positions back from the last node linked in the chain, or the first node in the chain otherwise. If activated by someone who shot the last {{ site.data.destiny.raids.ron.mechanics.dark_node }} with an aura and currently has {{ site.data.destiny.raids.ron.statuses.dark_field.name }} before activating the next {{ site.data.destiny.raids.ron.mechanics.link_node }} in its chain, the node chain becomes disrupted for roughly 15 seconds with the text ```A node of decay has been disrupted```.{%endcapture%}{{explanation_dark_node}}

#### **{{ site.data.destiny.raids.ron.mechanics.link_node }}**
Identical to the first encounter, but supports {{ site.data.destiny.raids.ron.statuses.dark_field.name }} now. {%capture explanation_link_node%}A node with a floating ball of black liquid above the tip, with a disjointed partial line to the most recently activated aura node in its chain. If activated by a player with the buff that matches the theme of the line, it will transform into a node matching the buff's theme and consume the buff.{%endcapture%}{{explanation_link_node}}

### Statuses

#### **{{ site.data.destiny.raids.ron.statuses.floor_timer.name }}**
Lasts {{ site.data.destiny.raids.ron.statuses.floor_timer.time }} seconds. Gained when a phase starts. A phase starts either when a Field buff is gained for the first time on a new floor, or after roughly 10 seconds when the following text is printed in the kill log: ```Energy travels upwards, beckoning you```. When the timer times out, the raid wipes after a short delay. Removed upon the floor's nodes being completed.

#### **{{ site.data.destiny.raids.ron.statuses.light_field.name }}**
Same as the first encounter. {{description_light_field}}

#### **{{ site.data.destiny.raids.ron.statuses.dark_field.name }}**
Mechanically similar to {{ site.data.destiny.raids.ron.statuses.light_field.name }}. Dark-themed instead of Light-themed. {% capture description_dark_field %}Lasts {{ site.data.destiny.raids.ron.statuses.dark_field.time }} seconds. Gained from being on a {{ site.data.destiny.raids.ron.mechanics.dark_node }} when it activates. Consumed when extending the node chain by activating a {{ site.data.destiny.raids.ron.mechanics.link_node | downcase}} when it is emitting an orange line.{%endcapture%}{{description_dark_field}}

### Special Enemies
#### **{{ site.data.destiny.raids.ron.special_enemies.shielded_cabal }} of Splendor / Decay**
Also referred to as Sunblighted enemies. Shadow Cabal enemies that are immune to all damage from players without the matching Field. They spawn periodically, with position changing depending on how many nodes have been completed on the side they spawn on.
- Exclusively minor Centurions passively(?) spawn until a side has been completed
- A Psion, boss Centurion and Legionary spawn on each side when a floor's nodes have been completed.

## Challenge: Crossfire
Challenge details unknown until April 4th, 2023.

## Encounter Triumph: Shields Up
No {{ site.data.destiny.raids.ron.special_enemies.shielded_cabal }}s can be killed while {{ site.data.destiny.raids.ron.statuses.floor_timer.name }} is active.

## Master Differences
- Unknown. Supposedly an {% include destiny/champions.md champ_type='unstop' enemy='Incendior' style='width=10px' name='true' %} spawns periodically.

## Rewards
One of the following:
- {{ site.data.destiny.raids.ron.items.sidearm }} (Legend only)
- {{ site.data.destiny.raids.ron.items.shotgun }} (Legend only)
- {{ site.data.destiny.raids.ron.items.heavy_grenade_launcher }} (Legend only)
- Arms

---

# Path to {{ site.data.destiny.raids.ron.encounters[2].area }}
To keep this section brief, all mechanic rehashes will be omitted.

## Objective
Reach the end of the Overwhelming Energy gauntlet.

### TL;DR
- Get {{ site.data.destiny.raids.ron.statuses.light_field.name }}
- Activate {{ site.data.destiny.raids.ron.mechanics.dark_node }} with {{ site.data.destiny.raids.ron.statuses.light_field.name }} active
- Enjoy immunity to the wipe mechanic

## Mechanics

### Nodes / "Pots"

#### **{{ site.data.destiny.raids.ron.mechanics.light_node }}** / "Light Node" / "Light Seed"
Same as normal, but every node has an aura. Nodes cannot be disrupted.

#### **{{ site.data.destiny.raids.ron.mechanics.dark_node }}** / "Dark Node" / "Dark Seed"
Same as normal.

### Statuses

#### **{{ site.data.destiny.raids.ron.statuses.dark_refuge.name }}**
{%capture explanation_dark_refuge%}Lasts {{ site.data.destiny.raids.ron.statuses.dark_refuge.time }} seconds. Provides immunity to Overwhelming Energy. Continously applied to any players standing on or somewhat above an activated {{ site.data.destiny.raids.ron.mechanics.dark_node }}. Activation lifetime is roughly 8 seconds and the plate will glow orange while activated. The node activates when a player interacts with the node while in possession of a {{ site.data.destiny.raids.ron.statuses.light_field.name }} buff. Gaining a Refuge will overwrite any active ones.{%endcapture%}{{explanation_dark_refuge}}

## Hidden Chest
The second hidden chest behind a closed door on top of the Pyramid, after the first group door. The door is openable by hitting a hidden switch located below the right side of the Pyramid.

As a reminder, there's a red chest node in this zone before the first group door.

---

# {{ site.data.destiny.raids.ron.encounters[2].objective }} {#{{ site.data.destiny.raids.ron.encounters[2].area | downcase | url_encode}}}
Caretaker 2: Electric Boogaloo. [Encounter map can be found here.](https://i.imgur.com/nIhkjxF.jpeg) I recommend not using those callouts as internally inconsistent callouts are bad. I recommend left/mid/right as it works for every set of callouts and is directionally absolute.

## Objective
The objective of the encounter is to defeat {{ site.data.destiny.raids.ron.bosses[0].full_title }}.

### TL;DR
- Kill Centurions to spawn {{ site.data.destiny.raids.ron.special_enemies.planet_colo }}s
- Kill {{ site.data.destiny.raids.ron.special_enemies.planet_colo }} to see planet colours
- Move light planets to the left and vice-versa
- Repeat the above but move matching planets to middle plates instead
- Gain matching colored buffs from said plates to damage boss

## Mechanics

### Enrage Timer
There is a hidden timer to reach damage phase, which is roughly 3 minutes (testing required), which is roughly enough time for 3 iterations of {{ site.data.destiny.raids.ron.statuses.planet_phase.name }}. It can be seen as the Shadow Cabal logo embedded on the floor near where the boss spawns. The symbol progressively fills up with orange. When it's full, the boss will cast {{ site.data.destiny.raids.ron.bosses[0].special_attacks[0].name }}.

### Planets
Each planet has a hidden alignment to either Light or Dark. There are 5 planets per side and planets can only be moved by swapping position with another planet. Light planets must be placed on the left side of the room and vice-versa to enter the Inner Plate Phase, which leads to damage phase. The planets have collision boxes.

#### **Planet Plates**
The black doritoes each contain three planets. At the start of each phase, each set of three planets contains one planet that is the wrong alignment relative to the side it's on. During {{ site.data.destiny.raids.ron.statuses.planet_phase.name }}, each plate's planets can be interacted with. Each set of three can only be interacted with once per {{ site.data.destiny.raids.ron.statuses.planet_phase.name }} and grants {{ site.data.destiny.raids.ron.statuses.see_planets.name }}. Taking {{ site.data.destiny.raids.ron.statuses.see_planets.name }} from all four plates during Inner Plate Phase will wipe the raid.

### Pyramid Shard
Only interactable during {{ site.data.destiny.raids.ron.statuses.planet_phase.name }}. Shooting the node moves any correct planets and disregards any incorrect movements. If only incorrect movements were provided, Honored Centurions will spawn (verification needed).

### Alignment Plates
Only interactable during the Inner Plate Phase and the damage phase. During the Inner Plate Phase, they become interactable as destination as part of {{ site.data.destiny.raids.ron.statuses.move_planets.name }}. During the damage phase, each plate grants a Field-type buff corresponding to what color it glows. When all glows are gone, damage phase ends. During Final Stand, all plates glow Dark.

### Statuses

#### **{{ site.data.destiny.raids.ron.statuses.planet_phase.name }}**
Lasts roughly 33 seconds. During this time, planets and/or plates can be interacted with, depending on phase. Once four {{ site.data.destiny.raids.ron.statuses.move_planets.name }}s have been consumed, the phase ends early.

#### **{{ site.data.destiny.raids.ron.statuses.see_planets.name }}**
Active until either {{ site.data.destiny.raids.ron.statuses.planet_phase.name }} ends or until {{ site.data.destiny.raids.ron.statuses.move_planets.name }} is obtained. Allows the user to see which planet has which energy alignment. Obtained by defeating a {{ site.data.destiny.raids.ron.special_enemies.planet_colo}}.

#### **{{ site.data.destiny.raids.ron.statuses.move_planets.name }}**
Obtained from interacting with a planet on top of a planet plate. Active until a destination is interacted with or when {{ site.data.destiny.raids.ron.statuses.planet_phase.name }} ends. Attempts to move the starting planet to the destination provided.

#### **{{ site.data.destiny.raids.ron.statuses.light_field.name }}**
Lasts for 7 seconds. Allows {{ site.data.destiny.raids.ron.bosses[0].name }} to take damage during damage phase while he is aligned to Light. Obtained from the an alignment plate of the matching color during damage phase.

#### **{{ site.data.destiny.raids.ron.statuses.dark_field.name }}**
Lasts for 7 seconds. Allows {{ site.data.destiny.raids.ron.bosses[0].name }} to take damage during damage phase while he is aligned to Dark. Obtained from the an alignment plate of the matching color during damage phase.

### Special Enemies

#### **Honored Centurion**
Spawns as part of the progressive enemy spawns. One spawns on each side, with a Solar shield. When a side's Centurion dies, they spawn a {{ site.data.destiny.raids.ron.special_enemies.planet_colo}} on their side's planet plates.

#### **{{ site.data.destiny.raids.ron.special_enemies.planet_colo}}**
A miniboss Minigun Colossus. Spawns on each plate after the Centurion dies, respective of the side that it spawned from.

#### **{{ site.data.destiny.raids.ron.bosses[0].full_title }}**
Boss. As per every Destiny raid boss, he's immune to all damage until damage phase. Has a health gate per plate which requires additional testing to determine how it works. Has the Incendior moveset and hitboxes, in addition to the following special attacks:

##### **{{ site.data.destiny.raids.ron.bosses[0].special_attacks[0].name }}**
Wipe attack. Cast upon running out of time in the plate phases, inputting the wrong planets in the Inner Plate Phase or after resolving damage phase {{ site.data.destiny.raids.ron.bosses[0].enrage }} times. Presumably also cast during Final Stand if the DPS check fails.

##### **{{ site.data.destiny.raids.ron.bosses[0].special_attacks[1].name }}**
Cast upon taking enough damage during damage phase or presumably taking more than 7 seconds to trigger his health gate. Upon cast, he switches alignment - (```The Explicator shifts focus```). Creeps from the boss towards the first activated plate corresponding to his alignment or, presumably, the center plate otherwise. After being cast 3 times, damage phase ends and the Outer Plate Phase starts.

## Challenge: Cosmic Equilibrium
Challenge details unknown until April 11th, 2023 (when GMs drop).

## Encounter Triumph: Singular Orbit
A player cannot gain {{ site.data.destiny.raids.ron.statuses.see_planets.name }} twice per damage phase.

## Master Differences
- Each {{ site.data.destiny.raids.ron.special_enemies.planet_colo}} is upgraded to a {% include destiny/champions.md champ_type='barrier' enemy='Railgun Colossus' style='width=10px' name='true' %}.

## Rewards
One of the following:
- {{ site.data.destiny.raids.ron.items.auto_rifle }} (Legend only)
- {{ site.data.destiny.raids.ron.items.sidearm }} (Legend only)
- {{ site.data.destiny.raids.ron.items.heavy_grenade_launcher }} (Legend only)
- Boots
- Class Item

---

# Path to {{ site.data.destiny.raids.ron.encounters[3].area }}
As a reminder, there's a red chest node before starting the next encounter located on the final fork before Nezarec.

---

# {{ site.data.destiny.raids.ron.encounters[3].objective }} {#{{ site.data.destiny.raids.ron.encounters[3].area | downcase | url_encode }}}
[Encounter map can be found here.](https://i.imgur.com/Q0o5sWn.jpeg)

## Objective
The objective of the encounter is to defeat {{ site.data.destiny.raids.ron.bosses[1].full_title }}.

### TL;DR
- Shoot {{ site.data.destiny.raids.ron.bosses[1].name }}'s exposed stomach to break soft detains and grab temporary aggro
- Complete both node chains to enter damage phase
- If node runners are too slow, shoot {{ site.data.destiny.raids.ron.bosses[1].name }}'s exposed shoulders to reveal wipe attack type
- Then complete and obtain matching Refuge to avoid mass death

## Mechanics

### Enrage Timer
There is a hidden timer to reach damage phase, which is roughly one minute. (testing required). Failure to break his shoulders after this timer resolves **after reaching damage phase once** will result in the boss casting {{ site.data.destiny.raids.ron.bosses[1].special_attacks[0].name }}, wiping the raid. Otherwise, he will cast a normal Overwhelming attack.

### Nodes / "Pots"
Identical to the second encounter. {{explanation_node}}

#### **Node Chains** / Node Sets
There are two sets of seven nodes each in this encounter. The {{ site.data.destiny.raids.ron.mechanics.light_node }} locations are exclusively on the left side of the map and vice-versa. The second position for each node is static. The third position onwards will zig-zag until the final node (verification needed).

#### **{{ site.data.destiny.raids.ron.mechanics.light_node }}** / "Light Node" / "Light Seed"
Same as normal. {{explanation_light_node}}

#### **{{ site.data.destiny.raids.ron.mechanics.dark_node }}** / "Dark Node" / "Dark Seed"
Same as normal. {{explanation_dark_node}}

#### **{{ site.data.destiny.raids.ron.mechanics.link_node }}**
Same as normal. {{explanation_link_node}}

### Statuses

#### **{{ site.data.destiny.raids.ron.statuses.dark_refuge.name }}**
Same as before, but provides immunity to Overwhelming Resonance now instead of Overwhelming Energy. {{explanation_dark_refuge | replace: "Energy", "Resonance" }}

#### **{{ site.data.destiny.raids.ron.statuses.light_refuge.name }}**
Functionally identical to {{ site.data.destiny.raids.ron.statuses.dark_refuge.name }}, but Light-flavoured instead of Dark. Lasts {{ site.data.destiny.raids.ron.statuses.light_refuge.time }} seconds. Provides immunity to Overwhelming Light. Continously applied to any players standing on or somewhat above an activated {{ site.data.destiny.raids.ron.mechanics.light_node }}. Activation lifetime is roughly 8 seconds and the plate will glow blue while activated. The node activates when a player interacts with the node while in possession of a {{ site.data.destiny.raids.ron.statuses.dark_field.name }} buff. Gaining a Refuge will overwrite any active ones.

#### **{{ site.data.destiny.raids.ron.statuses.hatred.name }}**
Has two variants depending on boss state. Further explained in the {{site.data.destiny.raids.ron.bosses[1].special_attacks[5].name}} section.

### Special Enemies
#### **{{ site.data.destiny.raids.ron.bosses[1].full_title }}**
Same as the {{site.data.destiny.raids.ron.special_enemies.tormentor}}, but with minor alterations to existing attacks, new attacks and slightly modified AI:

##### **{{ site.data.destiny.raids.ron.bosses[1].special_attacks[5].name }}**
Two variants, each of them have a debuff of the matching name associated with it.
- At the start of each node phase, {{ site.data.destiny.raids.ron.bosses[1].name }} will channel and reveal his shoulder and stomach weak spots. During this time, he will progressively debuff players. Each debuffed player will take a continous and persistent AoE knockup attack at the victim's feet, dealing Void damage (verification required). The attack will persist until the second attack starts, if at all.
- Lasts {{site.data.destiny.raids.ron.statuses.hatred.time}} seconds. Obtained by shooting {{ site.data.destiny.raids.ron.bosses[1].name }}'s chest weakspot. Stops the previous attack. Draws {{ site.data.destiny.raids.ron.bosses[1].name }}'s aggro, enabling the melee attacks in his moveset.

##### **{{ site.data.destiny.raids.ron.bosses[1].special_attacks[0].name }}**
Hard wipe attack. Cast upon the enrage timer resolving without shoulders being broken, after resolving damage phase {{ site.data.destiny.raids.ron.bosses[1].enrage }} times or taking too long during Final Stand.

##### **{{ site.data.destiny.raids.ron.bosses[1].special_attacks[1].name }}**
Soft wipe attack. Cast upon the enrage timer resolving with shoulders being broken and glowing blue. Deals no damage to players with {{ site.data.destiny.raids.ron.statuses.light_refuge.name }}.

##### **{{ site.data.destiny.raids.ron.bosses[1].special_attacks[2].name }}**
Soft wipe attack. Cast upon the enrage timer resolving with shoulders being broken and glowing orange. Deals no damage to players with {{ site.data.destiny.raids.ron.statuses.dark_refuge.name }}.

##### **{{ site.data.destiny.raids.ron.bosses[1].special_attacks[4].name }}**
Homing capabilities heavily increased, similar to Winter's Wrath projectiles. Used when the targeted player is outside of {{site.data.destiny.raids.ron.bosses[1].special_attacks[3].name}} attack distance.

##### **{{ site.data.destiny.raids.ron.bosses[1].special_attacks[6].name }}**
Always used before the channel for {{site.data.destiny.raids.ron.bosses[1].special_attacks[5].name}} and never used otherwise.

##### **Dark Harvest**
Not used. Being extremely close to {{ site.data.destiny.raids.ron.bosses[1].name }} after {{ site.data.destiny.raids.ron.bosses[1].special_attacks[3].name }} can break his AI due to this attack not being present in his moveset.

## Challenge: All Hands
Challenge details unknown until April 18th, 2023.

## Encounter Triumph: Synchronicity
If a node chain is finished, an accompanying node chain must be completed within 5 seconds of each other.

## Master Differences
- Each Honored Colossus is upgraded to a {% include destiny/champions.md champ_type='barrier' enemy='Railgun Colossus' style='width=10px' name='true' %}.

## Rewards
One of the following:
- {{ site.data.destiny.raids.ron.items.sidearm }} (Legend only)
- {{ site.data.destiny.raids.ron.items.auto_rifle }} (Legend only)
- {{ site.data.destiny.raids.ron.items.trace_rifle }} (Legend only)
- {{ site.data.destiny.raids.ron.items.shotgun }} (Legend only)
- {{ site.data.destiny.raids.ron.items.linear_fusion_rifle }} (Legend only)
- {{ site.data.destiny.raids.ron.items.heavy_grenade_launcher }} (Legend only)
- Headpiece
- Class Item

Additionally, if the raid exotic table was hit (presumably ~5% chance before bad luck protection):
- {{ site.data.destiny.raids.ron.items.exotic }}

The node red chest grants the following:
- Random RoN raid weapon with Deepsight Resonance with priority towards weapons that do not have their patterns completed

---

# Master Difficulty {#master}

Master difficulty applies the following changes to the raid:
- Master difficulty modifiers become applied
- Each encounter gets additional champions

## Reward Adjustments

All encounter chest rewards are overwritten with high-stat armor, specializing on a specific stat per a weekly rotation. All challenge chest rewards are overwritten with encounter-specific Adept weapons from the raid. The elective difficulty challenge chests share a different lockout than the normal mode challenge chests.

---

# End {#end}

## Spoils Chest
Weapons and armor that have been obtained from the raid can be purchased here. The first weapon purchase per week has guaranteed Deepsight Resonance, per week on an account-wide lockout. Subsequent purchases cannot be Deepsighted.

## Special Thanks
- [brekcut](https://www.twitch.tv/brekcut) for proofreading, recording the day1 and providing feedback.