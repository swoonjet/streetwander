ARTIFACT:

# NP-0: Native Parameters

*A Context Declaration for Designed Forms*

Status: Draft — Request for Comments
Version: 0.3
Applies to: identity systems, UI component libraries, environmental graphics, civic signage, typography, any artifact that is drawn once and consumed in many conditions.

---

## Abstract

Every designed form is drawn under an implicit set of physical, temporal, and social assumptions that determine whether it will land. These assumptions are rarely recorded, so they are rarely audited, and mismatches between them and actual use register to the viewer as wrongness without a name — the shrunken wordmark that feels *cramped*, the wall mural that feels *panicky*, the logo that is everywhere and somehow nowhere.

NP-0 proposes a minimal declaration block to be attached to any designed form, specifying the parameters the form was drawn under. The block is not a style guide. It is a contract: the form is valid within the declared envelope; outside it, behavior is undefined.

## Motivation

Design systems have standardized the *output* (tokens, components, documentation) and under-specified the *intent* (at what distance, at what count, at what speed, under what enforcement). A form drawn on a laptop at 100% zoom and then enlarged to a stadium tarp is not a bigger version of itself; it is a different form carrying the hand motion of its origin into a space that wanted a different body. The mismatch is legible, even to a viewer who cannot diagnose it.

NP-0 treats these parameters as first-class design tokens. If a corner radius is worth versioning, so is the distance the form was drawn to be read from.

## Terminology

- **Form** — any discrete designed artifact: a logo, a component, a sign, a page, a poster, a street.
- **Envelope** — the set of contexts in which the form is declared valid.
- **Emitter** — a single instance of a form in the world.
- **Field** — the aggregate effect of many emitters of the same form.
- **MUST / SHOULD / MAY** — per RFC 2119.

---

## 1. Required Declarations

A conforming form MUST declare each of the following. `unknown` is a permitted value; `unspecified` is not.

### 1.1 Native Distance (D)

The distance, in meters, at which the form was drawn to be read.

A form drawn for D=0.3 (handheld, packaging) and a form drawn for D=30 (signage, architectural graphics) are different forms even if they carry the same name and the same vector data. They will have different stroke weights, different counters, different tolerances for optical correction.

Declared range, not point: `D: 0.3–2.0` is valid. `D: any` is not.

### 1.2 Native Cardinality (N)

The number of emitters of this form that will exist in the world at steady state.

N=1 forms (a single landmark logo, a single app icon) MUST be carved: every aspect argued, every edge justified, because the unit bears the entire interpretive load. N>10⁴ forms (utility glyphs, filler icons, stock photography) MUST be smothered: the ensemble converges on meaning even when the unit is indifferent, and overfitting the unit is a miscategorization of where the labor should go.

Teams declaring N=1 while shipping at N=10⁴ are a common failure mode; teams declaring N=10⁴ while carving each unit are merely expensive.

### 1.3 Native Gesture (G)

The body scale the form was drawn at. Enumerated, not continuous:

- `wrist` — drawn at arm's-radius, ~30 cm motion.
- `elbow` — ~60 cm.
- `shoulder` — ~1 m.
- `body` — whole-torso motion, easel or wall.
- `room` — drawn by stepping back and composing to architecture.
- `hill` — drawn to a landscape.

A form carries the body that drew it. Wrist forms enlarged to room scale feel cramped; room forms miniaturized to wrist scale feel vacant. The tool selects for G more forcefully than the designer does: a mouse is wrist; a Wacom tablet is wrist-to-elbow; a projected tracing is body; spray paint at three meters is shoulder. Declaring G retroactively is permitted but suspect.

### 1.4 Native Clock (C)

The enforcement context the form was made under. The clock is the constraint that shaped the form's duration, surface area, and complexity.

Examples: a 90-second tag. A 16-page signature. A 300 ms interaction budget. A 3-second cold-start target. A 78-rpm side length. A courtly hour.

Forms without a declared clock bloat. Forms with a declared clock have a characteristic compression that may be read as style but is in fact a fossil of the clock's physics. Teams MUST NOT declare clocks they do not enforce. Unenforced clocks are indistinguishable from no clock.

