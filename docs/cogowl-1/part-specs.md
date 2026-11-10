# CogOwl 1 Part Specs (Rev A)

Every printed part for the Power and Torque kit, dimensioned in millimeters, with the Onshape steps to model it. Print the tolerance coupon (CO1-10) before modeling the rest, then update the variables with what it tells you.

All dimensions in mm. "AF" = across flats.

## Variables (Onshape Variable Studio)

| Variable | Value | Use |
|---|---|---|
| `#m` | 2 mm | gear module |
| `#pa` | 25° | pressure angle |
| `#grid` | 12 mm | hole pitch |
| `#hole` | 7.2 mm | frame holes |
| `#hexAxle` | 6.0 mm | axle across flats |
| `#hexBore` | 6.3 mm | bore across flats |
| `#plateT` | 4 mm | plate thickness |
| `#gap` | 18.5 mm | between plates |

## Conventions

- Hex bores are 0.3 larger than the axle. Frame holes clear the hex corners by 0.27.
- Gears in the same layer mesh. Axles are 48 apart for 12T + 36T and 36 apart for 12T + 24T.
- One Part Studio per part keeps the kit easy to revise. Drive all of them from the Variable Studio.
- Stack-up: every configuration fills the 18.5 gap with 18 of gears and spacers, leaving 0.5 of float.

## Changes from the earlier spec

- **Axles are hex end to end.** A hex can't pass through a Ø6.4 round hole (its corners are 6.93 across), so round journals couldn't be assembled. Frame holes are now Ø7.2 and the hex turns in them.
- **Plate is 180 wide, not 168.** With 14 columns, a 36T gear on C hit the corner post by 0.7 mm and overhung the plate. 15 columns puts B dead center and gives A and C 6.9 mm of clearance.
- **Drum barrel Ø19.3.** Corrects for string thickness so the crank-to-drum ratio is exactly 3.
- **Loads.** The cups were first sized around 3/8" USS steel washers. Kits now use found objects as loads and counters as effort, so no washers ship.

---

## CO1-01 Back frame

qty 1 · PLA · plate and posts are one part

| Feature | Size |
|---|---|
| Plate | 180 × 84 × 4, R4 corners |
| Hole grid | 15 × 7 on 12 pitch, first hole 6 from edges |
| Grid holes | Ø7.2 through, 101 (corners replaced by posts) |
| Posts | Ø12 × 18.5 tall at the 4 corner grid points |
| Post root | R2 fillet |
| Insert holes | Ø4.0 × 5 deep, top of each post |
| A / B / C | row 4 (y = 42), x = 42 / 90 / 138 |
| Letters | 3.5 tall, 0.6 engraved, inner face, centered y = 36 |

**Model it:**
1. Variable Studio: `#grid` = 12, `#hole` = 7.2, `#plateT` = 4, `#gap` = 18.5.
2. Sketch a 180 × 84 rectangle on the Top plane, R4 corners. Extrude 4.
3. Sketch one Ø7.2 circle at (6, 6). Extrude Remove through all.
4. Linear pattern the cut: 15 along X at 12, 7 along Y at 12.
5. On the plate's inner face, sketch 4 Ø12 circles at the corner holes. Extrude Add 18.5; they fill the corner holes.
6. Fillet the 4 post roots R2. Sketch Ø4.0 on each post top, Extrude Remove 5.
7. Text sketch A, B, C; Extrude Remove 0.6.

**Print:** flat on its back face, posts up. 0.2 mm layers, 3 walls, 20% infill. No supports.

Insert hole size comes from the insert maker's spec sheet. Ø4.0 × 5 fits the common M3 short insert (≈4 mm long); the coupon confirms it.

## CO1-02 Front plate

qty 1 · PLA

| Feature | Size |
|---|---|
| Plate | 180 × 84 × 4, R4 corners |
| Grid holes | Ø7.2 through, 101 |
| Corner holes | Ø3.4 through (M3 clearance) |
| Letters | outer face, same positions as back frame |

**Model it:**
1. Copy the back frame's first three features (derive or duplicate the Part Studio), without the posts.
2. Cut the 4 corner points to Ø3.4 instead of Ø7.2.
3. Engrave A, B, C on the outer face. Check they read correctly when the plate faces out.

**Print:** flat, letters facing up. Same settings as the back frame.

## CO1-03 Gears

12T, 24T, 36T · qty 2 each · PLA

| Feature | Size |
|---|---|
| Module / pressure angle | m = 2 · 25° |
| Tip Ø | 28 · 52 · 76 |
| Pitch Ø | 24 · 48 · 72 |
| Root Ø | 19 · 43 · 67 |
| Thickness | 6 |
| Bore | hex 6.3 AF, 0.4 chamfer both sides |
| Orange dot | Ø2.5 × 0.6 on one tooth, r = 11 · 23 · 35 |

**Model it:**
1. Custom features → search "Spur gear" and add a public gear FeatureScript that takes module and pressure angle.
2. Module 2, pressure angle 25°, teeth 12 / 24 / 36, thickness 6, no bore.
3. Sketch a hexagon on the gear face, 6.3 flat-to-flat, Extrude Remove through.
4. Model the dot as a separate part (Extrude New, 0.6) so the AMS can print it orange.

**Print:** flat. 0.12–0.16 mm layers for cleaner teeth. 4 walls so the teeth are solid.

**Backlash:** don't edit the tooth profile. In Bambu Studio set X-Y contour compensation to about −0.1 mm on the gears only, then adjust after the mesh test.

## CO1-04 Axle

qty 3 · PLA or PETG

| Feature | Size |
|---|---|
| Hex | 6.0 AF × 47.5 |
| Head | Ø12 × 2, flats at ±3.0 |
| Free end | 0.5 × 45° chamfer |
| Why full hex | passes through the Ø7.2 frame holes; corners (6.93) turn in them |

