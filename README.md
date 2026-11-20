
# Dreame L40s Pro Ultra / X40 Ultra – Dying mid-clean, then shutting off right off the dock (100% → 60% drop)

Technical root cause and DIY fix for the common battery shutdown issue on **Dreame L40s Pro Ultra** and **Dreame X40 Ultra** robot vacuums (battery pack model: `R2412-4S2P-MMBK`). An acquaintance's X40 Ultra developed the exact same problem around the same age.

## How the issue progressed (Symptoms)
* **Stage 1:** At first, the robot started stopping cleaning cycles halfway through, acting as if the battery had suddenly drained completely.
* **Stage 2:** Soon after, it got worse—the robot showed 100% battery on the dock, started a cleaning cycle, and the exact moment it rolled off the dock (or was lifted off by hand), it immediately shut down completely (screen/LEDs off, unresponsive to buttons).
* When placed back on the dock, the battery percentage suddenly dropped from 100% down to around 60–65%, then suspiciously "charged" back up to 100% within minutes, repeating the exact same loop.
* A full factory reset did not solve it.

## The Real Root Cause (It’s usually not dead cells)
At first glance, it looks like a failed battery cell, but after opening the pack, all cell voltages were completely healthy (~16V total). The real culprit is water/moisture getting past the unsealed edges of the bottom plate during mopping or dock washboard cleaning, pooling near the battery compartment, and wicking along the wiring harness under the factory heat-shrink wrap right onto the edge of the BMS board.

![Battery pack R2412-4S2P-MMBK](1.jpg)

Combined with the 16V DC voltage, electrolysis kicks in:
1. Copper oxidation eats away the solder mask and corrodes the main power pads (`P+1`, `P+2`, `P-`), causing an instant voltage sag under load that triggers the BMS protection cutoff.
2. The thin PCB trace for the middle white communication/sense wire (`TP13`) gets completely corroded/burned through.

![Corroded BMS board and TP13 trace](2.jpg)

## Solutions – Two Options

### 1. If your robot is still under warranty
* **Do not open it!** There is a factory `Warranty Seal` sticker inside one of the screw recesses next to the side brush—puncturing it immediately voids your warranty.
* Record a continuous, unedited 20-second video clearly showing the 100% charge on the dock, the instant shutoff when lifted off, and the ~64% reading upon placing it back on the dock, then submit it for warranty service.

### 2. If out of warranty (or you can't afford weeks of downtime)
* **Replacement battery:** Search for part number `R2412-4S2P-MMBK` to get a reliable aftermarket replacement (e.g., **Cameron Sino `CS-DRL400VX`** 5200 mAh or **`CS-DRL400VH`** 6800 mAh). Once the bottom plate is unscrewed, swapping it takes 5 minutes.
* **BMS repair (for advanced DIYers):** If the cell groups are balanced, the original pack can be saved by cleaning the BMS with isopropyl alcohol (IPA), resoldering the main power leads onto wider exposed copper planes, bridging the broken `TP13` trace, and sealing both sides of the PCB with conformal coating.

## Prevention
I sealed the cable entry point (where the 5 wires enter the heat-shrink sleeve) with **T-7000** acid-free electronics adhesive so moisture can't wick in again. Just avoid regular vinegar-smelling (acetoxy) silicone, as its fumes will corrode the copper traces just like water.

![Repaired BMS and T-7000 sealed cable entry](3.jpg)
