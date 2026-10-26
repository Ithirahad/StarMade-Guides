# Docking & Turrets

StarMade uses a **rail-based docking system**. A ship docks to rail blocks on a station or another ship with a **Rail Docker** block. Rails handle fixed docking, turrets, moving platforms and elevators, cargo transfer, and automatic hangar docking.

## Rail Blocks

| Block | Role |
|-------|------|
| **Rail Docker** | Goes on the ship being docked; the connector end |
| **Rail Basic** | Standard rail on the host. Docked ships move along it in the direction of its arrow |
| **Rail Turret Axis** | Lets the docked entity rotate around one axis; chain two for a full turret |
| **Rail Rotator Clock Wise / Counter Clock Wise** | Turns a docked entity as it passes over |
| **Rail Mass Enhancer** | Raises how much docked mass the host can move at full speed |
| **Rail Speed Controller** | Sets how fast rails and rotators move |
| **Rail Load / Rail Unload** | Moves items between a docked ship's storage and the host's |
| **Pickup Point** | Docks ships automatically when they come close |
| **Pickup Rail** | A rail meant to sit next to a Pickup Point |
| **Shootout Rail** | Undocks anything that moves onto it, launching it at 5× rail speed |

## Docking a Ship

1. Place a **Rail Docker** on your ship.
2. Each Rail Docker shows up as a **Rail Docker** entry in your Weapons panel. Put it on your hotbar.
3. Fly within **100 m** of a rail on the host, aim at the rail and **fire** with that slot selected.

You don't have to line anything up: the docker's arrow face snaps onto the rail's arrow face like a magnet, and your ship ends up one block out from the rail.

- Only ships can dock (not stations), and the host must be neutral, your faction, public, or a faction you are in.
- After a dock attempt or undocking there is a 5 second cooldown.
- **Create Docking** in the advanced build mode panel builds a new docked entity right on a rail. See [Advanced Building](00-advanced-building.md#docking).

## Undocking

Once docked, the Rail Docker entry on your hotbar is replaced by **Undock**. Fire with it selected to undock.

You can also undock from the host:

- The **Docks** section of the structure panel has **Undock All**, **Turrets** and **Normal** buttons.
- Sending a logic signal to a docked ship's Rail Docker undocks it.
- A **Shootout Rail** at the end of a track launches ships off it.

## Mass Limits

There is no hard size or mass limit for docking. Instead, each structure can move **50 mass** of docked entities at full speed, plus **50 for every Rail Mass Enhancer** on it. Enhancers can go anywhere on the host; they don't need linking, but each uses some reactor power.

For every unit of mass over that limit, rails, rotators and AI turret turning slow down by 5%, to a minimum of 5% speed.

## Turrets

A turret is built from docked entities on **Rail Turret Axis** blocks. One axis only rotates around one axis, so a full turret uses two:

```scene
{ "height": 300,
  "blocks": [ { "from": [-3,0,-3], "to": [3,0,3], "block": "GREY_HULL" } ],
  "steps": [
    { "text": "Place a Rail Turret Axis on the host ship, arrow face up.",
      "blocks": [ { "at": [0,1,0], "block": "RAIL_TURRET_AXIS", "orient": 12 } ] },
    { "text": "Dock the turret base to it with a Rail Docker facing down. The base turns left and right (yaw).",
      "blocks": [ { "at": [0,2,0], "block": "RAIL_DOCKER", "orient": 8 },
                  { "from": [-1,3,-1], "to": [1,4,1], "block": "DARK_GREY_HULL" } ] },
    { "text": "Put a second Rail Turret Axis on the side of the base, and dock the barrel to it with a docker facing sideways. The barrel tilts up and down (pitch).",
      "blocks": [ { "at": [2,4,0], "block": "RAIL_TURRET_AXIS", "orient": 20 },
                  { "at": [3,4,0], "block": "RAIL_DOCKER", "orient": 16 },
                  { "from": [4,4,-1], "to": [4,4,1], "block": "DARK_GREY_HULL" },
                  { "from": [4,4,-5], "to": [4,4,-2], "block": "CANNON_BARREL" } ] },
    { "text": "On the back of the barrel: a Cannon Computer linked to the barrels, a BOBBY AI Module so the turret aims by itself, and a Faction Module.",
      "blocks": [ { "at": [4,4,1], "block": "CANNON_COMPUTER" },
                  { "from": [4,4,-5], "to": [4,4,-2], "block": "CANNON_BARREL", "controller": [4,4,1] },
                  { "at": [4,4,2], "block": "BOBBY_AI_MODULE" },
                  { "at": [4,4,3], "block": "FACTION_MODULE" } ] } ] }
```

- A docker facing **up or down** on its entity turns around the vertical axis (yaw); a docker facing **sideways** tilts (pitch).
- The turret pivots on the docker, not the ship core, so the core can go anywhere on the turret.
- The barrel (the last entity in the chain) does the aiming and turns the base with it.
- Turrets can't rotate into blocks around them, so leave them room to turn.
- Heavier turrets turn slower under AI control.

### Turret AI

Put a **BOBBY AI Module** on the barrel (the entity on the last axis) and tick **Active**; it is set to the Turret type automatically. Turrets use the host's faction, so they don't need a Faction Module. From the host, `,` turns docked AI on and off and `.` resets turret rotation.

See [Ship & Turret AI](../02-ships/10-ship-ai.md) for targeting, remote control and the rest of the AI settings.

## Shared Power and Shields

- Docked entities run on the **reactor of the root ship**, so turrets don't need their own reactor.
- While the host's shields are above 25%, they also take hits aimed at its docked entities.

## Automatic Docking (Pickup Points)

For carrier hangars, place a **Pickup Point** next to a rail (usually a **Pickup Rail**):

- An unpiloted ship whose Rail Docker comes within 3 m of an active Pickup Point docks to the rail next to it. Your own ship does too while you fly it.
- The Pickup Point can be turned on and off with logic.
- A docked ship remembers the Pickup Point it used. The **Carrier Recall** fleet order sends fleet ships back to their pickup points on the flagship.

## Moving Rails

Ships docked to a **Rail Basic** move along the track by themselves, in the direction of the rail arrows, until the track ends. Use this for elevators, launch tubes and sliding doors.

- **Rail Rotator Clock Wise / Counter Clock Wise**: with nothing linked, it turns the docked entity 90° as it arrives. Link Activation Modules to it to set the angle: each active one adds 45°, and 9 or more make it turn non-stop. Link a Display Module with a number (0–360) to set an exact angle.
- **Rail Speed Controller**: link it to rails and rotators (`C`/`V`; `Shift+V` adds all touching rails), then link Activation Modules to it. Speed is the share of those modules that are on: 5 on and 5 off means 50% speed, and all off stops the track. Rails without a controller run at 50%.

## Cargo Rails

Link the ship's Rail Docker to Storage blocks on the ship, and link a **Rail Load** or **Rail Unload** to Storage on the host:

- **Rail Load** moves items from the host's storage into the docked ship's storage.
- **Rail Unload** moves items from the docked ship to the host.

Storage filters still apply.
