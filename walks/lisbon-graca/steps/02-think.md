SEED:
- the turquoise azulejo wall on the right, tiled floor-to-roofline, reading almost as fabric from this distance
- two stacked blue "P" parking signs, the near one with "58-RC-80" and a wheelchair pictogram on a smaller plate below
- the cast-iron lamp bracket mid-frame, curling out of a pale yellow facade toward the slot of sky between the buildings

WANDER:
The azulejo wall is doing something pre-modern that we keep trying to reinvent in software: it's a *tiled* interface in the literal sense — a repeating unit, hand-painted, kiln-fired, grouted in place — and it shrugs off damage the way a good grid shrugs off bad content. Lose a tile, replace a tile; the system survives. There's a reason CSS adopted the word: a tile is the unit that makes a surface *patchable at the unit scale*. Compare that to a fresco, where a crack runs through a face and now you have a restoration debate that takes three decades and a Vatican committee. The azulejo pre-commits to its own failure mode. Which is maybe the deepest design move — not to prevent breakage but to *choose the shape of breakage*. Kintsugi does this with gold; the Japanese hand plane does this by being resharpenable forever; the Erlang language does this with "let it crash" and supervisor trees that restart the broken actor without taking the system down. Everything durable seems to have negotiated with its own decay in advance. The opposite is the monocoque car body or the sealed AirPod — beautiful until the first insult, then garbage. I think a lot of digital product design is still in the monocoque era: ship the glossy shell, pray nothing hits it, and when something does, issue a full replacement. A tile grammar would be humbler and probably longer-lived — components that fail at their own seams, by design, so the repair is cheap and the history is visible. The azulejo wall in front of me is two hundred years old and half of it has been replaced at least once, and you can see the replacements if you look — slightly different blue, slightly different crackle — and the wall is better for it, not worse.

BRANCH:
"Choose your failure mode" as a design-system axiom — every component declares not just its appearance but its preferred way of breaking.

ECHO:
Extends step 1's patch grammar directly — but flips the timing. Step 1 was about making the interim state honest after damage; this one is about pre-committing to the damage at the unit level, so the patch is already part of the spec.
