# Burning EPROMs for a real Tempest

Tempest² is for the **12-ROM Tempest board**, where every program and vector ROM is a 2 KB part (2716 or 2516). It will not work as-is on boards fitted with 2732 EPROMs (the 6-ROM versions).

## What you need
- **Ten 2716 EPROMs** (2 KB × 8, 24 pin) for the program ROMs. Use single-supply +5 V parts (Intel-style 2716, or 2516). The old Texas Instruments TMS2716 is a three-supply chip with a different pinout and will not work.
- **Two more 2716s** if you want the optional vector ROMs.
- An EPROM programmer, and an eraser if you are reusing chips.
- Anti-static precautions (wrist strap or at least a grounded work surface).

## Program ROMs (required)

All ten are replaced. They sit in a row, D1 to R1, on the game PCB, and the files are named after their board locations.

| Location | File | CRC32 | 16-bit sum |
|---|---|---|---|
| D1 | `roms/program/136002-113.d1` | 61E7CD5F | 6B2B |
| E1 | `roms/program/136002-114.e1` | 1DD8ED5A | 18FE |
| F1 | `roms/program/136002-115.f1` | D427FAC4 | F379 |
| H1 | `roms/program/136002-316.h1` | C3E3A422 | 21B1 |
| J1 | `roms/program/136002-217.j1` | 33F09F6A | 552D |
| K1 | `roms/program/136002-118.k1` | 3534223C | 0029 |
| L/M1 | `roms/program/136002-119.lm1` | ED1E1CB7 | D316 |
| M/N1 | `roms/program/136002-120.mn1` | EF06689A | 49A0 |
| P1 | `roms/program/136002-121.p1` | 855BE2ED | E64B |
| R1 | `roms/program/136002-222.r1` | 3D0ACE3A | 8282 |

The 16-bit sum is the simple byte checksum most EPROM programmers display after reading a chip.

## Vector ROMs (optional)

These add the hyperspace star streaks and the fading title logo. Without them, Tempest² runs normally with Atari's dot star field and a logo that disappears at the end of the title.

| Location | File | CRC32 | 16-bit sum |
|---|---|---|---|
| N/P3 | `roms/vector/136002-123.np3` | 60CBBE53 | A796 |
| R3 | `roms/vector/136002-124.r3` | 6F80234A | 3D87 |

The original vector ROMs may be mask ROMs rather than EPROMs; a 2716 fits the same socket. **Only use these vector ROMs with the Tempest² program ROMs.** With any other program, the title logo is drawn at an unpredictable brightness and may be invisible.

The self-test ROM check passes with either these or Atari's original vector ROMs.

## Fitting
1. **Power off and unplug** the machine. Remember the monitor holds dangerous voltages even when unplugged; you don't need to go near it to reach the game PCB.
2. **Photograph the board** before removing anything, so you can see each chip's position and orientation.
3. **Burn and verify** each EPROM, and check its sum or CRC against the tables above. Label each chip with its location.
4. **Remove the old chips** carefully and keep them. You can go back at any time by refitting them.
5. **Fit the new chips** with the notch facing the same way as the originals. Check that no pins are folded under.
6. **Power on and run the self-test** (test switch). The ROM check should pass.
7. **Set the DIP switches** at L12 for the well designs and attract mode you want (see the README).

## After upgrading
- The high-score table now also stores the level each player reached. If the table looks odd the first time, clear it.
- If anything goes wrong, refit the original chips and you are back to stock.
