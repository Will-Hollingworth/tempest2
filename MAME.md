# Playing Tempest² in MAME

Tempest² runs as MAME's `tempest3` machine (Tempest, Revision 3), with its ROMs replaced.

## Setup
1. Make a new folder for it, separate from your normal ROMs folder, for example `C:\mame\roms-tempest2`.
2. Copy `mame/tempest3.zip` from this repository into that folder. Don't put it in your normal ROMs folder, or it will replace your stock Tempest Rev 3 set.
3. Start MAME with that folder as its only ROM path:

   ```
   mame tempest3 -rompath "C:\mame\roms-tempest2"
   ```

   Using only that folder matters: if MAME also sees your normal ROMs folder, it may load the stock `tempest3.zip` instead.

## The checksum warning
MAME knows the checksums of Atari's original chips, so it warns that some ROMs have the wrong checksums. That's expected, since the program ROMs are new. Carry on past the warning and the game runs normally.

## Settings
All of these are in MAME's DIP switch menu (press Tab, then "DIP Switches"):
- **"Language"** chooses the well designs: English = classic, French = alternate classic/Tubes, German = Tubes only, Spanish = alternate Tubes/classic.
- **"Minimum credits"** (formerly "2 credit minimum") turns invincibility for the demo player on and off.
- **"Rating"** turns the burn-in dimming on and off: "1, 3, 5, 7, 9" (MAME's default) = dimmed attract text and title sequence; "Tied to high score" = full brightness, as stock.

A change takes effect at the next game or attract demo; press F3 to reset if you want to see it straight away.

**High scores** are saved in MAME's `nvram` folder, as with the original game.

## Optional: sharper vectors
These MAME options give clean, thin lines closer to a real vector monitor:

```
mame tempest3 -rompath "C:\mame\roms-tempest2" -beam_width_min 1.0 -beam_width_max 1.0 -beam_intensity_weight 0 -flicker 0
```

## Without the vector ROM changes
To try Tempest² without the star streaks and the dimmed, fading title sequence, replace `136002-123.np3` and `136002-124.r3` in the zip with Atari's original vector ROMs from your stock `tempest3` set.
