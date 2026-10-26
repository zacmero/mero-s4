# mero-s4 — Samsung Galaxy S4 Zoom SM-C101 hardware archaeology

**Two independent, completely unresponsive SM-C101 units. A preservation-first, board-level diagnostic investigation.**

As of **2026-10-26** both devices have failed to start after long storage, despite earlier professional attempts and externally recharged batteries. This is **not** a routine battery-lock/charge-cable/boot-key issue. We are gathering objective USB and electrical observations before opening the first unit.

> **Evidence discipline:** Owner-observed facts, other users' repair reports, and our own hypotheses are separate. No board-level failure has been demonstrated on either unit. Preserve internal photos, files, device identifiers and firmware; **no factory reset, Odin flashing, blind chip heating/reflow, or random component replacement**.

## What the owner has established

| Check | Result |
|---|---|
| Device A / B model | **Both SM-C101**, independently confirmed |
| Failure history | Both ceased waking after lengthy uncharged storage; the same failure persisted historically even after batteries were externally recharged by a technician |
| Battery seating / lock | **Correct on both; ruled out** |
| Ordinary power button | No startup, no screen, no vibration reported |
| Recovery / Download Mode | Both unsuccessful; no visible response to attempted combinations |
| Charging | A ~1-hour charging attempt produced no display/charging indication |
| Test battery | Samsung Li-ion **3.8 V, 8.85 Wh**; measured **3.84 V open circuit**, essentially unchanged after unsuccessful attempts |
| Test battery health | **NOT established**: open-circuit voltage alone does not measure capacity or loaded voltage; also does not erase the history of battery-independent failures |
| USB to Arch | **Pending**, to be attempted with an actual **data-capable micro-USB cable** after Xperia work |
| Board inspection | Not yet performed; no verified component-level fault |

**No more basic charging/lock/button checklists unless genuinely new evidence calls for one.** Owner has explicitly declined buying another battery as the current diagnostic approach.

## Primary mission

Find where the power-up sequence fails, on two SM-C101 phones, **without destroying recoverable personal data**. Start with Arch USB evidence, then compare internal construction, battery/USB/power-button paths and relevant rails *only once exact model-specific test points are found*.

## Repository map

- [Owner device history and evidence](docs/DEVICE-HISTORY.md)
- [Comparable failures: original technician reports, with evidence strength](docs/CASE-STUDIES.md)
- [Service, schematics, teardown and manufacturer references](docs/REFERENCES.md)
- [Staged Arch USB + non-destructive board diagnostics](docs/DIAGNOSTIC-PLAN.md)
- [Paired A/B field notes template](docs/SESSION-TEMPLATE.md)

## Next milestone — S4-001: USB behavior on Arch

Using the micro-USB cable *proven* to carry data in the Xperia experiments:

```bash
lsusb -nn
sudo dmesg -wH
```

Connect **unit A**, record any new USB kernel events and `lsusb -nn` devices. Repeat the identical experiment with **unit B**. Save private raw logs outside Git. A complete lack of USB enumeration is useful but **not** proof that the CPU or eMMC is dead.

Do **not** use ADB as the primary detector: a powered-off phone may expose boot-mode USB without ADB. Do not use Heimdall/Odin in write mode or select download/reset actions.

## Technical baseline (published, not measured)

2013 Samsung Galaxy S4 Zoom family: **4.3-inch 540×960 Super AMOLED**, **1.5 GHz dual-core application processor** (market-dependent), **1.5 GB RAM**, **8 GB internal flash**, up to **64 GB microSD**, **16 MP camera with 10× optical zoom**, Xenon flash, **2,330 mAh** battery, originally Android 4.2. The **SM-C101 is the 3G model**; do not mix it with SM-C105 (LTE) service boards or firmware.

- [Samsung original announcement and published specifications, June 2013](https://www.samsungmobilepress.com/articles/samsung-introduces-the-galaxy-s4-zoom-the-first-smartphone-to-offer-10x-optical-zoom-for-perfect-picture-taking)
- [SM-C101 regional hardware detail](https://www.maiscelular.com.br/fichas-tecnicas/samsung/galaxy-s4-zoom/3g-sm-c101/)
- [Official Samsung Brazil SM-C101 support, user manual](https://www.samsung.com/br/support/model/SM-C1010ZKPZTM/)

**Status:** Research indexed; physical investigation pending. Some third-party sources associate SM-C101 with Exynos 4212 / Mali-400 and eMMC 4.41; verify exact chip/board revision before relying on these for component-specific work.
