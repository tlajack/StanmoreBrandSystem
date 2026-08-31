# Stanmore Brand Standards — Review

**Document:** `Stanmore Brand Standards.dc.html` (Rev. A — August 2026, work in progress)
**Reviewed:** August 14, 2026

The document is in strong shape overall — the visual system is confident, the writing is unusually practical for a brand guide (rules a print vendor can actually act on), and the section structure is right. What follows are the areas to refine, ordered by how much they matter.

## 1. The document breaks its own rules

- **The glow on the mark.** The cover, the “Primary” card, and the tagline lockup all apply a CSS white glow (`filter:drop-shadow(0 0 10px rgba(255,255,255,0.4))`) to make the mark read on black — but Misuse rule 4 says “Never add drop shadows, bevels, outlines or outer glows.” A standards doc can’t demo an effect it forbids. The underlying problem is that the outlined mark’s black keyline vanishes on near-black, so the glow is compensating. Either show the boxed version on dark grounds, or cut a true reverse asset with a white keyline, and drop the glow entirely.
- **The tagline spacing rule isn’t followed by the doc’s own lockup.** Section 01 says the tagline sits “one clear-space unit below” the mark (¼ box height ≈ 35px at cover scale), but the cover renders it with a 2px gap, nearly touching the wordmark. Either the rule or the artwork is wrong — pick one.
- **Type on the dots.** The flyer example says “Type never sits on the dots,” but the booth-panel mock directly above it sets the tagline on the halftone texture. Either move the tagline onto a clean chip in that mock or soften the rule to match the intent (no *body* type on dense dots).

## 2. Internal contradictions and factual slips

- **“Three one-colour versions” but only two are shown** (intro to Section 01 vs. the Black/White pair). The third — red — is presented later as *not approved*. Change the count or the framing.
- **Section 07 says the business card “front carries the mark alone,”** but Section 06 (and the actual proof) show the front carrying the partner-logo row on a white strip. One of these needs to change.
- **Ontario vs. Saskatchewan.** The cover and typography specimen say Ontario, but the business card proof shows a Saskatoon branch address with (306) numbers. If Stanmore operates in both, the “across Ontario” copy is wrong; if the proof is a placeholder, it will confuse staff who treat proofs as canonical.
- **Phone formatting drifts:** “1 855-955-LIFT” on the cover vs. “1 855 955-LIFT” in the decal artwork. Pick one format and state it — this is exactly the kind of thing a standards doc exists to settle.
- **“Below the minimum, drop the black keyline”** (Section 02) reads literally as “when you’re using it smaller than the minimum,” which shouldn’t happen. You mean “at or near the minimum sizes.” Reword.
- **“Roughly one third of the wordmark’s cap height”** for the tagline — “roughly” doesn’t belong in a spec a vendor has to hit. Give an exact ratio.

## 3. The colour spec has a real screen/print mismatch

- **#ED1C24 is not PMS 485 C.** Pantone 485 C is ≈ #DA291C — noticeably deeper and more orange than the hex specified on screen and inside the SVG artwork. #ED1C24 sits closer to 185 C / Red 032. Since the doc (rightly) says red is the one colour worth a press check, decide which is the master: if 485 is the established fleet colour, the digital hex should move toward #DA291C; if #ED1C24 is the master, the spot callout should change. Right now a vendor matching 485 and a designer matching the hex will produce two different reds — the exact failure the “same red on the card and the truck door” note warns against.
- **Steel and Fog have no print values.** They’re specified for “secondary type, rules, panels, table fills” — i.e., printed things — but the production table only covers red, black and white. Add CMYK (and uncoated variants) for the neutrals, and consider an “uncoated stock” column generally: letterhead usually runs uncoated and 485 shifts a lot between C and U.
- **Verify the vinyl series.** 3M 3630 is a *translucent* film made for backlit signage; for vehicle and equipment decals the opaque cast films (e.g., 3M 180mC / 7125 series) are the usual spec. If the 3630 numbers came from a sign vendor doing backlit work, they shouldn’t be the blanket “cut vinyl” spec for the fleet. Worth one phone call before this goes final.
- **Specify how the halftone prints.** The doc simulates it at 85% opacity multiply; the production note should say whether the dots print as solid 100K over the red or as a tint, so two vendors don’t interpret it differently.

## 4. Weak diagrams where the standards need to be most precise

- **The clear-space diagram shows no clear space.** The dashed red box sits tight against the mark, and the ¼-box-height unit is never drawn or labeled. This is the single most-referenced diagram in any brand guide — it needs the mark inset within the exclusion zone with the unit dimension marked (the classic “x” construction).
- **Clear space is defined off “box height,” but two of the three lockups have no box** (the unboxed primary and the stacked decal). Define the unit from something all versions share — cap height of the wordmark, for instance.
- **Misuse is text-only.** Eight “never” rules with no visual examples except the all-red mark. Small do-not thumbnails (stretched, recoloured, on-red, glowing…) catch far more real-world abuse than prose.
- **The retired mark is never shown.** The intro says the previous unboxed wordmark stays in circulation until replaced — but staff can’t police that without seeing it. One small “this is the old mark; do not order new material with it” figure would close the loop. It’s also ambiguous because the *new* system includes an unboxed version too, so “unboxed” doesn’t distinguish old from new.
- **“Primary” is only shown on flat black,** while its stated use case is “over photography and busy edges.” Show it doing the job it’s required for — equipment photography exists in the reference folder.

## 5. Asset-package hygiene (this will bite vendors)

- `stanmore-hor-2026-black.svg` and `stanmore-hor-2026-primary.svg` are **byte-identical files**, and the one named “black” is actually the white-filled outline artwork used on dark grounds. The doc’s own vendor checklist insists on using supplied vectors — so the file names need to match the roles the doc uses (“primary,” “reverse,” etc.), with the duplicate removed.
- **Both red SVGs (`-red`, `-oneColor-red`) are filled with pure #FF0000,** not brand #ED1C24. One of them is shown in the guide as the not-approved mark; consider not shipping unapproved artwork in the package at all — its existence invites use.
- `stanmore-hor-2026.svg` still contains a **layer literally named `bleed`** — an 18-unit stroke rect clipped in half by the viewBox to form the keyline. It renders fine in Chrome, but clipped-stroke geometry is exactly the kind of thing that shifts when a vendor opens it in Illustrator or converts to PDF. The keyline should be real filled geometry.
- A one-page **asset inventory table** (file name → version → where it’s used) would tie the package to the guide and largely neutralize the naming confusion above.

## 6. Smaller polish

- **Straight apostrophes throughout:** every “Lifting You Since '62” uses `'` where it should be a typographic `’62` — including the vendor-checklist line that *defines* how the tagline must be typed.
- **No `<title>`** in the helmet — the tab just shows the file path.
- The **Contents band relies on a `style-hover` attribute** while the global stylesheet’s `a:hover` turns links dark red — on the red band that’s near-invisible. If `style-hover` is a supported DC feature this is moot; if not, the hover state is broken.
- Two inline styles use **camelCase `clipPath`** (the angled-cut swatch) where everything else is kebab-case. The DC renderer handles it, but raw HTML wouldn’t — worth normalizing.
- **Scope statement:** the doc covers print, decals and trade show only. A single line saying where digital/web standards live (or that they’re forthcoming) would stop people from improvising from this doc.

---

**Top three if you only do three:** resolve the red (485 vs. #ED1C24) before anything gets printed, kill the glow and fix the dark-ground logo strategy, and rebuild the clear-space diagram so it actually shows the unit.
