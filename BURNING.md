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
| D1 | `roms/program/136002-113.d1` | A296B855 | 6842 |
| E1 | `roms/program/136002-114.e1` | 45133E36 | 1A1B |
| F1 | `roms/program/136002-115.f1` | DD2F9BA8 | F273 |
| H1 | `roms/program/136002-316.h1` | F7B7B4F9 | 2242 |
| J1 | `roms/program/136002-217.j1` | 80A0E820 | 560A |
| K1 | `roms/program/136002-118.k1` | 35C11CA1 | 003C |
| L/M1 | `roms/program/136002-119.lm1` | 05652966 | CFFD |
| M/N1 | `roms/program/136002-120.mn1` | 82F4A18F | 49B8 |
| P1 | `roms/program/136002-121.p1` | 82495421 | E8DE |
| R1 | `roms/program/136002-222.r1` | 131F7734 | 8050 |

The 16-bit sum is the simple byte checksum most EPROM programmers display after reading a chip.

## Vector ROMs (optional)

These add the hyperspace star streaks, the fading title logo and the softer attract-mode text. Without them, Tempest² runs normally with Atari's dot star field, a logo that disappears at the end of the title, and attract text at full brightness.

| Location | File | CRC32 | 16-bit sum |
|---|---|---|---|
| N/P3 | `roms/vector/136002-123.np3` | C5A7F6B9 | 4A58 |
| R3 | `roms/vector/136002-124.r3` | 3A9DCC4B | 3D87 |

The original vector ROMs may be mask ROMs rather than EPROMs; a 2716 fits the same socket. **Only use these vector ROMs with the Tempest² program ROMs.** With any other program, the title logo and all the text are drawn at an unpredictable brightness and may be invisible.

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