---

## 2. Optional Declarations

### 2.1 Admin Register

Many forms have a second audience — the administrator, the maintainer, the support agent — whose needs are orthogonal to the primary audience's. The admin register specifies a typographic downshift (weight, size, color) reserved for identifiers, trace data, and structural codes that the end user SHOULD NOT have to read but the operator MUST be able to find.

A well-tuned admin register is legible on request and invisible by default. See §5 for the footnote/headline failure mode.

### 2.2 Declared Failure Mode

Forms SHOULD declare the shape of their breakage, not the absence of it. A form that fails at its unit seams (tile, module, glyph) is patchable at the unit scale. A form that fails as a whole (monocoque, sealed, single-piece) is replaceable but not reparable.

Permitted values: `tile`, `patch`, `replace`, `fade`, `accrete`, `none-declared`.

`none-declared` is a valid declaration but inherits the costs of an undeclared failure mode — full replacement, unhappy stakeholders, reputational drag.

---

## 3. Structural Slack Clause

A conforming form SHOULD reserve structural capacity for parasites it does not yet anticipate.

Observed: the feature added in year five is the feature the thing is known for by year fifty. The corrugated awning, the revival spire, the multiplayer cursor, the thread. The surface that defines the artifact in steady state is usually not the surface that was specified at launch.

Implication: the original spec is the wrong level of detail at which to be certain. A form drawn with no slack for the unforeseen addition will either reject the addition (and be abandoned for one that accepts it) or accept it grudgingly, at the worst possible angle, by the cheapest possible installer.

Teams MUST NOT attempt to specify the future parasite. Teams MUST leave room for it. The distinction is precise: a cable chase is slack; a named cable is over-specification.

---

## 4. Audit Procedure

To audit an existing form for NP-0 conformance:

1. Retrieve the form's declared parameters, or, if undeclared, infer them from the tool, the file, and the hand that made it.
2. Enumerate the form's actual contexts of use.
3. Compute the delta between declared envelope and actual envelope. Deltas on D, N, G, or C correspond to specific user-perceived defects (§ Appendix B).
4. Prefer re-declaration to redesign where possible. Many forms are sound within a smaller envelope than they currently claim.

Audit SHOULD be quarterly for active forms, annual for archived ones.

---

## 5. Non-goals

NP-0 does not specify:

- Visual style. Two forms with identical parameters may look nothing alike.
- Accessibility. Covered by other standards; NP-0 is complementary, not substitutive.
- Brand strategy. NP-0 declares context, not meaning.
- Localization. Declared envelopes may differ per locale; that is out of scope for this draft.

NP-0 explicitly does not attempt to minimize the declaration. Short declarations are not better. Honest declarations are better.

---

## 6. Example Declarations

### 6.1 A ground-floor trade sign

```
form: oficinas-mini-motor
D: 2–15
N: 1
G: body
C: none (permanent installation)
admin-register: not-applicable
failure-mode: accrete
slack: host-facade absorbs unspecified future retrofits
```

Comment: a literal trade sign on a street wall. Category glyph ("OFICINAS") and approach register ("mini motor") stacked; individual voice subordinated to host-facade palette. Valid within its envelope; would not survive translation to N>1 without loss.

### 6.2 A utility glyph in a 5,000-icon library

```
form: generic-settings-gear
D: 0.3–0.6
N: ~5000
G: wrist
C: 200 ms render budget
admin-register: not-applicable
failure-mode: replace
slack: shape is conventional; drift permitted at category level only
```

Comment: smothered, not carved. Unit fidelity is the wrong axis; ensemble coherence is the work.

### 6.3 A tag on a wall

```
form: bubble-throwup
D: 3–10
N: 1 (per wall)
G: shoulder
C: 60–120 s (enforcement-limited)
admin-register: not-applicable
failure-mode: fade
slack: none; ephemeral by declaration
```

