# CogOwl Kits

Free, open-source 3D-printed engineering kits that teach elementary and middle schoolers physics through hands-on builds.

Each kit is a real mechanism that kids put together themselves, test, and measure. There are no screens and no rulers or scales. Kids take measurements by counting everyday objects. The program is free now during the test-kit phase and will stay free after it.

Follow along on Instagram: [@cogowlkits](https://instagram.com/cogowlkits)

---

## CogOwl 1: Power and Torque

> Build a gearbox. Lift a heavy load with one finger. Find out what you pay for it.

Students build a reconfigurable gearbox with a hand-cranked winch. A cup of counters (pennies, LEGO bricks, math cubes) acts as the "effort" and pulls on the crank. A load cup hangs from the winch drum. Kids rebuild the gear train between four tests, and they see that gears trade speed for strength but never add extra power.

| | |
|---|---|
| Designed for | Grades 3–5 (also works for middle school) |
| Time | 2 sessions × 45 min |
| Group size | 2–3 builders per kit |
| Prep | None. Each group finds 3 loads and about 40 identical counters in the room |

### What students learn

- Meshed gears turn in opposite directions
- Gear ratio: how many turns in for one turn out
- Torque: a twisting push gets stronger the farther from the axle you apply it
- Compound gear trains: ratios multiply (3 × 3 = 9)
- Gears trade speed for strength, and friction takes a small share

### Lessons

| Page | Lesson | What happens |
|---|---|---|
| 4 | Build the frame | Back frame, 3 hex axles, front plate, 4 thumb screws. About 5 minutes, no tools |
| 5 | 1 · Gears push gears | Meshing, direction, and the **hole rule** for spacing axles |
| 6 | 2 · Count the turns | Count turns with the orange dots to discover gear ratio (3:1, 2:1) |
| 7–8 | 3 · Twist it / **Test A** | Winch only: find the load that takes 9–12 counters to lift |
| 9 | 4 · The trade / **Test B** | 3:1 gearbox: fewer counters, more crank turns |
| 10 | 5 · Stack the layers / **Test C** | Two gear layers make a 9:1 compound train |
| 11 | 6 · Nothing for free / **Test D** | Flip the gears: fast but much harder to lift |
| 12 | Challenge | Lift 20 counters with at most 4 in the effort cup, using the fewest crank turns |

Students record a guess and then a measurement for every test on a wipe-off data card.

### Expected results

The crank wheel's string radius is exactly 3× the drum's, so the winch alone gives a 3× mechanical advantage. The red bead sits 20 cm above the load cup.

| Test | Setup | Effort counters | Crank turns to bead |
|---|---|---|---|
| A | Winch only | 9–12 (load is chosen to land here) | ~3 |
| B | 3:1 | ~A ÷ 3 | ~10 |
| C | 9:1 | ~A ÷ 9 | ~29 |
| D | Flipped (1:3) | ~9–12 for a 9-counter load | ~1 |

Effort ≈ load ÷ (3 × gear ratio). Crank turns ≈ 200 mm ÷ (2π × 10.17 mm) × gear ratio ≈ 3.1 × gear ratio. Friction pushes the real effort counts slightly higher.

---

## Engineering notes

Everything is modeled parametrically in Onshape from one Variable Studio, so a single tolerance change updates every part.

| Variable | Value | Use |
|---|---|---|
| `#m` | 2 mm | gear module |
| `#pa` | 25° | pressure angle |
| `#grid` | 12 mm | hole pitch |
| `#hole` | 7.2 mm | frame holes |
| `#hexAxle` | 6.0 mm AF | axle across flats |
| `#hexBore` | 6.3 mm AF | gear and spacer bores |
| `#plateT` | 4 mm | plate thickness |
| `#gap` | 18.5 mm | between plates |

Key design decisions:

- **The hole rule.** With module 2, a gear pair's center distance is m(z₁ + z₂)/2 = (z₁ + z₂) mm. On a 12 mm grid that comes out to (z₁ + z₂) ÷ 12 holes: 12T+24T = 3 holes, 12T+36T = 4, 24T+36T = 5. Kids can space any pair correctly without measuring.
- **Hex axles end to end.** A 6.0 mm AF hex has 6.93 mm corners, which can't pass a Ø6.4 round hole. The frame holes are Ø7.2, so the hex turns freely in them while gears and spacers key onto it.
- **Plate width 180 mm (15 columns).** With 14 columns, a 36T gear on axle C hit the corner post by 0.7 mm. Adding a column centers axle B and leaves 6.9 mm of clearance at A and C.
- **Drum barrel Ø19.3, not Ø20.** With 1 mm string, the string centerline sits at r = 10.17 mm. The crank groove puts its string at r = 30.5 mm, so the ratio is exactly 3.00.
- **Axial stack-up.** Every configuration fills the 18.5 mm gap with 18 mm of gears (6 mm) and spacers (2 mm, 10 mm), leaving 0.5 mm of float.
- **Tolerance coupon first.** One print tests hex bores (6.2/6.3/6.4), frame holes (7.0/7.2/7.4), heat-set insert holes, and gear mesh at 48.0 vs 48.3 mm center distance. Update the variables from the results before printing anything else.
- **Backlash** is tuned in the slicer (X-Y contour compensation ≈ −0.1 mm on gears only), not by editing the tooth profile.

Full dimensions, Onshape modeling steps, and print settings for every part: [`docs/cogowl-1/part-specs.md`](docs/cogowl-1/part-specs.md)

---

## Make a kit

### Printed parts (PLA)

| Part | Qty |
|---|---|
| CO1-01 Back frame (plate + 4 posts) | 1 |
| CO1-02 Front plate | 1 |
| CO1-03 Gears: 12T, 24T, 36T | 2 each |
| CO1-04 Hex axle | 3 |
| CO1-05 Spacers: 2 mm / 10 mm | 6 / 3 |
| CO1-06 Crank wheel with handle peg | 1 |
| CO1-07 Winch drum | 1 |
| CO1-08 Cups | 2 |
| CO1-10 Tolerance coupon | print first, not shipped |

General settings: 0.2 mm layers, 3–4 walls, 20% infill, no supports. Gears at 0.12–0.16 mm layers with 4 walls. Print both cups together so they weigh the same.

### Hardware

| Item | Per kit |
|---|---|
| M3 heat-set inserts | 4 |
| M3 × 8 knurled thumb screws | 4 |
| Braided string, ~1 mm | 1.5 m |
| Red pony bead | 1 |
| Wipe-off data card + marker | 1 |

### Assembly before shipping

1. Press the 4 heat-set inserts into the back-frame posts.
2. Tie the load cup to the drum and the effort cup to the crank wheel.
3. Thread the red bead onto the load string 20 cm above the load cup.
4. Mark one tooth on each gear with an orange dot (printed with the AMS, or with a marker).

---

## Repository layout

```
docs/
  cogowl-1/
    builders-guide.md   Student and teacher guide text: lessons, tests, answer key
    part-specs.md       Dimensioned specs, Onshape steps, print settings
LICENSE                 CC BY-SA 4.0
```

## Roadmap

- **CogOwl 1:** in test-kit phase with local families. Feedback goes straight into the next revision.
- **CogOwl 2 (in design):** a bridge-building kit and a slightly harder follow-up to CogOwl 1. It's planned around an infill-geometry beam-bending experiment, so kids can see how internal structure changes stiffness.

## License

Designs and documentation are licensed under [CC BY-SA 4.0](LICENSE). You can print, use, and adapt the kits, including in classrooms, as long as you credit CogOwl Kits and share your changes under the same license.

## Author

Designed and built by Peter Cohan.
