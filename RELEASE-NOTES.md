# Addon Adder 1.26 — the imps settle anywhere

## Wake an imp anywhere: ground placement

Until now a dormant imp had to be used on his job
block. Now he can be woken **on open ground**: use a
dormant imp on the **top face of any solid block**
and he wakes standing on that spot — the spot
becomes the centre of his work area (his anchor).
No station needed to start; whatever stations of
his kind stand inside the area, he tends.

- The old station wake works exactly as before —
  and Porter's two-tap chest pairing with it.
- It works on strays too: use a dormant imp on the
  ground near an unbound wild imp and he binds to
  that spot instead of a new one spawning (the item
  is not consumed), same as the station bind.
- Wake him somewhere with no station in range and
  he still wakes — his name tag says what he needs
  ("(needs a chest nearby)"), same as always.

## Bigger areas: 31-by-31

The work square grows from 21-by-21 to **31-by-31**
(fifteen blocks out in every direction from the
anchor), so a full-sized house or storage room fits
inside one imp's beat. Scan and step limits follow
the bigger square; the vertical band stays ±3.
(Lumen's patrol circle was already wider than the
square and is unchanged.)

## Every imp visibly works now

Each helper has a proper work animation, playing
while he's on a job and stopping when he idles:

- **Cinder** — scoop-and-throw at his cookers.
- **Sprout** — bends to chop and plant.
- **Bubble** — stirs with both arms, round and
  round.
- **Ledger** — rapid page-shuffle flap while he
  fetches and delivers.
- **Porter** — both arms up in a carry pose — and
  he keeps it the whole time he's hauling.
- **Lumen** — one arm raised high, holding his
  light up.
- **Shepherd** — quick snip-snip shears.
- **Fisher** — a real cast-and-hold: rod out for
  the whole fishing cycle, not just the catch.

And **Cinder's inventory icon is redrawn** on the
same template as the rest of the family — he was
the one odd-looking dormant in the inventory. His
spawn egg already matched and is unchanged.

## Porter counts, sorts, and tidies

- **Double-chest loop fixed.** A double chest is
  two blocks sharing one inventory; Porter counted
  each half as its own chest, so he took the first
  stack out of one half and put it straight back
  in the other, forever. A double chest now counts
  as **one** chest — and as a hard rule he never
  delivers into the container a stack came from.
- **Sign sorting.** Put a sign on a chest and he
  sorts by it: an exact item name ("raw iron")
  takes just that item; a group name covers the
  whole group — "ores" takes every ore block and
  raw metal, "finished material" (or "smelted")
  takes ingots and anything already smelted or
  processed. The full group list: ores, finished
  material, food, wood, stone, crops, mob drops,
  fuel, redstone. Labeled chests are destinations,
  unlabeled chests are intake, and a stack sitting
  in the wrong labeled chest gets re-homed.
- **No signs? He tidies anyway.** With no labeled
  chest in his area (and no pair tapped on
  purpose), Porter runs his own auto-sort: one
  category per chest, picked by what a chest
  mostly holds already, then empties claimed for
  the categories actually in demand. Assignments
  stick — emptying a category chest doesn't
  reassign it. Items with no chest to go to stay
  exactly where they are; nothing is ever voided
  or dropped. Signs always beat his system, and
  his system never overrides a deliberate pair.

## Fisher fishes — with your rods, in the open

- **Hand him a better rod.** Use (don't crouch) on
  Fisher while holding a rod and he takes it and
  fishes with it — **visibly, in his hand**. Any of
  Better Fishing's five rods works, and so does a
  vanilla fishing rod: its enchantments are read
  live (Lure bites faster, Luck of the Sea finds
  more treasure and bigger trophies). Hand him
  another rod and the old one comes back to you;
  pick him up and he returns the rod he's holding.
  Nothing handed to him is ever lost.
- **Same numbers as Better Fishing.** Bite windows
  by rod (Bamboo slowest, Golden Lure fastest),
  Lunker size shifts on Deep and Abyss, treasure
  from 2% (Bamboo) to 12% (Abyss) — doubled when
  the catch rolled small or regular, capped at
  40% — and the Abyss rod's Double Hook chance.
- **Fishing you can watch.** He casts to his spot,
  a bobber sits on the water, a fish swims in and
  holds under it, the bobber dips, there's a
  splash — and he reels in **that** fish: its
  species and size are decided when he casts, the
  way our fishing mod does it. Standalone, the
  catches are vanilla fish; **with Better Fishing
  in the world he uses its rods, its show, and its
  sized catches (bass included)** — he detects it
  on his own, no setup. His reel always lands the
  fish once it bites; he's a helper, not a minigame.

## Versions

| Pack | Was | Now |
|---|---|---|
| Cinder Imp | 1.3.8 | **1.3.9** |
| Sprout Imp | 1.1.8 | **1.1.9** |
| Bubble Imp | 1.1.8 | **1.1.9** |
| Ledger Imp | 1.1.7 | **1.1.8** |
| Porter Imp | 1.1.6 | **1.1.7** |
| Lumen Imp | 1.1.7 | **1.1.8** |
| Shepherd Imp | 1.1.7 | **1.1.8** |
| Fisher Imp | 1.1.7 | **1.1.8** |

Everything else in the set is byte-identical to
1.25. The PC app is unchanged too — same version
10 build, re-hosted here; none of its six built-ins
changed in 1.26.

## Honest limits

- Every pack passed its full test-rig gate on BDS
  (the base checks — ground wake, reach, outside-
  area untouched, station broken mid-run, pickup —
  plus the new ones: Porter 25/25 with double
  chests, sign reading and sticky auto-sort proven;
  Fisher 26/26 standalone and 29/29 with Better
  Fishing pinned, including a Lure 3 / Luck 3 rod
  shifting bite times exactly as the rules predict
  and both that rod and a Deep Rod coming back
  intact on pickup). What a player-less server
  cannot prove is how any of it **looks**: the work
  animations on screen, the rod in Fisher's hand
  (and its glint), the bobber, the swimming fish
  and the splash. The rig proves the state — flags
  flip, entities spawn, catches land — never the
  pixels. The on-screen looks get their first real
  proof in Austin's own playtest.
- Same honest carry-overs as the rig found them: a
  real player's ground tap delivering the "up"
  face, and sign text typed by hand in the client
  (dyed, glowing or waxed signs included), go
  through the same stable APIs the rig exercised
  but get their first live proof in play. Bubble's
  finished-brew detection is the unchanged 1.25
  poll logic (a script-stocked stand never finishes
  a brew on a headless server, with or without
  him) — his service cycle is gate-proven end to
  end; a full brew under him is playtest territory.
- One fishing footnote: the current Better Fishing
  build ships no catfish item, so on the rare roll
  where Fisher's table picks catfish, the catch
  lands as a cod (documented fallback, no fish
  shown). Every other rolled fish shows and lands
  as itself.
- A movement limitation older than this release
  (present since the 1.3.7 hop system): an imp
  whose straight hop path crosses a container's
  cell at feet level can orbit that block. The
  gates lay their arenas out around it, and 1.25
  playtest layouts never hit it; a real fix belongs
  to a movement pass of its own, not this release.
- Lumen keeps his `@minecraft/server` **2.3.0** pin —
  his light-level APIs exist only there. Every other
  pack pins 2.0.0 / server-ui 2.0.0 as before.
