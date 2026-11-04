# Addon Adder 1.23 — one hold, one imp

## The wake fix

Holding a dormant imp item on its job block used to wake a
whole swarm. The game re-fires the use action for as long as
the button is held, and every fire ran the wake handler
again — one 450 ms hold produced **eleven** Sprout Imps from
a single dormant item (only the first spawn consumed the
item; the queued repeats spawned anyway).

The fix, in every helper pack's wake handler: before
spawning, check whether an imp is already bound to that
exact block. If one is, the repeat fire stands down. First
imp claims the block; the swarm is impossible.

**Proven in Austin's actual game** (2026-11-03, flat test
world, survival, one 450 ms held use on the composter): the
"Your Sprout Imp is awake" message fired once, exactly one
Sprout Imp stood in the composter, the dormant item was
consumed, and a teleport-all count check moved exactly one
imp. Before the fix, the same hold made eleven.

## Refreshed packs

- **Cinder Imp 1.3.6** — wake fix, plus banked XP now
  rounds to one decimal on write and on claim, so the
  fractional "ghost XP" remainder (13.999… showing as a
  stuck fraction) is gone.
- **Bubble Imp 1.1.7** — wake fix.
- **Sprout Imp 1.1.7** — wake fix.
- **Lumen Imp 1.1.6** — wake fix.
- **Ledger Imp 1.1.6** — wake fix.
- **Shepherd Imp 1.1.6** — wake fix.
- **Fisher Imp 1.1.6** — wake fix.

Porter Imp was deliberately not patched: his wake routes
through a two-chest bind that already refuses repeat fires
("already has both chests"), so he can't swarm by design.
Feral Imp and The Listener have no item wake. Rogue Village
unchanged.

## Verification

- Combined BDS boot of all ten mob packs at the new
  versions: zero script/pack errors; summons found for
  Sprout, Porter, Lumen, Ledger, Shepherd, Fisher, Feral
  and The Listener in the combined boot, and Cinder +
  Bubble on a follow-up two-pack boot after a chunk settle
  (the combined-boot miss is a known rig settle artifact,
  same as 1.22's gate).
- Install sweep on Austin's PC by manifest UUID: every
  copy of the seven packs (global store, Shared tree, and
  every world's embedded packs) at the new versions, zero
  stale copies, world pins rebuilt in all four worlds.
- In-game wake proof as above (screenshots tf-inhand82f /
  tf-woke82f / tf-pile82f).
- Phone APK: versionCode 24, versionName "1.23", signer
  SHA-256 unchanged
  (`cd68dfb5ffd6c620787ba6c374bf70b92c3f580967eab5f661fe0c3677e6566c`),
  all 18 bundled .mcaddons inside the APK byte-identical
  to the staged release files; the seven refreshed packs'
  manifest versions verified inside the staged .mcaddons.
- PC app stays version 9 — its six built-ins are
  unchanged; the fixed imps reach the PC through the feed.

## Honest limits

- The Ledger fetch test from the 1.22-era playtest (a
  fetch that appeared to mint items) is being retested on
  this build: the leading theory was swarm-era parallel
  Ledger jobs, which this fix makes impossible. The solo
  retest result will land in the playtest report, not in
  these notes, because it hasn't run yet.
- Difficulty-sensitive retests (Feral, Listener) and the
  Bubble/Shepherd clean retests run under the flat world's
  real rules (Normal difficulty, keepInventory off) — the
  earlier passes ran under test settings Austin corrected
  on 2026-11-03, so those verdicts stay provisional until
  the retests land.
