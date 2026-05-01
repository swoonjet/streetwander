ARTIFACT:

---

**HANGANG IMAGING CO., LTD.** — Optical Engineering Group
INTERNAL MEMORANDUM · CONFIDENTIAL

**Document control:** ENG-OPT-2025-0411, Rev. D
**Effective:** 2025-08-19
**Author:** S. Park, Senior Optical Engineer
**Reviewers:** J. Cho (Mech), H. Yu (Compliance), M. Lee (Product)
**Distribution:** PDM, BOM Review, Sourcing (Group 2), MFG-Suwon
**Subject:** Front lens module selection — DR-series successor (project codename **TIDAL**)
**Supersedes:** ENG-OPT-2025-0411 Rev. C (2025-07-02)

---

### 1. Purpose

This memo records the rationale for selecting the front lens module for the TIDAL platform (planned MY26 launch, replacing the DR900M family in the EU/CA/AU channels). Three candidate modules were evaluated against the requirements set in PRD-TIDAL-1.4 (§4.2). A recommendation is given in §6.

### 2. Background

The DR-series has shipped approximately 3.1M front-channel units globally since the DR650 (2014). The installed front optic across the DR550 / DR650 / DR750 / DR900 line has been a Korea-sourced 3.4–3.6 mm ƒ/1.8–ƒ/2.0 wide-angle module with nominal horizontal field of approximately 122° on the 1/1.8″ sensor (DR900M-1CH). Distortion characteristic: barrel, peak −34 % at corner, monotonically increasing from center, with the inflection point falling well outside the safe-area mask used by the on-board parking-mode motion detector.

The customer base, the firmware fleet, and the parking-mode neural detector (FW v9.x and forward) have all been trained against, and tuned around, this geometric profile. Departures from the established profile carry downstream cost; this memo accounts for that cost.

### 3. Requirements (summary, full set in PRD §4.2)

| Req. ID | Description | Target |
|---|---|---|
| OPT-01 | Horizontal field of view (corner-to-corner, image circle) | ≥ 118°, ≤ 130° |
| OPT-02 | ƒ-number, full open | ≤ ƒ/2.0 |
| OPT-03 | Chief ray angle at sensor edge, matched to IMX678 µ-lens map | ≤ 32° |
| OPT-04 | MTF50 on-axis @ 4K Nyquist (0.5 cy/px), best focus | ≥ 0.42 |
| OPT-05 | MTF50 corner @ 0.7 field, best focus | ≥ 0.18 |
| OPT-06 | IR-cut, 650 nm @ 50 % | per spec sheet HK-IR-440 |
| OPT-07 | Mechanical fitment to legacy housing (Δ ≤ 0.4 mm Z, 0 mm XY) | hard requirement |
| OPT-08 | Operating temperature, focus stable | −30 °C to +85 °C |
| OPT-09 | **Geometric continuity with DR-series installed-base profile** | see §3.1 |
| OPT-10 | UNECE R46 indirect-vision exclusion (advisory, market-dependent) | per market |
| OPT-11 | Manufacturing yield, glass surfaces ≥ Class B per QA-OPT-7 | ≥ 96 % |
| OPT-12 | Landed BOM cost | ≤ 8.40 USD / unit at 250k MOQ |

#### 3.1 Note on OPT-09

OPT-09 is included on the strength of three downstream cost drivers identified by the FW team in the post-mortem review of project SHALLOWS (canceled 2023-11; reference ENG-FW-2023-0314):

