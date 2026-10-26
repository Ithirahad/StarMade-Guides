# Ship & Turret AI

A ship, station turret or docked entity with a **BOBBY AI Module** can fly and fight on its own. Only one AI Module is allowed per ship.

## Setting Up AI

1. Place a **BOBBY AI Module** on the ship.
2. Press `R` on it to open the AI panel. You can also press `;` (or the **AI** button on the top bar) while you are in the ship.
3. Pick a **Type** and tick **Active**.

> Entering a ship's core or a cockpit turns its AI off. Turn it back on when you leave.

The AI also switches off if the ship's core overheats. A logic signal into the AI Module turns the AI on or off.

## Types

| Type | What it does |
|------|--------------|
| **Ship** | Hunts enemies within 3 sectors, flies to them and fights |
| **Turret** | Stays docked, turns to face targets in weapon range and fires |
| **Fleet** | Waits for orders from its fleet. See [Fleets](../05-ai-and-fleets/01-fleets.md) |

The game picks some of these for you:

- An entity docked on the last axis of a turret becomes a **Turret**. See [Docking & Turrets](../01-building/02-docking-and-turrets.md#turrets).
- A ship that joins a fleet becomes **Fleet** and turns on; when it leaves the fleet it goes back to **Ship**.

## Who the AI Attacks

The AI attacks whoever its faction is at war with. Pirates are enemies of everyone.

- A ship **without a faction** only fights Pirates (and other factions that attack neutrals).
- Docked turrets without their own faction use the host's faction.
- The AI never targets shops, cloaked ships, or anything in a protected sector.
- When a Ship AI is hit by an enemy, it turns on the attacker (at most once every 25 seconds).

## The AI Panel

### General

| Setting | What it does |
|---------|--------------|
| **Active** | Turns the AI on or off |
| **Type** | Ship, Turret or Fleet |
| **Remote Control** | Turrets only: lets the host's pilot aim the turrets (see below) |
| **Priority** | How to choose between targets: Random, Closest, Furthest, Weakest, Strongest, Lightest, Heaviest, Lowest shields, Highest shields |
| **Keep target until lost** | Stay on one target instead of picking again every scan |
| **Minimum range** | Ship AI: the distance to keep from its target. **Auto** fights up close |
| **Maximum range** | Ship AI: how far away it fights from. It can't be more than the range of your weapons. **Auto** uses your weapon range |
| **Multi-Output Fire Mode** | **Volley** makes every cannon and missile fire in volleys; **Simultaneous** leaves each weapon's own setting |
| **Missile Damage Prioritization** | Shown when **Missiles** is first in Aim At: shoot the missiles with the Highest or Lowest damage first, or Random |

### Aim At

An ordered list of what **turrets** shoot at: **Selected Target**, **Ships**, **Stations**, **Missiles**, **Astronauts** and **Asteroids**. Turn each one on or off and move it up or down; the turret goes for the first kind it finds. New AIs aim at Ships, Stations and Astronauts.

- **Selected Target:** the target the host's pilot has pinned for the AI (`X` while flying), or the host AI's own target.
- **Missiles:** point defence. Turrets shoot down enemy missiles in range.
- **Asteroids:** a turret with salvage beams mines nearby asteroids.

### Focus Fire

Pick which systems the AI shoots at on its target, in priority order: Reactors, Stabilizers, Chambers, Thrusters, Shield Rechargers, Shield Capacitors. With focus fire off, the AI aims at a random system on the target.

## How Ship AI Fights

- It flies to the target and stops a bit inside its weapon range (or at its Minimum range), then circles while firing.
- Against targets on a planet it makes **strafing runs** instead: dive, fire, pull up and turn back for another pass.
- A ship armed with only warheads rams its target.
- It steers around other ships and gas giants in its way.
- When it loses its target it stays where it is and searches again every few seconds. It doesn't flee, patrol or go home.
- Out of combat it uses its scanner; in combat it uses cloaking, jamming and jump inhibitors if it has them.
- With no thrusters it barely moves.

## How Turrets Fight

- Turrets only look for targets **within their weapon range**. The range sliders don't affect them.
- Turrets lead moving targets (except beam-only turrets).
- After 30 seconds without a target, a turret turns back to its starting rotation.

### Remote Control

With **Remote Control** on, the pilot of the host ship can select **Turret Control** on the hotbar. The turrets then aim wherever the pilot looks and fire when they click. With another slot selected, the turrets go back to picking their own targets.

## Weapons the AI Uses

- **Cannons, beams and missiles** linked to the core. It switches between them every half second.
- **Repair beams** on friendly ships that are damaged.
- **Salvage beams** on asteroids.

## Controlling Docked AI from the Host

| Action | How |
|--------|-----|
| Turn turret and docked AI on / off | `,` while flying |
| Reset turrets to their starting rotation | `.` while flying |
| Turrets On / Off, Act. all / Deact. all (non-turrets) | **Docks** section of the structure panel |
| Activate / Deactivate all AI turrets or docked AI | Rail Speed Controller panel |

`,` only affects docked entities that have an AI Module.
