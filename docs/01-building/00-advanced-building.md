# Advanced Building

Build mode has a radial menu of shape tools for placing blocks in geometric patterns, and an **advanced build mode** panel full of power tools. Together they dramatically speed up construction of large ships and stations.

## Advanced Build Mode

You must be in **Build Mode** (inside a ship core or build block). Hold `Left Ctrl` to enter advanced build mode; the tool panel appears on the right side of the screen. **Tap `Left Ctrl` twice** to make it stick, and tap it again to leave.

In advanced build mode:

- You aim with the **mouse cursor** instead of the centre of the screen.
- The mouse wheel **rotates** the selected block.
- The **build size** sliders apply, so one click can place or remove a whole area of blocks.
- The middle mouse button puts the block you are pointing at on your hotbar.

> **Speed tip:** Hold `Left Shift` in build mode to move much faster — essential for working on large structures.

## Build Tools Radial Menu

Press the **backtick key** (`` ` ``) in Build Mode to open the radial menu of eight shape tools. Pick one from the ring, then click in the world to use it.

How clicks work for every shape tool:

- Normally each click lands on a point **5 blocks in front of your camera**, so you can build out into empty space. Hold `Left Ctrl` to click exactly on the block face under your cursor instead.
- **Left-click** starts a shape that places blocks; **right-click** starts one that removes them. The first click decides which. Removing needs you to click on actual blocks.
- A live preview shows the shape: yellow to place, red to remove.
- Press `Escape` to cancel a shape you have started.
- A finished shape is one undo step (`Ctrl+Z`).
- Shapes use your symmetry planes, remove filter and build size, and you need enough blocks in your inventory.

The **centre button** of the radial menu toggles **Hollow Mode**: Box, Circle, Cylinder, Ellipsoid and Polygon are then built as empty shells or outlines instead of solid fills.

### Single

The default mode. Place or remove one block (or one build-size area) per click.

### Line

Draw a straight line of blocks.

1. Click to set the **start point**.
2. Click again to set the **end point**. The line is placed.

- **`Left Ctrl` + mouse wheel** cycles axis restriction: Auto, XY plane, XZ plane, YZ plane.
- **Hold `Left Shift`** to snap to straight lines and 45° diagonals.

### Box

Fill a rectangular volume with blocks.

1. Click to set the **first corner**.
2. Click to set the **opposite corner**. The box is placed.

Hollow mode builds only the six walls.

### Curve

Draw a smooth curve.

1. Click to set the **start point**.
2. Click to set the **end point**.
3. Click to set the **control point**. The curve bends toward it (it doesn't pass through it).

- **`Left Ctrl` + mouse wheel** cycles axis restriction.
- **Hold `Left Shift`** to snap angles.

### Circle

Place a flat circle of blocks.

1. Click to set the **center**.
2. Click to set the **radius**.

- **`Left Ctrl` + mouse wheel** cycles the plane: Auto (facing you), XY, XZ, YZ.
- **Hold `Left Shift`** to snap the radius to 90° steps.
- Hollow mode builds a ring instead of a disc.

### Cylinder

Build a cylinder.

1. Click to set the **base center**.
2. Click to set the **radius**.
3. Click to set the **height**.

- While setting the radius, **`Left Ctrl` + mouse wheel** cycles the plane and **`Left Shift`** snaps it.
- Hollow mode builds an open tube with no ends.

### Ellipsoid

Build a sphere or egg shape that fits inside a box.

1. Click to set the **first corner** of the box.
2. Click to set the **opposite corner**. The ellipsoid is placed.

Hollow mode builds a shell one block thick.

### Polygon

Build a flat shape with 3 to 8 corners.

1. Before you start, **`Left Ctrl` + mouse wheel** sets how many corners it has (3 by default).
2. Click to place each corner. The shape is placed as soon as you place the last one.

Hollow mode builds only the outline.

> The axis, plane and corner settings reset to their defaults after each shape.

## Tool Panel

### General

- **Orientation:** shows which way the selected block will face. Click it to pick a shape; the mouse wheel rotates the block.
- **Undo / Redo:** also `Ctrl+Z` / `Ctrl+Y`.

### Build Size

Three sliders (X, Y, Z) grow the area you place or remove with a single click. Scroll on a number to change it; right-click to reset it. The server sets the maximum (`PLAYER_MAX_BUILD_AREA` in `server.cfg`, 100 by default).

### Symmetry

Click **XY**, **XZ** or **YZ**, then click a block to put a symmetry plane there. Placing or removing a block on one side does the same on the other side. Use all three planes to build in eight places at once. **Unset** removes a plane.

- **ODD** puts the plane through the middle of a block instead of between blocks — use it for ships with an odd width.
- **Mirror cubic blocks** / **Mirror non-cubic blocks** (both on by default) turn blocks on the other side so they mirror the ones you place, for example wedges and weapon outputs facing outward on both sides.

### Selection

- **Copy Brush:** click **\*PICK AREA\***, then click the two corners of the area to copy.
- **Cut Mode:** with this on, copying an area also removes those blocks and puts them in your inventory, like a cut. Undo puts them back.
- **Paste:** shows the copy as a preview; click to place it. You need the blocks in your inventory. While pasting:
  - Mouse wheel rotates the copy (hold `Left Shift` for the X axis, `Left Ctrl` for the Z axis).
  - `Left Alt` + arrow keys / `Page Up` / `Page Down` nudge it one block (add `Left Shift` for 10).
- Links between blocks (C/V) are kept when both ends are inside the copied area.
- **Templates:** save a copy under a name with tags, and load it later in any build. Search by name or tag.
- **Remove/Replace:** pick a block type (from the list or **Pick with camera**). Right-click then only removes that type of block. Tick **Only replace** to swap those blocks for your selected block instead. This is invaluable for **refitting ships**.
- **Highlight Selected in Entity:** shows every block of the chosen type in the structure.

### Hotbar

Save your hotbar as a named **layout** and load it again later.

### Color Finder

Find a block by color: enter a hex color, pick a random one, or adjust saturation and brightness, then **COPY TO HOTBAR**.

### Block Mixer

Choose up to 10 blocks. With the mixer on, each block you place is picked at random from them — great for weathered or patterned hulls. **SET FROM HOTBAR** fills it from your hotbar.

### Fill Tool

Click **Place Fill Origin** and click a spot, then press **Fill** to flood the connected space (or the connected blocks of one type) with your selected block. The slider sets how many blocks each press adds.

### Build Helpers

Shows a guide shape in the world (**line**, **circle**, **ellipsoid** or **torus**) to build along. Tick **Restrict Building to Helper** to only place blocks inside it.

### Docking

**Create Docking** builds a new docked entity in two clicks: pick the rail, then pick where its core goes and which way it faces. See [Docking & Turrets](02-docking-and-turrets.md).

### Display

Toggles that help while building:

- **Buildlight:** a flashlight for building in dark areas (also `P`).
- **Lighten up blocks:** removes shadows so dark interiors are fully lit. Turn it off now and then to see how your ship really looks.
- Structure info, extra block info, reactor convex hull, and center of mass indicators.
