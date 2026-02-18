# assisted_recon
Search &amp; Strike: Assisted Recon

Below is a **high-level product specification** for a *Cannon Fodder / Desert Strike–inspired* “Where’s Wally?”-style target detection game with tiered AI assistance modes.

I’ll keep this structured in a way you could realistically use for a lightweight GDD (Game Design Document) or internal pitch.

---

# 1. Working Title

**“Search & Strike: Assisted Recon”**
(Alt names: *Fog of Targeting*, *Operation Needlefield*, *Overwatch: Human-in-the-Loop*)

---

# 2. Core Concept

A top-down / isometric battlefield search game where the player must identify and confirm specific military-style targets hidden within dense, cluttered environments.

The player may choose between:

* **No AI Support**
* **Fast AI Support (High Recall, Low Precision)**
* **Slow AI Support (Higher Precision, Slower Latency)**

The core tension:
**Speed vs Accuracy vs Trust in AI**

This is not a shooter. It is a **cognitive detection and classification game**.

---

# 3. Player Objective

For each level:

* Identify N hidden targets (e.g. radar stations, SAM launchers, supply trucks).
* Avoid false positives (civilian vehicles, decoys, damaged assets, shadows).
* Complete within time and error constraints.

Victory is based on:

* Correct identifications
* False positive rate
* Missed targets
* Completion time
* AI usage efficiency

---

# 4. Core Gameplay Loop

1. Player loads into dense isometric battlefield scene.
2. Mission briefing:

   * “Locate 6 mobile SAM units before they relocate.”
3. Player scans manually OR activates AI.
4. AI highlights candidate targets (depending on mode).
5. Player confirms or rejects highlighted objects.
6. Score calculated.
7. Debrief shows:

   * True Positives
   * False Positives
   * Missed Targets
   * AI reliability metrics
   * Trust alignment score

---

# 5. Game Modes

## 5.1 No AI Mode (Pure Human)

**Description:**

* Player manually searches.
* No hints.
* Highest potential score multiplier.

**Design Intent:**

* Tests human visual search.
* Encourages slow, methodical scanning.
* Serves as baseline performance metric.

**Scoring:**

* +100 per correct target
* −50 per false identification
* −100 per missed target
* 1.5x score multiplier

---

## 5.2 Fast AI Mode (“Tactical Scan”)

**Description:**

* Instant overlay of highlighted candidate targets.
* High recall (rarely misses targets).
* Low precision (many false positives).

**Behaviour Model:**

* Detects ~90% of real targets.
* False positive rate ~30–40%.
* Highlights decoys, trucks, shadows, similar shapes.

**Design Intent:**

* Encourages filtering.
* Tests player judgment under noisy AI assistance.
* Models overconfident but weak CV systems.

**Tradeoffs:**

* Fast.
* Overwhelming.
* Requires cognitive triage.

**Scoring Adjustment:**

* −20% score multiplier.
* Additional penalty if player blindly accepts all AI suggestions.

---

## 5.3 Slow AI Mode (“Strategic Analysis”)

**Description:**

* Player must wait 5–10 seconds per scan.
* Produces fewer false positives.
* May still miss some targets.

**Behaviour Model:**

* Detects ~80–85% of real targets.
* False positive rate ~5–10%.
* Does not highlight decoys as often.
* Scan animation reinforces “compute time.”

**Design Intent:**

* Models deliberative AI.
* Encourages strategic timing.
* Introduces pacing tension.

**Scoring Adjustment:**

* −10% score multiplier.
* Time penalty for each scan activation.

---

# 6. AI Personality Layer (Optional Advanced Feature)

Each AI mode can have personality framing:

| AI Name    | Type         | Personality                           | Behavior Trait              |
| ---------- | ------------ | ------------------------------------- | --------------------------- |
| “Hawkeye”  | Fast AI      | Overconfident                         | Flags aggressively          |
| “Sentinel” | Slow AI      | Cautious                              | Rare but careful highlights |
| “Ghost”    | Experimental | Occasionally withholds correct target |                             |

This supports future expansion into:

* Trust calibration mechanics
* AI with “motives”
* Unreliable system narrative

---

# 7. Level Design

## Environments

* Desert airfield
* Urban combat zone
* Jungle encampment
* Arctic radar station
* Coastal missile site

Each environment includes:

* Visual clutter density variable
* Civilian-like objects
* Decoys
* Camouflage mechanics
* Lighting variation
* Weather (dust, fog, smoke)

---

# 8. Target Types

* SAM launchers
* Radar dishes
* Armoured vehicles
* Fuel depots
* Command tents
* Mobile missile carriers

Each has:

* Visual similarity variants
* Damaged variants
* Civilian look-alikes

---

# 9. Scoring System

Final score formula example:

```
Score = 
  (True Positives × 100)
  − (False Positives × 50)
  − (Missed Targets × 100)
  − (AI Activation Penalty)
  − (Time Factor)
  × Mode Multiplier
```

---

# 10. Trust Calibration Mechanic (Advanced Layer)

Track:

* Player acceptance rate of AI suggestions.
* Player rejection accuracy.
* Overtrust vs undertrust index.

At end of mission:

“You relied on AI suggestions 87% of the time.
AI false positive rate was 32%.
Your optimal trust level would have been 61%.”

This introduces:

* Human-autonomy teaming lessons.
* Calibration gameplay.
* Meta-performance feedback.

---

# 11. Difficulty Scaling

Variables:

* Number of targets
* Density of clutter
* Similarity of decoys
* AI reliability degradation
* Moving targets
* Time limits

Advanced levels:

* Targets relocate if not found quickly.
* AI reliability shifts dynamically.
* Electronic warfare interference reduces AI performance.

---

# 12. UI Elements

* Isometric battlefield
* Zoom + pan
* AI overlay highlights (glow or box)
* Target confirmation click
* Mission progress tracker
* AI reliability indicator (hidden vs visible optional)

---

# 13. Ethical Framing Option (If Desired)

To avoid real-world sensitivity:

* Stylized, toy-soldier aesthetic (Cannon Fodder tone).
* Fictional factions.
* Abstracted military assets.
* Emphasis on detection, not destruction.

---

# 14. Potential Educational Angle

This game naturally demonstrates:

* Human-AI teaming
* False positive fatigue
* Automation bias
* Trust calibration
* Speed-accuracy tradeoff

Given your interest in HAT assessment work, this could become a serious-game research testbed.

---

# 15. MVP Scope (Realistic Build)

**Phase 1:**

* 3 levels
* 3 AI modes
* Static targets
* Basic scoring

**Phase 2:**

* Trust analytics
* Dynamic AI reliability
* Moving targets
* Narrative wrapper

---

# 16. Why This Works

It’s:

* Simple
* Scalable
* Visually rich
* Mechanically tight
* Experimentally useful

It also creates emergent tension:

> “Do I trust the AI… or is it flooding me again?”

---

If you’d like, I can next:

* Write a one-page pitch deck summary
* Create a research framing version for a HAT study
* Design a more cyberpunk or Gibson-style narrative skin
* Or define a technical architecture (e.g., Unity + lightweight CV simulation backend)

