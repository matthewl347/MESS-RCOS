# MESS Team Member Doc — <Your Name>

> **How to use this template**
> 1. Copy this file to `docs/team/<your-name>.md` (lowercase, dashes, e.g. `docs/team/jane-doe.md`).
> 2. Fill in **one section per commit**, in order. That gives you 5 commits.
> 3. Use clear commit messages, e.g. `docs: add team and role intro (jane-doe)`.
> 4. Delete the instruction lines in *italics* as you fill each section in.
> 5. Be specific. "Works on sensors" is not useful; "Owns the BH1750 driver in `components/bh1750`" is.

---

## 1. Team and Role

**Team:*Team 4*

**What my team is responsible for:**
*The main part of MESS that my team is responsible for is the BME280 and BH1750. The main milestone items that this covers is to read/confirm data from each sensor individually using ESP32*


**My role on the team:**
*My main role on the team is to process the data and to build the GUI in which the data collected by the sensors will vbe displayed.*

**Teammates: *Truman Sikes, Tanay, Matthew Lin* <names>

---

## 2. How My Part Fits the System
*Commit 2 — `docs: describe how <area> fits the system (<name>)`*

*Explain where your piece sits in the data flow below. What does it receive, what does it produce, and who uses its output?*

```text
Sensors (BME280, SGP30, BH1750)
   → main/app_main.c (reads each sensor once per second)
   → mess_broadcast (queues reading, sends over ESP-NOW)
   → mess_mesh (dedup, newest-reading cache, relays up to 8 hops)
   → other boards relay it onward
   → mess_hotspot (stores readings, serves table at http://192.168.4.1/)
   → laptop / server / UI
```

**My part receives:**

**My part produces:**

**Who depends on my part:**

**Key files / folders:**
- `path/to/file` — what it does

---

## 3. Current State and Gaps
*Commit 3 — `docs: add current state and gaps for <area> (<name>)`*

**What works today:**
*Things you have actually run or tested. Say how you tested them.*

-

**What is a stub, placeholder or unfinished:**
*e.g. "bh1750.c still returns the placeholder `BH1750`; the working code is only in firmwareBH1750."*

-

**What is broken or untested:**
*e.g. "Relay through a middle board (A–B–C test) has not been run on real hardware."*

-

---

## 4. Plan Through Milestone 3
*Commit 4 — `docs: add milestone plan for <area> (<name>)`*

### Milestone 2 (end of October): data application and meshing
| Task | Owner | Estimate | Done? |
|---|---|---|---|
| | | | ☐ |
| | | | ☐ |
| | | | ☐ |

### Milestone 3 (before Thanksgiving): testing gauntlet
*How will you try to break your part? (long runtime, distance, many nodes, a node dropping out, bad sensor wiring, etc.)*

| Test | How to run it | What "pass" looks like |
|---|---|---|
| | | |
| | | |

### Stretch goal I'd like to take on
*Pick one from the milestones doc or propose your own. One or two sentences on why and how.*

---

## 5. Risks, Dependencies and Questions
*Commit 5 — `docs: add risks and open questions for <area> (<name>)`*

**I'm waiting on / depend on:**
*Who or what is blocking you? e.g. "UI needs numeric readings from the sensor team before graphs show real data."*

-

**Risks (what could go wrong in my area):**
*e.g. I2C bus conflicts between sensors, hotspot and mesh sharing channel 1, cache filling up with many nodes.*

-

**Open questions for leads / other teams:**

-

**Things I want to learn on this project:**

-