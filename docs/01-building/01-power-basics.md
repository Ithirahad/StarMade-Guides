# Power Basics

A ship core makes no power of its own. Without a reactor your thrusters run at only 5% of their strength and weapons, shields and other systems don't work, so every real ship needs a **reactor**.

This page covers the basics. See [Reactors](../02-ships/03-reactors.md) and [Chambers](../02-ships/04-chambers.md) for the details.

## Reactors and Stabilizers

**Reactor Power** blocks make power. All reactor blocks that touch each other form one **reactor**, and the more blocks it has, the more power it makes. There is no special shape: any group works.

A ship can have several reactors, but only one is **active** at a time. Inactive reactors make no power. You can switch the active reactor in the reactor menu (10 second cooldown).

**Reactor Stabilizer** blocks keep the active reactor stable:

- The first **10 reactor blocks** are free. After that you need **one stabilizer per reactor block** for 100% stability.
- Stabilizers can go **anywhere on the ship**, in as many groups as you like, at any distance from the reactor. Only your 20 biggest groups count.
- Below 100% stability your reactor still makes full power, but the ship takes **extra damage** from beams and explosions, up to 21× at 0%.

```scene
{ "height": 260,
  "blocks": [ { "from": [0,0,0], "to": [2,1,2], "block": "REACTOR_POWER" } ],
  "steps": [
    { "text": "18 Reactor Power blocks touching each other form one reactor.", "blocks": [] },
    { "text": "A separate group is a second reactor. Only one reactor is active at a time; switch between them in the reactor menu.",
      "blocks": [ { "from": [6,0,0], "to": [6,0,1], "block": "REACTOR_POWER" } ] },
    { "text": "The first 10 reactor blocks are free, so 18 blocks need 8 stabilizers. They can be split into groups anywhere on the ship.",
      "blocks": [ { "from": [0,0,6], "to": [3,0,6], "block": "REACTOR_STABILIZER" },
                  { "from": [-4,0,0], "to": [-4,0,3], "block": "REACTOR_STABILIZER" } ] },
    { "text": "A Reactor Conduit connects the reactor to a chamber.",
      "blocks": [ { "from": [1,2,1], "to": [1,3,1], "block": "REACTOR_CONDUIT", "orient": 2 },
                  { "from": [1,4,1], "to": [2,4,1], "block": "MOBILITY_CHAMBER" } ] } ] }
```

## Reactor Level

A reactor's **level** goes up by one for every **150 reactor blocks** (0–149 blocks is level 0). The level sets how big your chambers must be: at level 0 a single chamber block is enough, and each level after that needs about 7–8 more chamber blocks per chamber.

## Reactor Menu

Open the **Reactor Menu** with `Insert`, from the radial menu (`Tab`), or with the **REACTOR** button on the top bar while you are in a ship with a reactor.

![reactors_fig8.png](https://images.steamusercontent.com/ugc/2279448944260776147/400EEF1E43DF8653CB08D428BC65B29AA535D5D8/)

![reactors_fig9.png](https://images.steamusercontent.com/ugc/2279448944260892781/922E77078628FE6B556375E2F0C7733866256961/)

It shows everything about your reactors: size, level, power, stability and capacity. Use its previous/next buttons to switch the active reactor, and open the chamber tree from it.

## Chambers and Reactor Capacity

**Reactor Chambers** give your ship special bonuses and abilities. Connect them to the reactor (or to each other) with **Reactor Conduit** blocks. Each chamber uses some **Reactor Capacity** (RC), and you can't go over 100%.

To set up a chamber, open the reactor menu, select the unspecified chamber, press **Specify Chamber**, and pick an option. You can then upgrade it for a stronger effect at the cost of more RC.

![reactors_fig11.png](https://images.steamusercontent.com/ugc/2279448944261039736/6E1BEAA5CF92481FF59386D28BE15B1B4A109A48/)

![reactors_fig12.png](https://images.steamusercontent.com/ugc/2279448944261040189/AC23A9D2FD9F674DE1E893896A0CE7F8562554B4/)

There are eight chamber types:

| Chamber | What it does |
|---------|--------------|
| Defence | Shield capacity, armor HP and damage-type armor |
| FTL | Jump drive (distance, autocharge), jump inhibitors, warp gates |
| Logistics | Mining bonus, faster and cheaper factories, smaller cargo volume |
| Mass | Gravity fields |
| Mobility | Top speed, turn rate, thrust blast, anti-gravity |
| Power | Reactor boost and failsafe |
| Recon | Scanners: ores, cargo, cloaked ships |
| Stealth | Cloaking, jamming, anti lock-on |

See [Chambers](../02-ships/04-chambers.md) for each tree.
