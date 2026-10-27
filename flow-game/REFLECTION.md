# Flow — Written Reflections

These are draft responses for the three written rubric categories. Review, personalize, and revise them in your own voice before submitting.

---

## Reflection 1: Prototyping

**What was accomplished:**
I built a complete, playable prototype of Flow — a water-allocation puzzle game inspired by charity: water's mission. The game includes 15 distinct puzzles spread across 3 towns, a full scoring/XP system, town progression, a local leaderboard, achievements, educational facts, and responsive layouts for mobile, tablet, and desktop. Everything runs in the browser with no backend, using plain HTML, CSS, and vanilla JavaScript, with `localStorage` handling persistence between sessions.

**What works:**
The core loop — allocate water with sliders or +/− buttons, submit, see an efficiency score and XP reward, retry or continue — is fully functional and tested. The efficiency formula (fully satisfied zones ÷ total zones) and the XP brackets (85%+/60–84%/below 60%) are implemented exactly as specified and verified against boundary cases (59%, 60%, 84%, 85%). The anti-farming protection works: resubmitting an identical solution only awards the *difference* over your previous best, not full XP again. Two challenge mechanics are implemented — water shortage (supply below total demand) and pipe leakage (a fixed loss applied before distribution) — along with a "critical building" mechanic where certain levels force a genuine trade-off between funding the hospital and funding everything else.

**What was challenging:**
Designing the actual puzzle numbers was the trickiest part. Every level needed to have a valid best-possible outcome and never require an impossible score, which meant hand-verifying (and then programmatically re-verifying via brute-force subset checking) that every one of the 15 puzzles has an achievable solution at its intended difficulty — including the Town 3 levels, which were deliberately tuned so that the *only* way to reach the best possible score is to sacrifice the critical hospital. That forced trade-off was a deliberate design choice to make the scarcity feel meaningful rather than arbitrary.

**What could be improved in the next version:**
Real illustrated artwork instead of emoji-based building icons would raise the visual polish significantly. A backend (even a lightweight serverless one) would let the leaderboard be genuinely shared across players instead of local-only. I'd also like to add more granular difficulty curves within each town rather than a flat 5-puzzle structure, and expand the achievement list.

**What was learned:**
Building this reinforced how much small balancing decisions affect whether a "puzzle" actually feels like a meaningful decision versus a math exercise — the difference between a shortage puzzle with multiple valid 75% solutions versus one with a single forced trade-off completely changes how it feels to play. It was also a good exercise in keeping game state, UI state, and persistence cleanly separated so the displayed values always match the actual internal state.

---

## Reflection 2: Talking Points

**What Flow is:**
Flow is a browser-based educational puzzle game where players act as water-resource managers for a town, deciding how to distribute a limited water supply across a hospital, homes, a school, and a factory. It's inspired by charity: water's mission to bring clean water to communities that lack reliable access.

**How players interact with it:**
Players use sliders or +/− buttons to allocate water to each building, watching in real time as buildings show whether they're fully satisfied, partially satisfied, or unsatisfied. Submitting a distribution scores the round and reveals how well the town's needs were met.

**How scoring works:**
Efficiency is calculated as the percentage of buildings that received *at least* their full water demand — not the percentage of total water used. That distinction is the central lesson of the game: spreading water thin across everyone isn't necessarily better than fully meeting fewer critical needs. Scoring tiers (Success, Partial Success, Needs Improvement) award XP accordingly, and later levels introduce water shortages, pipe leakage, and a critical hospital building that can't always be fully funded — forcing players into the same kind of prioritization real water-scarce communities face.

**How it connects to charity: water's mission:**
The game is a conversation-starter, not a donation platform. After every puzzle, players see a short fact about the real-world impact of clean water access — on health, education, and local economies — and the home screen links directly to charitywater.org for anyone who wants to learn more or support real projects. The game is explicit that it is an unofficial, independent educational prototype, not an official charity: water product, and that gameplay doesn't generate real-world donations.

**Future improvements planned:**
Replacing placeholder icon art with original illustrations, building a lightweight online leaderboard, and expanding the puzzle library with new challenge types (e.g., seasonal supply changes, multi-town resource sharing).

---

## Reflection 3: LinkedIn Post

I just finished building **Flow**, a browser-based puzzle game prototype inspired by charity: water's mission to bring clean water access to communities around the world.

In Flow, you manage a limited water supply across a hospital, homes, a school, and a factory — deciding who gets fully funded and who doesn't. The scoring is intentionally not "how much water did you use," but "how many critical needs did you actually meet" — a small design choice that turns out to teach a real lesson about resource prioritization under scarcity.

Built with plain HTML, CSS, and vanilla JavaScript (no frameworks, no backend) — 15 puzzles across 3 towns, a working XP/progression system, local leaderboard, achievements, and a couple of challenge mechanics (water shortages and pipe leakage) that force genuinely hard trade-offs in the later levels.

It was a fun exercise in game balancing — making sure every level has a fair, achievable "best possible" outcome even when a perfect score isn't mathematically available — and in keeping UI, game logic, and persistence cleanly separated so the game state is always trustworthy.

Flow is an independent, unofficial educational project — not affiliated with or endorsed by charity: water, and it doesn't generate real donations. But if it gets even a few people thinking about water access and clicking through to learn more about the real organization, that's a win. 💧

#gamedevelopment #javascript #webdev #sideproject
