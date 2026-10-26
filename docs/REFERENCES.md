# Source index — Galaxy S4 Zoom SM-C101

Research checked **2026-10-26**. Links are to original manufacturer pages, teardown guides or public forum discussions. **Service file listings ≠ verified access to the contained schematic.** We have not downloaded or interpreted private/restricted technical PDF attachments.

## Official / product identity

1. [Samsung Mobile Press (2013), initial S4 Zoom announcement and spec table](https://www.samsungmobilepress.com/articles/samsung-introduces-the-galaxy-s4-zoom-the-first-smartphone-to-offer-10x-optical-zoom-for-perfect-picture-taking). Family spec: 4.3-inch qHD, 1.5 GHz dual-core (processor choice differs by market), 1.5 GB RAM, 8 GB storage, 16 MP 10× OIS camera, 2,330 mAh. **Press sheet combines 3G/LTE variants, so distinguish C101 from C105.**
2. [Samsung Brazil SM-C101 official support](https://www.samsung.com/br/support/model/SM-C1010ZKPZTM/). Brazilian manufacturer's model page, Portuguese-language user manual `SM-C101_UG_BR.pdf` listed.
3. [SM-C101 regional specifications (MaisCelular)](https://www.maiscelular.com.br/fichas-tecnicas/samsung/galaxy-s4-zoom/3g-sm-c101/). Third-party, useful for 3G variant and candidate Exynos 4212, Mali-400, eMMC. Treat chipset/board detail as **provisional** until board identification.

## Physical disassembly

4. **[VRM24 — full 21-step SM-C101 teardown in Portuguese](https://vrm24.com/pt/instru%C3%A7%C3%B5es/como-desmontar-samsung-galaxy-s4-zoom-sm-c101-por-si-mesmo/)**. Step photos, video, precise order. Includes 2 initial screws, front/antenna covers, 8 midframe screws, flash/camera flex, motherboard. Tools Phillips PH000, plastic opening tool, tweezers. Warning: delicate coax, display and button flex connectors; record screw positions. The author labels the job easy/10 minutes, but plan for slower careful work.
5. [VRM24 — English version](https://vrm24.com/instructions/how-to-disassemble-samsung-galaxy-s4-zoom-sm-c101/). Same illustrated teardown.

## Schematics and service / troubleshooting documents (availability caveats)

6. [VinaFix, SM-C101 service manual (2019 thread)](https://vinafix.com/threads/samsung-galaxy-s4-zoom-sm-c101.35269/). Lists `Samsung SM-C101 service manual.pdf` **2.2 MB** with manufacturer/model and downloadable attachment **behind paid membership**; contents not verified.
7. [GSM-Forum, SM-C101 schematic diagram and troubleshooting thread](https://forum.gsmhosting.com/vbb/f258/samsung-sm-c101-galaxy-s4-zoom-schematic-diagram-1826466/). Service/troubleshooting and PCB layout referenced. A 2018 reply attaches **five RAR parts** of `samsung SM-C101 service manual troubleshooting`; may require login and availability check. Avoid untrusted executables.
8. [Servicell Arauca, multi-model PDF file index](https://www.servicell-arauca.com/foros/showthread.php?tid=24456). Index explicitly lists folder `samsung/SM-C101/` and **Cover.pdf, Product Specification.pdf, Disassembly & Reassembly.pdf, Electrical Part List.pdf, Exploded View.pdf, Part List.pdf, Troubleshooting.pdf**; **index only** — no direct PDF or contents verified here.

## Field reports / analogies

9. [iFixit — completely dead despite new battery, December 2016](https://www.ifixit.com/Answers/View/359202/Phone+wont+start+or+charge+at+all). Anecdotal user report, repair recommendation not a confirmed diagnosis. **Ignore unsupported heat-gun/reflow claim in later comment.**
10. [Russian GSMForum — dead device, transients, MAX77693/8767-60 discussion 2016–2018](https://gsmforum.ru/threads/samsung-galaxy-s4-zoom-sm-101.254396/). Several independent authors. See [case studies](CASE-STUDIES.md) for translations and qualifications.
11. [GSM-Forum — SM-C101 eMMC Boot1/no Download Mode discussion (2016)](https://forum.gsmhosting.com/vbb/f664/sm-c101-change-kmvnw000lm-b206-kmvtu000lm-b503-2168038/). Specialist-level repair anecdote, not a first-step procedure.
12. [XDA — spontaneous S4 Zoom shutdown thread (2013)](https://xdaforums.com/t/q-samsung-galaxy-s4-zoom-turns-off-bug.2585150/). Page inaccessible during this pass; lead only.

## Retrieval policy / evidence gates

- Preserve actual original service manual PDFs (where legally accessible) with filename, source URL, retrieval date and SHA-256 **privately** if license/access terms permit.
- Don't infer IC pinouts from forum prose. Derive exact test pads, grounds and voltages from verified schematic and board revision or direct tracing.
- Don't silently promote chipset and IC names from similar Samsung Galaxy S4 **non-Zoom** phones.
- Do not store owner's phone IMEI/serial, raw personal photos or unredacted USB logs in this public repository.
