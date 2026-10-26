# Non-destructive troubleshooting — SM-C101 × 2

**Scope:** two independently dead S4 Zoom SM-C101 units. Preserve data; move to measured board fault localization. Don't repeat the already eliminated battery lock, button combinations or long charging attempts.

## S4-001: finish external evidence — USB enumeration on Arch (NEXT)

**Prerequisite:** known-good, data-capable micro-USB cable verified with another device; Linux host. Use a normal safe 5 V USB port and leave the old battery disconnected between test sessions as appropriate. Don't leave aging Li-ion batteries charging unattended.

1. Record baseline with neither phone connected:
   ```bash
   lsusb -nn
   sudo dmesg -wH
   ```
   Keep the `dmesg` terminal open. Another helpful independent monitor is `udevadm monitor --kernel --subsystem-match=usb`.
2. Connect **phone A** once, watch 30–60 seconds and record whether kernel connection/USB descriptor events occur. Take a fresh `lsusb -nn`. If safe, briefly press power once and observe again. **No recovery-button circus; those tests were completed.**
3. Unplug A; separately repeat **exactly** with **phone B** using the same host port, cable, and battery/charging state.
4. Save a short *redacted* summary to [session template](SESSION-TEMPLATE.md). Raw `dmesg` and `lsusb` logs may include device-identifying numbers; keep them locally outside Git.
5. If a device enumerates: note vendor/product IDs, class and driver only. **Do not** blindly run Odin, Heimdall flash, partition/repartition, firmware download, rooting or filesystem writes. `adb devices` can be a supplementary identification check, not the enumeration test itself.
6. If no device enumerates: record the negative test under exact circumstances. Possible remaining causes include USB connector/port path, inability to start the USB controller, PMIC sequencing, processor/boot-stage failures, and more. **No enumeration does not prove dead CPU or eMMC.**

**Evidence gate:** paired, reproducible results for A and B plus exact connection conditions.

## S4-002: staged visual inspection after USB test

Tools: Phillips **PH000**, quality plastic spudger/picks, tweezers, organized screw tray; optional magnification and ESD-conscious workspace.

- Unplug charger and **remove the battery, SIM, microSD**.
- Follow [VRM24 SM-C101 teardown](https://vrm24.com/pt/instru%C3%A7%C3%B5es/como-desmontar-samsung-galaxy-s4-zoom-sm-c101-por-si-mesmo/) **only far enough to expose areas needed**. The guide goes: 2 screws at end → front/antenna covers → 8 screws → flash connector and 2 more screws → midframe. Recheck orientation with photos at every stage.
- Photograph **board revision markings**, USB connector, battery connector, power switch and flex routing (edit/redact visible unique identifiers before committing).
- Inspect under magnification for damage to port pads, bent contacts, corrosion, cracking, detached flex, overheated ICs, liquid damage or previous repair marks.
- Don't detach the optical zoom assembly, desolder chips, or disturb Xenon flash circuitry as a first step. **Camera xenon-flash capacitor(s) may retain high voltage even with battery removed**; never touch exposed flash circuitry or attempt to discharge it casually.
- Compare A versus B without swapping parts initially; keep each handset's original configuration identifiable.

**Evidence gate:** documented visible board revision and high-quality photos of relevant power/USB regions, no damage from opening.

## S4-003: no-power continuity and passive board measurements

**With charger and battery DISCONNECTED:**
- Confirm known ground by continuity from appropriate board ground to USB shell/ground, **only after identifying reference points**. Do not randomly bridge nearby pins.
- Measure suspicious rails in **resistance or diode mode** against ground only after schematic or safe unambiguous test-point mapping. A low ohm reading alone can be normal on a modern processor rail. Compare matching A/B locations.
- Check the power-button contact/line continuity only with verified board mapping, with the button pressed/released.
- Look for differences in USB VBUS path / common protection fuses, flex or connectors in unpowered condition.

**With power applied, later and only once test points are confirmed:**
- Measure DC on identified **VBAT**, **USB VBUS**, PMIC inputs/enables, and startup rails as indicated by an **authentic SM-C101 schematic**.
- Do not place meter on current/A setting across battery terminals or USB power: that shorts the supply. Current needs an appropriate series setup / protected inline meter or a correctly configured current-limited bench supply.
- 3.84 V **open-circuit** on the shared battery does not establish its ability under load; interpret loaded voltages cautiously. A later stabilized lab supply may be useful in the hands of someone who can set voltage, current limit and polarity correctly; **not** a beginner improvisation with the charger.
- Never probe near Xenon-flash high-voltage circuits.

**Evidence gate:** paired A/B table with board revision, test-point identities and conditions, measured resistance and voltage.

## S4-004: boot-chain/eMMC investigation (only if indicated)

- References mention **MAX77693**, a device called **8767-60**, eMMC Boot1, and failed Download Mode. All are *candidate topics* from forums, not a diagnosis or an approved pinout.
- Confirm expected supply rails and startup behavior first. Read boot/serial/JTAG documentation only after identifying **this exact board revision** and a legal path to preserve storage content.
- Avoid soldering/removing the eMMC, shorting CMD lines, “Factory Repair,” direct flash/programming, full-board reflow, or random chip swaps. These are data-loss and board-damage risks.

## Paired test discipline

| Category | Phone A | Phone B |
|---|---|---|
| Board revision/photo | TODO | TODO |
| Battery model/label (no serial) | TODO | TODO |
| USB kernel events with known data cable | TODO | TODO |
| USB vendor/product IDs (if any) | TODO | TODO |
| Connector appearance / contamination | TODO | TODO |
| Power button/flex continuity (unpowered) | TODO | TODO |
| Ground and identified no-power measurements | TODO | TODO |
| Identified power rails (if safe) | TODO | TODO |
| Suspected failure from actual evidence | UNKNOWN | UNKNOWN |

**No conclusion based on one reading or on a different handset's anecdotal rail values.** The point of owning two is to compare repeatable conditions.
