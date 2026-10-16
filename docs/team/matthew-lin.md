# MESS Team Member Doc — <Your Name>

> **How to use this template**
> 1. Copy this file to `docs/team/<your-name>.md` (lowercase, dashes, e.g. `docs/team/jane-doe.md`).
> 2. Fill in **one section per commit**, in order. That gives you 5 commits.
> 3. Use clear commit messages, e.g. `docs: add team and role intro (jane-doe)`.
> 4. Delete the instruction lines in *italics* as you fill each section in.
> 5. Be specific. "Works on sensors" is not useful; "Owns the BH1750 driver in `components/bh1750`" is.

---

## 1. Team and Role

**Team: *Team 4*

**What my team is responsible for:**
*The main part of MESS that my team is responsible for is the BME280 and BH1750. The main milestone items that this covers is to read/confirm data from each sensor individually using ESP32*


**My role on the team:**
*My main role on the team is to process the data and to build the GUI in which the data collected by the sensors will vbe displayed.*

**Teammates: *Truman Sikes, Tanay, Matthew Lin* <names>

---

## 2. How My Part Fits the System

```text
Sensors (BME280, SGP30, BH1750)
   → main/app_main.c (reads each sensor once per second)
   → mess_broadcast (queues reading, sends over ESP-NOW)
   → mess_mesh (dedup, newest-reading cache, relays up to 8 hops)
   → other boards relay it onward
   → mess_hotspot (stores readings, serves table at http://192.168.4.1/)
   → laptop / server / UI
```

**My part receives:*mess_broadcast*

**My part produces:*mess_hotspot*

**Who depends on my part:*The person reading reading the data to make inferences on the data*

**Key files / folders:*N/A, work has not yet begun*
- `path/to/file` — what it does

---

## 3. Current State and Gaps

**What works today:**

- Sensor reading is functional. I tested it by plugging the BME280 and BH1750 to the ESP 32, afterwards, we were able to test it by running Arduino on it and get readable measurements of our environment.

**What is a stub, placeholder or unfinished:**


- The current placeholder that we have is how the data from the BME280 and BH1750 is being sent and rendered by our group. We did not store the working code anywhere right now.

**What is broken or untested:**


- The relay of data from one laptop to another is currently still untested, however, it is necessary in order to be able to remotely collect data

---

## 4. Plan Through Milestone 3

### Milestone 2 (end of October): data application and meshing

| Task | Owner | Estimate | Done? |
|---|---|---:|---|
| Integrate sensor readings into `main/app_main.c` and confirm each sensor is read once per second | Me | 2–3 hours | ☐ |
| Verify readings are passed into `mess_broadcast` and sent correctly over ESP-NOW | Me | 2 hours | ☐ |
| Test that `mess_mesh` correctly deduplicates readings, updates the newest-reading cache, and relays packets between boards | Me / Mesh Team | 3–4 hours | ☐ |

### Milestone 3 (before Thanksgiving): testing gauntlet


| Test | How to run it | What "pass" looks like |
|---|---|---|
| Long runtime test | Run the system continuously for several hours while sensors send readings once per second | No crashes, memory issues, or stopped transmissions; readings continue updating normally |
| Multi-node relay test | Set up at least three boards in an A–B–C layout so A cannot directly reach C and must relay through B | Readings from A successfully reach C through B without duplicate packets |
| Node dropout test | Run several connected boards, then power off one relay node during operation | Remaining nodes continue operating and the mesh recovers or reroutes without crashing |
| Distance test | Gradually increase the distance between boards while sending readings | Packets continue to relay reliably within the expected operating range |
| Bad sensor / disconnect test | Disconnect or miswire a sensor while the firmware is running | System handles the failed sensor without crashing and other sensors or mesh functions continue working |

### Stretch goal I'd like to take on
*One goal I want to try and run is the letting our sensors run for an extended period of time because that way the sensor can get more reliable data. This will likely be done by programming the sensors to be more resilient.*

---

## 5. Risks, Dependencies and Questions

**I'm waiting on / depend on:**

- I'm waiting and depending on the setting up of the sensors to be fully finished before I continue my work.

**Risks (what could go wrong in my area):**

- A risk that I can see happening is a cache filling up too many nodes.

**Open questions for leads / other teams:**

- Will there be instructions on how to reliably extract the data and read it somewhere?

**Things I want to learn on this project:**

- I want to learn how to transfer data between devices, learn a bit of R so I can format the data, and learn how to build a GUI that uses the R processed data.