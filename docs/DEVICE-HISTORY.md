# Two-device incident report — S4 Zoom SM-C101

**Observed by owner, updated 2026-10-26.** No unique serial numbers, IMEIs, or owner photographs containing identifiers are stored in this public repository.

## Device A and device B

- **Both models independently verified as Samsung Galaxy S4 Zoom SM-C101.**
- Both worked historically but stopped waking after long intervals without charging.
- Owner states that even when the problem first emerged and the batteries were newer, **both batteries were sent for external full recharging**, and the phones remained unresponsive. A technician also attempted repair but failed to get either phone booting. Exact technical procedures and measurements from that technician are not available.
- **Power switch, battery lock/seating, charge attempts, Recovery Mode and Download Mode combinations** have already been explored by the owner without any startup signs. The battery locks are confirmed correct. Avoid suggesting repetition.
- Recent trial: test battery **Samsung 3.8 V lithium-ion, 8.85 Wh** (nominal ~2,330 mAh, consistent with Samsung spec). Multimeter reads **3.84 V at rest**, prior to and following failed attempts. This does **not** determine its dynamic capacity, current capacity or voltage sag.
- Battery tested in **each** phone: neither showed power-on, display activity, recovery/download mode, or apparent reaction.
- Approximately one hour with a USB charger did not produce a visible charging icon.
- No demonstrated computer USB enumeration test **yet**: will be carried out on Arch with a verified USB **data** cable once Xperia experiments conclude.
- The owner **does not want to buy another battery** as a first step; the scope is electronics investigation and meaningful diagnostics.

## What is proven and what isn't

**Proven**
- Exact shared handset variant: **SM-C101**.
- No software-based boot/key recovery screen can currently be invoked on either unit.
- Past problems persisted after external battery charging attempts.
- A resting 3.84 V battery was measured with a working multimeter.

**Not proven**
- Whether that battery can deliver stable voltage under a startup current.
- Whether the USB data path enumerates in bootloader/ROM mode or no mode.
- Whether either handset has a PMIC, charging-controller, USB, button-flex, main-CPU, camera-board or eMMC failure.
- That both handsets share an identical physical defect.
- Whether either phone contains photos or other recoverable files; avoid wiping storage without assessing.

## Investigative decision log

- **2026-10-26:** owner confirmed SM-C101 on both devices, excludes battery-lock error and simple startup modes, requests advanced repair references and eventual board access.
- **Next:** Linux USB event capture, separate A and B measurements, model-correct board documentation, then staged disassembly and paired passive inspection.
- **Do not:** recommend basic charge/lock procedures again, casually treat an eMMC guess as a diagnosis, or buy/replace parts before measuring.

## Note on battery testing

A 3.84 V open-circuit voltage is evidence of cell voltage at almost zero current, not proof that it has capacity to operate a smartphone. At the same time, the batteries' prior external recharge and the failure history support investigating device electronics rather than declaring this *only* a dead battery. Both observations coexist.