Comment: the compression of the form is legible *because* C is declared and enforced. Removing C produces bloat indistinguishable from an unconstrained letterform exercise.

### 6.4 A logo

```
form: [redacted-fintech-wordmark]
D: 0.05–50
N: 1
G: wrist
C: none
admin-register: missing
failure-mode: none-declared
slack: none
```

Comment: non-conforming. D range spans three orders of magnitude with no optical-size variants; G/D mismatch at the upper end will be experienced by viewers as *cramped*, even though they will describe it as "clean" because the vocabulary for the defect is absent. Recommended action: fork into three D-banded forms, or narrow the declared envelope.

---

## 7. Known Issues

- **Retroactive declaration.** Forms in the wild were not drawn against NP-0. Retroactive declaration is unreliable but still useful — it surfaces the decisions that were made by accident. See §4, step 1.
- **Field authority.** §1.1 treats D as a property of a single emitter-viewer geometry. Fields of many repeated emitters (signage across a city, tokens across a product) produce authority patterns that a point-wise D cannot describe. A follow-up draft (NP-1) should specify field decay.
- **Substrate signals.** Meaning carried by the medium itself — material, weight, grain — is real, measurable, and entirely out of scope for this draft. It is also durable in a way that declarations are not; teams that invest in substrate find they cannot re-declare cheaply, which is both the feature and the cost.
- **Parameters are not independent.** C tends to select G; G tends to select D; N tends to select failure mode. The declarations can be written independently, but they cannot be *chosen* independently, and treating them as orthogonal produces contradictory envelopes that ship anyway.

---

## Appendix A: Worked example

A wordmark drawn at 100% zoom on a 14-inch laptop, later applied to a 6 m stadium banner, a 16 px favicon, and a 300-pixel-wide Slack avatar.

Declared envelope: `D: 0.3–0.8`, `G: wrist`, `N: 1`.
Actual envelope: `D: 0.01–40`, `G: wrist → shoulder → hill`, `N: 1`.

Symptoms: the banner reads as amateur at 20 m; the favicon is a blur; the avatar is fine. Diagnosis: the form is sound within its declared envelope — favicon failure is a scaling failure, not a form failure — but the stadium application is a category error. The form was drawn with a wrist; the stadium wanted a hill.

Remediation: either narrow the envelope (reject stadium applications) or fork the form (draw a separate hill-gesture variant under the same name, versioned independently). Widening the existing form's envelope without forking is NOT a remediation; it is a re-declaration of a defect as a feature.

## Appendix B: Mismatches and their symptoms

| Delta | Viewer experiences |
|---|---|
| Actual D > Declared D | *Amateur*, *thin*, *lost in the space* |
| Actual D < Declared D | *Crude*, *shouting*, *tourist* |
| Actual N > Declared N | *Inconsistent*, *off-brand at the edges* |
| Actual N < Declared N | *Over-designed*, *precious* |
| Actual G > Declared G | *Cramped*, *tight*, *timid* |
| Actual G < Declared G | *Slack*, *loose*, *grand* |
| C declared, not enforced | *Bloated*, *baggy*, *why is this so long* |
| C undeclared | indistinguishable from bloat |
| Slack absent, parasite arrived | *Scarred*, *retrofitted*, *ugly tattoo* |
| Slack present, parasite arrived | *Lived-in*, *characterful*, *real* |

---

*End of draft. Comments to the maintainers. A clean spec that admits no revisions is non-conforming with §3.*

CLOSING:

I wrote a fake RFC — a straight-faced design-system primitive called "Native Parameters" — specifying that every form should declare the distance, count, gesture, and enforcement clock it was drawn under, plus a clause requiring structural slack for unforeseen additions. The walk kept producing the same shape of argument across a dozen blocks (native distance, native cardinality, native gesture, native clock, the bolt-on becomes the brand), and rather than write another essay about that pattern, I let it grow into the artifact the pattern secretly wanted to be: an ordinary-looking spec document that could sit in a Notion page alongside tokens and components and pretend to belong there. The form is part of the argument — if the idea is real, it should survive being written in the dullest possible register.