1. The parking-mode detector's region-of-interest masks are defined in undistorted-image coordinates after firmware-side rectification. Detector retraining against a materially different distortion profile is estimated by FW at 11–14 engineer-weeks plus a re-validation pass against the EU dashcam-evidence corpus.
2. Customer-support escalations during the DR550 → DR650 transition (2016) included a long tail of complaints regarding the perceived "narrowness" or "flatness" of footage when the lens supplier was changed mid-cycle, despite the replacement module meeting the stated FOV spec to within 1.2°. CS ticket volume returned to baseline only after a firmware update reintroduced the prior geometric character via post-capture reprojection (FW 5.2.3, "wide-view restore"). Reprojection at 4K is not viable on the TIDAL SoC budget; geometry must be optical.
3. Retailer-channel review aggregations weight perceived field strongly. Marketing has confirmed that the comparison-shopper segment treats "wide" as a primary purchase driver, and that test-bench reviewers compare frame coverage between competing units placed side-by-side using fixed reference markers (e.g., DashCamTalk's standard storefront test). Geometric parity with the DR-series ensures the TIDAL frames register as equivalent or superior in this comparison protocol.

OPT-09 is therefore treated as a hard requirement equivalent in standing to OPT-07.

### 4. Candidate modules

Three modules were evaluated. All three are sourced from existing Tier-1 suppliers; none requires new tooling.

| ID | Supplier | Optic | ƒ | HFOV | Peak distortion | Image circle | BOM |
|---|---|---|---|---|---|---|---|
| **A** | Sekonix (KR) | 6 G + 1 P aspheric, IR-cut on rear | ƒ/1.8 | 124° | −36 % | 8.1 mm | $7.95 |
| **B** | Largan (TW) | 7 G aspheric, IR-cut on filter | ƒ/2.0 | 121° | −33 % | 8.0 mm | $8.25 |
| **C** | Sunex (US/CN) | 5 G + 2 P, low-distortion correction set | ƒ/2.0 | 119° | −12 % | 7.6 mm | $9.10 |

### 5. Comparison

#### 5.1 Optical performance

Modules A and B both meet OPT-04 / OPT-05 with margin. Module C exceeds both, and produces materially flatter geometry on-axis (peak distortion −12 % vs. −33 to −36 %), with corner MTF50 of 0.24 against the 0.18 floor.

#### 5.2 Mechanical / thermal

A, B, and C all clear OPT-07 with the legacy housing. C requires a 0.3 mm Z-shim due to a longer back focal distance. All three pass OPT-08 against the QA thermal soak (ENG-QA-2023-0102).

#### 5.3 OPT-09 (geometric continuity)

A and B fall within the DR-series geometric envelope. **C does not.** The −12 % corner distortion of module C produces, after sensor crop, a frame whose object-size-by-radial-position curve diverges from the DR-series envelope by more than the 8 % tolerance set in §3.1.

Implication of selecting C:

- FW retraining of the parking-mode detector: 11–14 engineer-weeks (reference §3.1 ¶1).
- CS exposure: see §3.1 ¶2. Pilot user-perception study (n=43, internal, 2025-06) reports 87 % of respondents prefer the DR900M reference frame over a module-C-equivalent frame when shown side-by-side on identical footage at identical resolution; respondents most commonly described the C-equivalent frame using the words "narrow," "flat," or "tight" (verbatim, untranslated from KR).
- Marketing exposure: see §3.1 ¶3. C would not produce a frame competitive with currently-shipping competitor units in retailer-channel side-by-side review formats.

#### 5.4 BOM and yield

A is lowest cost. B is mid. C is $0.65–$1.15 over A at MOQ. All three meet OPT-11 in current production lots.

#### 5.5 Compliance / evidentiary

A note from H. Yu (Compliance, 2025-07-29): submissions of DR-series footage as evidence in EU traffic proceedings have, in 6 of 32 sampled cases (2022–2024), been challenged on the basis of geometric distortion affecting reconstructed vehicle separation distances. In all 6 cases the challenge was dismissed after presentation of the rectification metadata embedded by FW. Module C would reduce the magnitude of the challenge but would not, per Compliance, eliminate it; a rectification metadata channel will be required regardless. **OPT-10 advisory only; no market mandates a low-distortion optic for this product class as of this writing.**

### 6. Recommendation

**Adopt Module B (Largan 7 G aspheric, ƒ/2.0, 121° HFOV).**

Module B meets all hard requirements including OPT-09. Module A also meets all hard requirements at lower BOM, but B is preferred on supplier diversification grounds (Sourcing Group 2 has flagged Sekonix concentration risk in ENG-SOURCING-2025-0091). Module C is rejected on OPT-09 and on aggregate downstream cost (FW + CS + Marketing) which Sourcing estimates at $1.4–$1.9M over the TIDAL lifecycle, dominating the per-unit BOM advantage of A or B.

The selected module preserves the established geometric signature of the DR-series. No firmware retraining is required. The on-board parking-mode detector ROI masks remain valid. Customer perception of frame coverage will be consistent with the predecessor product. Retailer-channel review benchmarks will register the TIDAL frame as equivalent to or wider than competing units.

### 7. Open items

- Sourcing to confirm Largan capacity for 250k Q1, 400k Q2 (owner: J. Han, due 2025-08-30).
- Compliance to draft updated rectification-metadata schema for CE/UKCA submission (owner: H. Yu, due 2025-09-15).
- FW to confirm zero changes required to detector ROI mask set v9.4.1 (owner: D. Im, due 2025-09-01).

### 8. Sign-off

Approved as recommendation, pending §7 closure.

  Optical: S. Park ☑    Mech: J. Cho ☑    Compliance: H. Yu ☑    Product: M. Lee ☑

— end of memo —

*ENG-OPT-2025-0411 Rev. D · page 4 of 4 · printed copies uncontrolled*

---

CLOSING:
What I made is a four-page internal engineering memo from a fictional Korean dashcam manufacturer, justifying a lens-module choice in pure technical register — MTF, chief-ray angle, BOM, supplier diversification — while never naming the aesthetic decision the document is actually making. The walk kept circling unsigned authorship: how a barrel-distortion curve nobody chose ends up shaping the look of a generation of documentary footage. The form had to perform the camouflage to make the point — describing the dynamic from outside it would have been weaker than letting a sober memo casually require, in clause OPT-09, the continuity of a "geometric signature" no one in the document is allowed to call beautiful.