**Model it:**
1. Sketch on the Front plane: hexagon 6.0 flat-to-flat, one flat on the X axis.
2. Extrude 47.5. Sketch a Ø12 circle on the end face, trim with two lines at ±3.0, Extrude 2 in the opposite direction.
3. Chamfer the free end 0.5.

**Print:** lying on a hex flat, so layer lines run along the axle. 0.2 mm layers, 4 walls. The head flats match the hex flats so it prints flat.

The head stops the axle sliding forward. If axles drift backward in testing, add the optional TPU collar (see spacers).

## CO1-05 Spacers

2 mm × 6 · 10 mm × 3 · PLA

| Feature | Size |
|---|---|
| OD | Ø10 |
| Bore | hex 6.3 AF |
| Lengths | 2 and 10 |
| Stack rule | layer 1 only: 2 + gear + 10 · layer 2 only: 10 + gear + 2 · both: 2 + gear + 2 + gear + 2 |

**Model it:** sketch a Ø10 circle and a 6.3 AF hexagon. Extrude 2. Duplicate and extrude 10.

**Print:** standing up. Print extras; they're tiny and they will get lost.

**Optional TPU collar:** same part, 4 long, bore 5.8 AF, printed in TPU. It grips the axle and stops it sliding out the back.

## CO1-06 Crank wheel

qty 1 · PLA or PETG

| Feature | Size |
|---|---|
| OD / width | Ø64 × 8 |
| Groove | 3 wide × 2 deep, root Ø60 (string center r ≈ 30.5) |
| Bore | hex 6.3 AF |
| Handle peg | Ø10 × 20 at r = 24, R2 root fillet |
| Tie hole | Ø2 through at r = 28, opposite the peg, slotted 1.5 wide out to the groove |

**Model it:**
1. Revolve the section profile (flange 2.5 · groove 3 · flange 2.5) around the axle axis.
2. Cut the hex bore. Extrude the peg 20 from the outer face at r = 24; fillet R2.
3. Cut the tie hole and a 1.5 slot from it to the groove root.

**Print:** flat, peg pointing up. Use PETG if PLA pegs snap under classroom use.

The groove radius (30.5 with 1 mm string) is exactly 3× the drum's string radius. That ratio is what makes the winch a 3× machine in Test A.

## CO1-07 Winch drum

qty 1 · PLA

| Feature | Size |
|---|---|
| Flanges | Ø30 × 2, both sides |
| Barrel | Ø19.3 × 8 (string center r ≈ 10.2) |
| Bore | hex 6.3 AF |
| Tie hole | Ø2 at r = 7, slotted out to the barrel |

**Model it:** revolve the profile. Cut the hex bore. Cut the tie hole and slot.

**Print:** flat on a flange. No supports.

Ø19.3, not Ø20: with 1 mm string, the string center sits at 10.17 and 30.5 ÷ 10.17 = 3.00.

## CO1-08 Cups

qty 2 · PLA

| Feature | Size |
|---|---|
| Inside | Ø30, 66 deep |
| Wall / floor | 1.2 / 1.2 |
| Outside | Ø32.4 × 67.2 |
| Ears | 2 tabs 8 × 6 above rim, Ø3 hole |
| Mass | ≈ 11 g each |

**Model it:**
1. Sketch a Ø32.4 circle, Extrude 67.2. Shell 1.2, removing the top face.
2. Sketch two 8 × 6 tabs on the rim's outer wall line, Extrude 1.2 thick. Cut Ø3 holes.

**Print:** upright, 3 walls, 0.2 mm layers. Both cups must weigh the same, so print them together.

## CO1-09 Base (optional, not in the current kit)

qty 1 · PLA

| Feature | Size |
|---|---|
| Plate | 220 × 100 × 4, R4 |
| Rail | slot 4.4 wide between two walls 3 thick × 10 tall |
| Back wall | x 20–200 |
| Front wall | x 34–186 (stops short of the bottom posts) |
| Placement | front edge flush with the desk edge |

**Model it:** sketch the plate, Extrude 4. Sketch the two wall rectangles, Extrude 10 up.

**Print:** flat. 3 walls, 15% infill.

The cups need about 25 cm of drop, so the gearbox sits at a desk edge, and a loaded cup can tip it. The base holds it upright. The shipped kit leaves it out (it's longer than the shipping box) and has one builder hold the gearbox steady instead. A $1 spring clamp also works.

## CO1-10 Tolerance coupon

print first · PLA

| Feature | Size |
|---|---|
| Gear bore hex | 6.2 · 6.3 · 6.4 AF |
| Frame holes | Ø7.0 · 7.2 · 7.4 |
| Insert bosses | Ø12 × 10 tall, holes Ø3.9 · 4.0 · 4.1 × 5 |
| Mesh test | separately: one 12T + one 36T on two 16-wide bars with Ø7.2 holes 48.0 and 48.3 apart |

**Model it:** bar 120 × 30 × 4. Cut the six test holes, add the three bosses, cut the insert holes.

**Print:** same settings as the real parts, same filament.

**Pass criteria:** the axle slides through the hex by hand with no wobble; it turns freely in the round hole with the least play; the insert goes in straight and flush; the gears mesh at 48.0 without binding. Update the variables, then model everything else.

---

## Buy, don't print

| Item | Per kit | For |
|---|---|---|
| M3 heat-set inserts | 4 | back-frame posts |
| M3 × 8 knurled thumb screws | 4 | front plate, no tools |
| Braided string, ~1 mm | 1.5 m | two strings |
| Pony bead, red | 1 | 20 cm above the load cup |
| 2" spring clamp (optional) | 1 | holds the gearbox at the desk edge |
