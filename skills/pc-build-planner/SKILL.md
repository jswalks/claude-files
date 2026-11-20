--
name: "pc-build-planner"
description: "Plan a custom desktop PC build and find where to buy each part, especially during sales like Black Friday: requirements, compatibility checks, UK price comparison and deal validation."
---
 
# PC Build Planner
 
A repeatable method for speccing a desktop PC, checking every part is compatible, and buying each part at a genuinely good price. Default market is the UK (prices in GBP, incl. VAT) unless the user says otherwise.
 
Hardware generations, prices and stock change constantly. Never spec from memory: search for current-generation parts, current reviews and live prices before recommending anything, and say when a price was checked.
 
## 1. Gather requirements (ask once, briefly)
 
Ask only what's missing, in one message:
- **Budget**: total, and whether it includes monitor, peripherals, Windows licence.
- **Primary uses**: gaming (target resolution + refresh rate, key titles), productivity, local AI/LLMs (VRAM matters most), video editing, virtualisation/Docker, streaming.
- **Reused parts**: GPU, storage, case, PSU (check PSU age/quality before reusing).
- **Constraints**: size (ATX / mATX / ITX), noise, aesthetics (RGB, white build), Wi-Fi, upgrade path, brand preferences.
- **Deadline**: buying during a specific sale window?
If the user is unavailable, assume a balanced build for their stated use and state the assumptions at the top.
 
## 2. Allocate the budget
 
Start from the use case, then adjust to current prices:
- **Gaming**: GPU ~35-45% of the tower budget; CPU ~15-20%.
- **Local AI/LLMs**: prioritise GPU VRAM above raw speed; 64GB+ system RAM; fast NVMe for models.
- **Productivity / compilation / VMs**: more CPU cores and RAM; GPU can be modest.
- Never cut corners on the PSU: pick a reputable unit from current PSU tier lists.
## 3. Pick parts (research before choosing)
 
For each category, search for current reviews and benchmarks (e.g. Tom's Hardware, TechPowerUp, Gamers Nexus, Hardware Unboxed) and choose 1 primary pick + 1 alternative:
CPU, CPU cooler, motherboard, RAM, GPU, storage (NVMe), PSU, case, case fans, OS.
 
Record for each part: exact model number / MPN (critical for price matching), key specs, why it was picked.
 
## 4. Compatibility checklist (must all pass)
 
- **CPU ↔ motherboard**: same socket; chipset supports the CPU; check whether a BIOS update is needed for this CPU and whether the board has BIOS Flashback.
- **RAM**: correct DDR generation; speed within the platform's sweet spot; ideally on the board's QVL; 2 sticks preferred over 4 for DDR5 stability; EXPO (AMD) / XMP (Intel) profile.
- **Motherboard ↔ case**: form factor fits.
- **GPU ↔ case**: GPU length and thickness (slots) within case clearance, accounting for front radiators/fans.
- **Cooler**: supports the socket; air cooler height under case limit; AIO radiator size supported at the chosen mount position; cooler rated for the CPU's power draw.
- **PSU**: wattage = CPU max power + GPU board power + ~100W, then ~30-50% headroom; ATX 3.x with native 12V-2x6 cable for GPUs that need it; PSU length fits the case.
- **Storage**: number of M.2 slots; PCIe generation; lane sharing (some M.2 slots disable SATA ports or drop the GPU slot to x8: check the manual).
- **Connectivity**: enough fan/RGB headers, USB-C front panel header if the case has one, Wi-Fi/Bluetooth if needed.
Cross-check the final list on PCPartPicker UK (uk.pcpartpicker.com) and use its compatibility warnings, but don't rely on it alone; verify clearances against manufacturer spec pages.
 
## 5. Price comparison
 
For every part, find the best current UK price from a reputable seller:
- **Tools**: WEM Price Compare (`wem:compare`, `wem:deal`, `wem:verify`) for cross-retailer prices; Canopy (`canopy:amazon-price-and-deals`) for Amazon UK; PCPartPicker UK price lists; the browser to check retailer pages directly.
- **UK retailers to check**: Scan, Overclockers UK, CCL, Box, Ebuyer, Novatech, Aria PC, Amazon UK, Currys, Argos.
- Match on exact model / MPN, not product name (GPU variants differ in cooler, clocks, length).
- Include delivery cost; note stock status and dispatch time.
- On Amazon, check who it's **sold and dispatched by**. Prefer Amazon or the brand over unknown marketplace sellers.
- Consider bundles (CPU + board + RAM combos) and cashback/game codes, but value them at real worth.
## 6. Validate deals (is it actually a deal?)
 
- Check price history: PCPartPicker UK price history, Keepa or CamelCamelCamel (UK) for Amazon.
- A "was" price only matters if the item actually sold at it recently. Compare with the 30-90 day low.
- Check hotukdeals for the item to see community-reported lows and seller issues.
- Re-verify any price right before recommending purchase (`wem:verify` or the live page). Black Friday prices change hourly.
- Flag anything that looks too good from an unfamiliar seller.
## 7. Buying advice (UK)
 
- Online purchases normally carry a 14-day cancellation right under the Consumer Contracts Regulations; check each retailer's returns policy, especially for opened items.
- Paying by credit card for single items costing £100-£30,000 gives Section 75 protection.
- Splitting the order across retailers to get the cheapest price on each part is fine; note the extra delivery costs and multiple warranty contacts.
- Order the motherboard early enough to check whether it needs a BIOS update.
- Mention that this is general guidance, not legal or financial advice.
## 8. Deliverable
 
Produce a **build sheet** as a Sheets artifact (or the format the user asks for) with one row per part:
Category | Part (exact model) | Key specs | Retailer | Price (£) | Delivery | Link | Price checked at | Deal verdict (good / fair / wait) | Alternative
 
Plus a total, budget remaining, and a short summary in the reply: the build's expected performance for the stated use, any compatibility notes (e.g. BIOS update needed), and which prices are time-sensitive.
 
If the user wants to wait for better prices, offer a scheduled task to re-check the build's prices on chosen dates (e.g. Black Friday and Cyber Monday).
