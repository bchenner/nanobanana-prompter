---
name: nanobanana-prompter
description: Generate image prompts for AI image generation (Gemini via the Nanobanana API) — realistic UGC, commercial and lo-fi content. Three modes — plain text, JSON (compact and full analytical), and modification mode for image deltas — plus character reference sheets, image-to-JSON reverse engineering, and setting swaps. Use when the user wants an image prompt written or refined, a scene reverse-engineered into a prompt, or an avatar placed into a new setting.
---

# Image Prompt Architect

Generate image prompts for AI image generation (Gemini via the Nanobanana API). Two modes: **plain text** for simplicity, **JSON** for detail and consistency.

## Reference Files

- `reference/prompt-examples.md` — Full prompt example library with compact and full analytical examples. **Read this file before every prompt generation** to match structure, tone, and level of detail.

**Before generating any prompt**: Read `reference/prompt-examples.md` for the closest matching use case. Match the level of detail and conversational tone from the examples — do not over-engineer beyond what the examples demonstrate.

---

## Core Principles

These rules override everything else. If a field reference or example contradicts these, follow these.

### Default outputCount = 4 for image gens <!-- date: 2026-05-04 -->

Every image generation should produce **4 candidates by default** — the user picks the best of the batch. Request 4 outputs on every generation (`outputCount: 4` where the API supports it); never default to 1.

### No animals in distant background of image gen prompts <!-- date: 2026-05-04 -->

Cattle, horses, livestock, birds, flocks etc. **glitch in Veo's frame interpolation downstream** — a static-looking herd in a NanoBanana still becomes warped, multi-headed, or melting once Veo animates from it. Strip animals from setting backgrounds in any image prompt that will feed a Veo3 clip. Humans and vehicles are fine. If the script dialogue mentions livestock, keep the reference in audio only — do NOT show it in the visual.

### Templates can be `{scene}` alone (no universal anchor text) <!-- date: 2026-05-04 -->

When using a template + per-scene injection pattern for image gens, **keep the template minimal — `{scene}` alone is fine**. Putting universal anchor text (generic setting descriptions, "a UGC selfie of a woman in a kitchen", boilerplate composition language) into the template *dilutes the avatar reference adherence on Nanobanana*. All per-scene specifics — subject action, environment, composition, wardrobe, props — go in the per-scene payload. The template just carries the placeholder.

Caught 2026-05-04: universal-anchor templates mentioning generic supermarket / kitchen / cafe settings collapsed avatar identity adherence and bled their generic settings into outputs even when the dynamic carried completely different scenes.

### No hyphens in image prompts

Project-wide rule: **never use hyphens** in NanoBanana prompt bodies, exclusion lists, or any field. Use spaced or unhyphenated alternatives ("close up" not "close-up", "three quarter view" not "three-quarter view", "wide angle" not "wide-angle"). Applies to the positive prompt, the `--no` list, and every nested field in the JSON.

### Text in generated images — SPLIT rule (updated 2026-06-22)

**Foreground held-product label = still low priority.** Don't burn cycles fixing the text on a product the avatar HOLDS — it gets composited in post. Identity / composition / wardrobe / pose / setting carry the image.

**Background garbled text AND background faces = a HARD AI TELL (reversed 2026-06-22).** Glyph-shaped-NONSENSE text on BACKGROUND shelf labels, book spines, signage, AND melted/uncanny FACES inside background framed photos / posters / screens are among the STRONGEST giveaways an image is AI — proven the single decisive MISSED tell on 3 of 4 realism-sweep candidates that wrongly passed. These are NOT low priority; they FAIL realism. So:
- **At prompt time:** avoid text-heavy and framed-photo-heavy backgrounds, or keep them genuinely out of focus / sparse / turned away (a plain wall or a shelf of unlabeled/turned items beats a wall of fake-label products and family photos).
- **At review time:** zoom the background and REJECT garbled background text or melted background faces. Reject only glyph-shaped-NONSENSE text / malformed faces — NOT text merely too small or blurry to read (real shelves have those too).

### Write Like a Person, Not a Spec Sheet

Prompts are creative briefs, not technical documentation. The model responds better to conversational language than camera specs.

**Do this:**
> "iPhone camera propped on a bathroom counter, good quality but not professional"

**Not this:**
> "iPhone 15 Pro rear camera, 26mm f/1.78 lens, 4K 30fps video frame, sensor noise in shadows, milky blacks"

### Describe Action, Not Appearance

Tell the model what the subject is *doing*, not how attractive they are. Give the model a character to play.

**Do this:**
> "playfully biting the straw of an iced green drink, nose scrunched"
> "half-sitting half-standing, flicking hair back with one hand"
> "mid-sentence, slight head tilt, explaining something"

**Not this:**
> "beautiful young woman posing with a calm yet playful smile"
> "standing gracefully with a serene expression"

### Tell the Model What It ISN'T

Negative boundaries are powerful for steering away from AI look:
- "NOT professional lighting"
- "not a studio, not luxury"
- "not over-processed, not airbrushed"

### Let Imperfections Happen

Don't describe perfect features. Describe clothing fit, fabric behavior, hair movement, body action — the model adds natural imperfections on its own. Over-describing skin texture region-by-region ("clearly visible pores across nose, cheeks, and chin") still backfires into uncanny territory — but a SHORT natural-texture line is now mandatory per the Skin Finish rule below. <!-- updated 2026-06-12: the old "never mention skin texture" reading is superseded — one brief texture line is required; the ban is on multi-region cataloguing -->

### Skin finish: mandatory natural-texture line on every realistic avatar prompt <!-- date: 2026-06-12 -->

Beauty-filter-smooth skin rendering is an AI tell — caught in a benchmark comparison against 1M-view reels reading as 100% real footage while our generated avatars rendered filter-smooth.

**Every realistic avatar prompt must include ONE short natural skin texture line:**
> "skin shows pores, fine lines, and slightly uneven tone across cheeks and forehead, matte but not airbrushed, a slight oil sheen on the nose, minor facial asymmetry, not retouched, no beauty filter"

<!-- tightened 2026-06-12 after the benchmark test pass: the earlier "visible pores, slight shine" wording still left airbrush-smooth patches on upper cheeks/forehead. Naming the regions (cheeks, forehead, nose) kills the smooth patches without cataloguing blemishes per zone. -->

**Rules:**
- ONE sentence, not a region-by-region catalogue (the Let Imperfections Happen caution still holds — don't list blemishes per face zone; naming the broad regions in the texture line above is fine, listing defects per zone is not)
- Add anti-smoothing terms to the `--no` / exclusion list: `airbrushed skin, beauty filter, retouched skin, porcelain skin, flawless skin, smoothed skin`
- Applies to REALISTIC workflows only — animation/cartoon styles are exempt (this playbook is realistic-only)
- This does NOT override `face.preserve_original: true` / the character reference — identity still comes from the ref sheet; the texture line governs the FINISH, not the features

### Prop scale: real-world scale is the DEFAULT <!-- date: 2026-06-12 -->

Demo props default to **real-world scale, handled naturally in the avatar's hands** — squeeze, pour, stir, with correct object physics (gripped not floating, liquid connects, plausible weight). The benchmark 1M-view video carries its entire visual interest through real-scale objects manipulated on camera; surreal-scale defaults (giant lungs, skin sheets front-center) code AI instantly when used where a real object should be.

**Surreal / giant-scale props are NOT banned** — giant organ pours and similar are proven viral formats. But they are a **deliberate format choice that must be flagged in the brief**, never a default you reach for. If the brief doesn't explicitly call for surreal scale, render the prop at real scale.

### Narrative Clutter = Realism

Small imperfect details signal "real" to the model:
- Hair tie on wrist, coffee ring stain on table, phone face-down on cushion
- Condensation on a bottle, scuffed shoes, a pen left on a notebook
- Masking tape on a skateboard, a crumpled receipt, a half-empty water glass

These are more powerful than any technical camera setting for making images look authentic.

### Framing variability — scene-dependent, dynamic, no contradictions <!-- date: 2026-06-25 -->

Don't shoot every scene as the same eye-level, one-arm-length selfie. Framing is **scene-dependent** — compose interesting shots with dynamic poses (vary camera angle, distance, and the avatar's positioning: lean-in, crouch, seated, turning to a prop) so a multi-scene video isn't one frozen locked-off shot. **Hard constraint: no contradictory framing — everything must fit on screen and the shot type must agree with what's shown vs. hidden.** The classic contradiction: cropping the face OUT while calling it a wide or medium shot — a faceless symptom/body shot must be a TIGHT crop, never wide/medium. Keep angle + distance + crop + the in/out-of-frame element list describing ONE physically possible frame.

### Anchor the Hands

Always give hands something to interact with — a surface, a prop, a body part:
- "hand resting on thigh", "fingers wrapped around coffee mug"
- "one hand on phone, other resting on counter"
- "head resting on hand, elbow propped on table"

Never let hands float freely. Never have hands clasped or interlocking (AI can't render this).

### Plain Fabrics Win

"No overt patterns" on clothing reduces AI rendering errors. Plain, solid-color fabrics render more convincingly than complex patterns, plaids, or prints. When in doubt, keep it simple.

### Lighting Must Be Pattern-Matchable

The model renders realistic lighting when it can pattern-match to real photos of that environment. Two approaches:

**Natural light** (always works): "soft natural daylight", "natural window light", "dim directional daylight entering from the left". The model has seen millions of real photos lit by windows and sunlight.

**Artificial light** (must be specific): Name the fixture placement + color temperature so the model can recall real photos with that lighting. "Overhead diffused light, neutral white" (retail store), "overhead diffused light, neutral white leaning slightly warm" (home studio). Never just "warm room light" — too vague, defaults to golden AI glow.

**Avoid**:
- Studio language: "key light", "fill light", "rim light", "bounce", "falloff" — even conversationally, these push toward professional setups
- Describing shadows or light ratios: "shadows on the right side of her face", "background darker than subject"
- Stacking "warm" across multiple fields (lighting + atmosphere + background) — if warmth is needed, put it in ONE place with restraint

**Flat neutral lighting is the DEFAULT for realistic workflows** <!-- date: 2026-06-12 -->. State it in POSITIVE language ("flat neutral white indoor light", "soft window daylight, slightly overexposed whites", "no color grade, iPhone on a tripod look"). Warm / golden / lamp-lit / moody / evening-glow lighting is banned as a default and allowed only when the user explicitly requests it. The brief's banned-phrase list (extended 2026-06-12 with `warm lamp light`, `golden glow`, `moody lighting`, `dramatic lighting`, `evening glow`, `candlelit`, `glowing moon`, `dark void background`) applies to every field of every prompt. This coexists with the Mixed Sources rule below: name two mismatched sources for realism, but the overall read must stay flat neutral white — never a warm/moody dominant grade.

### UGC Lighting: Always Use Mixed Sources <!-- date: 2026-04 -->

Single-source lighting is an AI tell. Real indoor spaces have MULTIPLE mismatched light sources — overhead fixtures plus window, lamp plus ceiling light, etc. The color temperature mismatch between sources is what makes lighting look real.

**For any UGC/indoor scene, ALWAYS describe at least 2 light sources:**

**Do this:**
> "Overhead kitchen ceiling light (cool white LED) plus natural daylight from the window on the left. The two sources create uneven illumination — left side of face brighter from the window, right side flatter from the overhead. Window in background slightly overexposed, clipped to white. Not color corrected."

**Not this:**
> "Warm, golden, soft natural window light from the left"

**The key UGC lighting cues:**
- **Mixed color temperatures**: Name two sources with different warmth (cool overhead + warm window, or warm lamp + cool daylight)
- **Uneven illumination**: One side of the face/body noticeably brighter than the other
- **Avoid VISIBLE windows in the background** <!-- date: 2026-06-22, user verifier --> — a window in frame (especially the blown to white rectangle AI loves to render) is a dead giveaway it is AI. Place the subject against a wall, shelf, headboard, doorway, or curtain instead. Window LIGHT is still good (daylight coming from an OFF frame window), but the window itself should NOT be in the shot. This OVERRIDES the older "overexposed window" cue.
- **Not color corrected**: Explicitly say "not color graded" or "auto white balance slightly off." Real phone videos have a mild color cast from mixed sources (yellow-green, blue-warm, etc.)
- **Unflattering overhead light**: Real kitchens, bathrooms, and offices have overhead lighting that creates shadows under eyes and chin. Don't fight this — it's what real looks like

**Never use a single perfect light source for UGC.** "Natural window light from the left" produces a perfectly lit portrait that screams AI. Real rooms have ugly mixed lighting. Embrace it.

### UGC Camera: Imperfect Framing Is Mandatory <!-- date: 2026-04 -->

Perfectly centered, perfectly level compositions are an AI tell. Real phone videos are propped up quickly, slightly crooked, slightly off-center.

**For any UGC/selfie/propped-phone scene, ALWAYS include these camera cues:**

**Framing:**
- Subject shifted slightly off-center (left or right of center, not dead center)
- Tight and slightly cramped — "the framing feels like someone quickly propped their phone and hit record"
- Part of an elbow or hand slightly cropped at the frame edge
- NOT perfectly composed, NOT symmetrical

**Angle:**
- Phone propped at a slightly imperfect angle — "tilted about 2 degrees" or "not perfectly level"
- Describe HOW the phone is propped: "leaning against a jar on the counter", "propped against a stack of books"

**Lens:**
- "Wide smartphone lens with slight barrel distortion at the frame edges"
- This is the single strongest anti-AI cue for composition — real phone cameras have visible wide-angle warping

**Smartphone artifacts (add to composition or as a separate field):**
- "Visible digital noise and grain in shadow areas"
- "Compressed dynamic range — bright areas clip to white" (do NOT stage a visible window to get this; keep windows off frame per the no visible windows rule above)
- "Auto white balance slightly off from mixed lighting sources"
- "Not color graded, not post-processed"

**Add to --no for every UGC prompt:**
> perfectly centered composition, symmetrical framing, even lighting, color corrected, golden hour, warm glow, studio softbox, ring light, fashion photography, editorial, magazine, visible window, window in background, blown out window

---

## AI Look Anti-Patterns

These make images look generated. Avoid them in all prompts.

| Anti-Pattern | Why It Fails |
|-------------|-------------|
| Beauty descriptors ("beautiful", "stunning", "porcelain", "flawless") | Pushes model toward smooth, textureless AI skin |
| Generic pose words ("posing elegantly", "standing gracefully") | Produces stiff, symmetric, obviously-AI poses |
| Skin PERFECTION descriptors ("porcelain-white skin", "smooth complexion") | Forces unnatural beauty-filter smoothness — an AI tell. Note: a short natural-TEXTURE line (pores, slight shine, asymmetry) is required, not banned — see the Skin Finish core principle <!-- updated 2026-06-12 --> |
| Technical camera specs (f-stops, focal lengths, aperture values) | Model doesn't understand these — they add noise without improving output |
| Detailed lighting diagrams (key/fill/rim with angles and color temps) | Over-constrains the model. "Warm light from the left" works better than a 4-paragraph lighting setup |
| Hex color palettes (#E0C8B8, #3B2E2A) | Model doesn't reliably interpret hex codes. Use plain color words |
| Over-detailed micro_details on every object | Diminishing returns. Reserve micro_details for the 1-2 most important items |
| `negative_prompt` JSON blocks with 10+ forbidden elements | A few key `--no` items work. Long forbidden lists add noise |
| Subject not interacting with environment | Person feels pasted in. They should be *doing something* in the space |
| **Single perfect light source** ("warm golden window light") | Real rooms have mixed, mismatched sources. Single sources produce perfectly lit portraits that scream AI |
| **Perfectly centered subject** | Real phone videos are quickly framed. Dead-center = obviously composed = AI |
| **Symmetrical composition** | Real phone photos have one elbow cropped, tilted horizon, cramped framing. Symmetry = studio |
| **"Golden hour" / "warm glow"** | The #1 most overused AI lighting cliché. Real indoor content has ugly overhead LED + window |
| **Even illumination across the face** | Real mixed lighting creates one side brighter than the other. Even = studio softbox = AI |
| **Visible window in the background** <!-- date: 2026-06-22, user verifier --> | A window in frame (and the blown to white rectangle AI renders) is a dead giveaway it is AI. Put the subject against a wall / shelf / doorway and keep the window OFF frame. (Reverses the older "clip windows to white" cue.) |
| **"Golden hour" / cinematic outdoor light** | AI overcooks outdoor scenes into postcard / travel brochure lighting. Real outdoor phone video is flat, harsh, sometimes overcast, unflattering. (Outdoor scenario, see Scenario realism below) |

---

### Scenario realism + the skin spectrum — be well rounded, not just gritty <!-- date: 2026-06-22, user verifier -->

Realism is NOT the same as "messy." The recipe must handle the full spectrum of real photos, from a blemished amateur selfie to a good looking person with clear skin — both can read 100 percent real, and both can read AI if done wrong. Pick the point on the spectrum the brief calls for; never default to airbrush smooth, and never assume "more blemishes equals more real."

**Skin spectrum (two valid realistic looks):**
- **Gritty real** (default for raw UGC): visible blemishes, redness, uneven tone, oil sheen, texture. For relatable amateur creators.
- **Clean real** ("perfect" skin that is still real): clear, even, good skin WITH real micro detail kept — fine visible pores across the nose and cheeks, natural specular highlights, faint fine lines, slight asymmetry, real skin translucency. NO blemish cataloguing, but also NO beauty filter / airbrush / wax / porcelain. The tell that separates clean real from AI is PORES plus real light falloff, not blemishes. Keep the anti smoothing terms in --no.
- Whichever point you pick, keep framing logic correct (the framing_directive) and keep the rest of the realism stack (flat neutral light, no visible window, candid pose, narrative clutter sized to the scene).

**Authentic background beats staged set** (iter-02 win, 2026-06-22): a real, crammed, slightly disorganized background (a packed product shelf, a lived in room) reads more real than a tidy, sparse, styled set. Clutter should look accumulated, not arranged.

**Subject attractiveness + elevated wardrobe (default direction)** <!-- date: 2026-06-22, user -->: the default generated person should be **naturally good looking and well dressed** — but the realism stack stays fully RAW; attractiveness is the ONLY knob that moves, never trade realism for polish.
- **Attractive WITHOUT the beauty-descriptor trap**: achieve it through FEATURES + GROOMING + STYLING, never adjectives. Do NOT write "beautiful / stunning / gorgeous / flawless" (they force the smooth airbrushed AI skin — the #1 tell; see AI Look Anti-Patterns). Instead: good bone structure, well groomed hair, tasteful light makeup where it fits, a fit healthy build, a flattering candid angle. Skin stays REAL (clean-real spectrum: pores, slight texture, real specular, slight asymmetry, no airbrush).
- **Elevated wardrobe**: a step up from the default plain heather tee — stylish, well fitted, quality everyday pieces (a fitted ribbed knit, a structured jacket or blazer over a plain tee, quality denim, considered colors). Still PLAIN / solid fabrics (the Plain Fabrics Win rule holds — no busy patterns), worn naturally on a real body, NOT a styled fashion shoot.
- **Everything else stays raw**: flat neutral indoor light, candid off center phone framing, lived in windowless background, real skin finish, phone-camera artifacts, narrative clutter. Net read: "an attractive, stylish real person who just filmed themselves on their phone", NOT "a model on a shoot" (the glamour/fashion/influencer look reads as AI and the realism verifier will reject it).

**Per scenario realism (filled as each is tuned in the autoresearch sweep):**
- **Indoor talking head selfie**: windowless, subject against a wall or shelf, face upper 35 to 45 percent, crammed authentic background. [tuned 2026-06-22]
- **Outdoor**: flat / harsh / overcast daylight (slightly blown pale sky), NO golden hour / cinematic / warm glow; BUSY MUNDANE real background in DEEP focus (suburban street, parked cars, chain link fence, trash bin, power lines — not a scenic vista, no bokeh); wind in hair, slight squint, candid off center selfie. [tuned 2026-06-22, 4/4]
- **Unique / exotic location**: tourist phone snap NOT a postcard — populate with mundane real clutter (other tourists, parked scooter, trash bin, chalkboard signage, power lines, AC units), flat harsh daylight + blown pale sky, DEEP focus (no bokeh), tilted horizon, person too close to the lens with the landmark awkwardly cropped behind; face stays dominant. [tuned 2026-06-22, 4/4]
- **Handheld props** (avatar holding a product): fingers WRAP and conform to the object, it rests against the palm, fingers occlude part of the label (forces correct front/behind layering), real scale relative to hand and face; product held BESIDE the face or shoulder (never a centered hero product), face stays dominant; anti studio (lived in background, flat light, a smudge or reflection on the product, partially readable label). --no claw hand, extra fingers, floating product, giant product, tiny product, centered hero product, styled product photo. [tuned 2026-06-22, grip 4/4]
- **Kitchen / recipe demo**: real lived in counter clutter (crumbs, zest, dish towel, cutting board, jars cropped at the edges), NOT a cooking show set; ONE clear hand action with correct CONTACT PHYSICS (lemon squeeze with the juice drip connecting into the glass, pour stream connecting, spoon in the mug); demo framing (face at the upper end of 18-25%, hands and ingredients in the lower frame); flat overhead light. [tuned 2026-06-22, action 4/4]
- **Prop only B-roll close-up** (NO face — use the PROP directive): hero object off center, a single hand and forearm from a frame edge OR no hand at all, real contact / water physics (splash crown, ripple, ginger sinking, juice drip connecting), casual counter clutter (smear, stray drips, pulp, containers cropped at the edges) NOT a styled food photo, deep focus, real wet textures (no 3D / CGI cleanness). [tuned 2026-06-22, 4/4; prop directive correctly produced zero person/face]
- **Older demographic (grandma / older man)**: aged skin must be STRUCTURAL, not drawn on — deep set lines BY LOCATION (forehead, crow's feet, nasolabial folds, lip lines) PLUS pigmentation (age and sun spots, uneven tone) PLUS thinning / crepey / sagging structure PLUS aged hair (gray with visible scalp and flyaways, not salon styled) PLUS aged hands (veins, prominent knuckles). Bracket it both ways: NOT a smoothed young face with gray hair added, and NOT cartoonishly over wrinkled. [tuned 2026-06-22, 4/4]
- **Male (everyday man)**: ordinary, NOT a model — uneven patchy stubble (thick chin, sparse cheeks, stray/gray hairs), visible pores plus shine plus a blemish or redness, soft rounded jaw with a slight double chin from the selfie angle, thinning or messy hair, asymmetric features. --no male model, chiseled jaw, fitness influencer, groomed beard, perfect stubble, symmetrical beard. [tuned 2026-06-22, 4/4]
- **Car selfie**: driver seat, parked — seatbelt across the chest (correct retractor geometry), headrest behind, door panel + side window + side mirror, parking lot or street visible through the glass (car windows ARE natural here — do NOT suppress them), harsh directional daylight (one side of the face brighter, side glass bright), cramped tight framing (phone close in a confined space), worn interior + clutter (phone mount, cup, cable). NOT showroom clean. [tuned 2026-06-22, 4/4]
- **Mirror selfie**: the phone is the highest garble risk — force ONE plain dark rectangle (no screen detail) in ONE naturally gripped hand, held at chest or face height; real mirror with smudges / dust / spots; lived in reflected room (unmade bed, dresser, open closet — no window); waist up is fine. --no two phones, warped phone, garbled screen, extra fingers, claw hand. [tuned 2026-06-22, 4/4]
- **Full body**: adapt the crop WIDE (head to toe) — the chest-up directive is talking-head ONLY; keep the candid / off center / phone-imperfection principles but frame the whole body. Natural everyday stance (weight on one leg, slight contrapposto, NOT a square model pose), hands SIMPLE and partly hidden (one in a pocket, the other relaxed) to cut finger garble, BOTH feet present in the SAME pair of well formed shoes, correct head to body proportions (not elongated), face correctly small but undistorted. --no elongated body, wrong proportions, oversized/tiny head, extra fingers, extra feet, melted shoes, fashion model pose, mannequin. [tuned 2026-06-22, 4/4]
- **Darker / deep skin tones**: name the WARM or neutral UNDERTONE (rich brown, NOT grey, NOT ashy, NOT desaturated), EXPOSE FOR THE FACE (phone meters for her face, detail retained, NOT left underexposed/dark/crushed), soft natural specular highlights on forehead / cheekbones / nose bridge (NOT a greasy glamour sheen, NOT a uniform plastic sheen), real varied texture (pores, unevenness, subsurface warmth). --no ashy skin, grey skin, desaturated skin, plastic skin, oily glamour sheen, uniform sheen, underexposed face, crushed shadows. [tuned 2026-06-22, 4/4]
- **Window recurrence (cross cutting, reinforce on EVERY indoor ROOM prompt)** <!-- date: 2026-06-22 --> — SCOPE: this is for indoor ROOM backgrounds (bedroom, kitchen, office). It does NOT apply to CAR selfies (car windows are natural and expected) or genuine outdoor shots. — even with the no visible windows rule, the model regrows a window ~half the time on indoor scenes, and kitchens are the STICKIEST (window over the sink is a strong prior). The rule is only ~50 percent effective from the prompt alone. So: (1) state POSITIVELY "a solid wall / packed shelf / run of cabinets directly behind the subject, no window in the frame", (2) keep the window terms in --no, AND (3) treat windowless as a CANDIDATE SELECTION gate — generate the 4 and pick a windowless one (do not rely on the prompt alone).

## Three Prompt Modes

### 1. Plain Text

Single-line prompt. Use when simplicity is key or for quick iterations.

Structure:
```
[Medium & Style] + [Subject & Action] + [Environment] + [Lighting] + [Camera] + parameters
```

**Example:**
```
Raw unedited smartphone selfie, a young person with messy hair and a tired smile wearing an old grey oversized hoodie, holding phone in one hand, looking right into the lens, cluttered living room with unmade couch, mixed natural window light, wide-angle front camera distortion --no professional camera, bokeh, makeup, 3d render --ar 9:16
```

### 2. JSON

Structured prompt for detailed, consistent outputs. **Two formats — two different paradigms:**

**Full Analytical JSON** — the default format for all image prompts. Use for everything: UGC selfies, portraits, product scenes, multi-object compositions.
```json
{
  "meta": {},
  "character_reference": {},
  "global_context": {},
  "composition": {},
  "subject": {},
  "objects": [],
  "text_ocr": {},
  "semantic_relationships": []
}
```

### 3. Modification Mode

Takes an existing base image as reference and applies a small change via plain text instruction. No JSON, no full prompt. The base image already defines the scene, subject, environment, lighting, and camera. You only describe what changed.

**When to use:**
- End frames (base = start image, instruction = what shifted)
- Product placement (base = speaking scene image + product photo, instruction = how the subject holds/interacts with the product)
- Angle variations (base = existing scene, instruction = new framing)
- Any image that is a small delta from an existing one

**Input:**
1. Base image uploaded as reference (the start frame or existing scene)
2. Optional: additional reference image (product photo, prop photo)
3. Plain text instruction describing ONLY what changed

**Examples:**
```
The speaker holds the product bottle in her right hand, resting on the desk surface.
```
```
She leans slightly forward, looking down at the open product box on the table.
```
```
Same scene but framed as a tighter close-up, chest and above.
```

**Rules:**
- Keep instructions short and specific (1-2 sentences)
- Don't re-describe the scene, subject, environment, or lighting. The base image handles all of that.
- Focus on the delta: what moved, what appeared, what changed position
- If a product photo is provided as a second reference, the model uses it for accurate product appearance
- Anchor hands to the product or a surface (same rule as always)

| Variation Type | Base Image | Additional Reference | Instruction Focus |
|---------------|------------|---------------------|-------------------|
| End frame | Start image | — | Posture shift, expression change, gesture |
| Product hold | Speaking scene image | Product photo | How subject holds/displays the product |
| Angle shift | Existing scene | — | New framing (tighter, wider, different angle) |

---

## Parameters

Parameters go at the end of plain-text prompts.

| Parameter | Values | Notes |
|-----------|--------|-------|
| `--ar` | `1:1` (default), `9:16` (vertical), `16:9` (cinematic) | Always 9:16 for TikTok/Reels |
| `--no` | comma-separated list | What to avoid: `--no professional lighting, makeup, 3d render` |
| `--s` / `--stylize` | 25-50 (strict) to 750 (artistic) | **Keep low for UGC.** High values = "art" not reality |

---

## Compact Format Guide

The compact format is conversational. Write it like you're describing the image to a friend, not filling out a database.

### `subject`
The scene description and what the person is doing. This is the most important field — get the action and energy right.

```json
{
  "description": "A young woman taking a mirror selfie, playfully biting the straw of an iced matcha latte, nose scrunched",
  "age": "young adult",
  "expression": "playful, nose scrunched, biting straw"
}
```

Optional: `"mirror_rules": "ignore mirror physics for text on clothing, display text forward and legible to viewer"` — use for mirror selfies where brand logos need to be readable.

### `face`
Keep it minimal. The reference image handles identity. Focus on makeup level and let natural texture happen on its own.

```json
{
  "preserve_original": true,
  "makeup": "natural sunkissed look, glowing skin, nude glossy lips"
}
```

**Don't** catalogue blemishes or texture region-by-region (undereye circles, per-zone pore lists) — but DO include the single mandatory natural-texture line from the Skin Finish core principle ("natural skin texture, visible pores, slight shine, minor asymmetry, not retouched, no beauty filter"). <!-- updated 2026-06-12: filter-smooth skin is an AI tell -->

### `hair`
Simple — color and style. Add movement if relevant.

```json
{
  "color": "brown",
  "style": "long straight hair falling over shoulders, a few flyaways"
}
```

### `clothing`
Plain fabrics, specific garment types. Avoid patterns.

```json
{
  "top": {
    "type": "oversized hoodie",
    "color": "light heather grey",
    "details": "soft fleece, relaxed fit, hood falling back"
  },
  "bottom": {
    "type": "denim jeans",
    "color": "light wash blue",
    "details": "relaxed fit, visible button fly"
  }
}
```

### `accessories`
Layer specific items. Trend stacking (multiple distinct accessories) makes content feel culturally current.

```json
{
  "headwear": { "type": "olive green baseball cap", "details": "white NY logo, headphones worn over the cap" },
  "jewelry": {
    "earrings": "large gold hoop earrings",
    "necklace": "thin gold chain with cross pendant",
    "wrist": "gold bangles and bracelets mixed"
  },
  "prop": { "type": "iced beverage", "details": "plastic cup with iced matcha latte and green straw" }
}
```

### `photography`
Keep it simple and conversational. 5-6 lines max. No f-stops, no focal lengths.

```json
{
  "camera_style": "smartphone mirror selfie aesthetic",
  "angle": "eye-level mirror reflection",
  "shot_type": "waist-up composition",
  "aspect_ratio": "9:16 vertical",
  "texture": "sharp focus, natural indoor lighting, social media realism, clean details"
}
```

**"Social media realism"** = bright, flattering, high-def, aspirational but attainable. It's reality with a filter.
**"Raw photorealism"** = gritty, noisy, imperfect. iPhone video frame quality.

Choose the right one for the content type. Don't default to raw for everything.

### `background`
Environment as a short list. Don't over-describe — the model fills in believably when given a setting + a few key elements.

```json
{
  "setting": "bright casual bedroom",
  "wall_color": "plain white",
  "elements": ["bed with white textured duvet", "leopard print throw pillow", "distressed white nightstand"],
  "atmosphere": "casual lifestyle, cozy, spontaneous",
  "lighting": "soft natural daylight"
}
```

---

## Full Analytical Format Guide

This is a scene graph — an object-oriented spatial description. Every element gets its own ID, attributes, and spatial position. Use this when objects need to not bleed into each other and spatial relationships are critical.

### Key Concepts

**Object ID De-entanglement**: Separate objects prevent texture/adjective bleed. "Worn" on a skateboard (obj_007) won't make the person (obj_001) look worn. This is the primary reason to use full analytical over compact.

**Semantic Relationships as Glue**: Listing objects isn't enough — define their interaction. "Subject is squatting directly over the skateboard" prevents the skateboard from floating or merging into the ground.

**Foreshortening Must Be Named**: AI struggles with extreme angles. Explicitly name perspective effects: "foreshortening", "top-down", "low-angle distortion." This guides the geometry engine.

### Fields

#### `meta`
```json
{
  "image_quality": "High",
  "image_type": "Photo",
  "aspect_ratio": "9:16"
}
```

#### `character_reference`
```json
{
  "instruction": "Use the attached reference sheet as the absolute ground truth for the subject's facial features, skin texture, and body proportions. The output must be a 1:1 match of the character provided."
}
```

#### `global_context`
Scene description + lighting. Keep lighting simple — a source, direction, and quality. No hex color temperatures.

```json
{
  "scene_description": "A candid selfie taken on an outdoor patio, subject holding a supplement bottle at shoulder height, residential house in background",
  "time_of_day": "Daytime",
  "lighting": {
    "source": "Natural sunlight",
    "direction": "Frontal, diffused",
    "quality": "Soft, even"
  }
}
```

#### `composition`
Camera angle and framing. Use plain descriptions, not lens specs.

```json
{
  "camera_angle": "Eye-level selfie",
  "framing": "Close-up, subject fills most of frame",
  "depth_of_field": "Deep — subject and immediate background in focus",
  "focal_point": "The product bottle and subject's face"
}
```

#### `subject`
Pose, clothing, and position. Same anti-patterns apply — action over appearance.

```json
{
  "pose": {
    "body_position": "Standing",
    "gesture": "Left hand holding bottle near shoulder height, right arm extended forward (selfie)",
    "head_angle": "Facing camera",
    "expression_mood": "Neutral, relaxed"
  },
  "clothing": {
    "outfit_description": "Plain white hoodie, casual loungewear",
    "colors": ["White"],
    "accessories": ["Tortoiseshell round glasses", "Multiple small gold hoop earrings"]
  },
  "position_in_frame": "Center",
  "prominence": "Foreground"
}
```

#### `objects[]`
Each object gets its own ID. Use `micro_details` only on the 1-2 most important objects (usually the product). Don't micro-detail everything.

```json
{
  "id": "obj_001",
  "label": "Supplement Bottle",
  "category": "Product",
  "location": "Mid-right, held by subject",
  "prominence": "Foreground",
  "visual_attributes": {
    "color": "Translucent cyan/blue with white cap",
    "texture": "Smooth plastic",
    "state": "New"
  },
  "micro_details": [
    "White screw-top lid with vertical ridges",
    "Label wraps around bottle",
    "Gummies visible inside through translucent plastic"
  ]
}
```

#### `text_ocr`
When brand text must appear on products. Use `mirror_rules` in compact format instead for mirror selfies.

```json
{
  "present": true,
  "content": [
    { "text": "ASHWAGANDHA", "location": "Bottle label center", "font_style": "Sans-serif uppercase bold", "legibility": "Clear" }
  ]
}
```

#### `semantic_relationships`
The spatial glue. Define how objects interact with each other and the subject. Critical for preventing floating objects and merging.

```json
[
  "Subject is holding Supplement Bottle in left hand",
  "Subject is positioned in front of Sliding Glass Door",
  "Glasses are worn on Subject's face"
]
```

---

## Character Consistency

For maintaining the same character across multiple images:

1. Add `character_reference` block to the JSON:
```json
"character_reference": {
  "instruction": "Use the attached reference sheet as the absolute ground truth for the subject's facial features, skin texture, and body proportions. The output must be a 1:1 match of the character provided."
}
```

2. Set `face.preserve_original: true` on the subject (Identity Lock Protocol)

3. The reference sheet image is attached alongside the prompt as a generation input

**Don't over-describe the face when using a reference** — the image handles identity. Focus on expression and action instead.

### Character Ref Sheets Don't Show Attire <!-- date: 2026-04 -->
Character reference sheets only capture the face, head coverings (headwrap, hat, glasses), and basic upper body. They do NOT show the full outfit, jewelry, bangles, necklaces, or any clothing detail below the shoulders. When generating scene images that use a character reference:
- **Always describe the full attire in the scene prompt** — dress/top style, color, pattern, jewelry, bracelets, accessories
- Don't assume the character ref provides wardrobe information — it only locks the face
- The scene prompt is the ONLY place the model learns what the character is wearing

### Use Reference Frames When Copying Videos <!-- date: 2026-04 -->
When replicating a scene from an existing video, you may be given an extracted frame from the original as a visual reference. When a reference frame is provided:
- Study it carefully for composition, camera angle, lighting, color palette, object placement, and framing
- Match what you SEE in the reference, not what you imagine the scene should look like
- "Make it look like THIS" is more precise than any text description — use the reference as ground truth
- Call out specific details from the reference in your prompt: "the glass is positioned in the lower-left third, slightly off-center, with the liquid at roughly 2/3 full"
- This is especially valuable for B-roll scenes (organs, recipe close-ups, 3D renders) where the composition is hard to describe in words

### Medical/Organ B-Roll Must Be Photorealistic <!-- date: 2026-04 -->
When generating medical B-roll (organs, anatomy, body parts), use photorealistic surgical/anatomy-lab quality — NOT clean 3D CGI or medical diagrams.
- Organs should look like wet, glistening real tissue with blood vessels, texture, imperfections
- Use `image_type: "Photo"` not `"3D Render"`
- `--no` block must exclude: 3D render, CGI, digital model, medical illustration, diagram, clean smooth surface, plastic
- Diseased organs: dark discoloration, fatty deposits, rough texture, nodular scarring
- Healthy organs: pink, smooth but still organic, wet sheen, visible vasculature
- This visceral realism is what stops the scroll — clean CGI organs don't trigger the same response

### Generating a Character Reference Sheet

> **Fallback only** <!-- date: 2026-04 --> — the default workflow is to **upload an existing character reference photo**. Only generate a new sheet from text when there is no photo on hand and one is explicitly asked for.

Use this plain text template to generate a new character reference sheet from scratch. Fill in the bracketed fields based on the character description.

```
A character reference sheet of a [age range] [ethnicity/background] [gender], [specific skin tone], [hair color] hair [hair style], [distinctive eyebrow description], [eye color] eyes, [face shape and defining facial features — jawline, nose, cheekbones, etc.]. Three vertically stacked photos filling the entire frame edge to edge with no gaps, no borders, no dividing lines between them. Top third: front-facing headshot, relaxed neutral expression, looking directly at camera. Middle third: three-quarter view, head turned slightly to the right. Bottom third: full side profile facing right. All three shots are shoulders-up, wearing a plain [color] [simple top — e.g. black crewneck t-shirt]. [Signature accessories — glasses, earrings, necklace, etc.]. No makeup, natural bare skin. Shot on a smartphone against a plain light grey wall, natural window light from the left, social media realism. --ar 9:16 --no borders, frames, dividing lines, white space between photos, text, labels
```

**Key rules for reference sheets:**
- **Always plain text** — this is a utility image, not a creative scene
- **Describe the face in detail** — this is the one case where face topology is correct, because there's no reference image to rely on
- **Include signature accessories** (glasses, earrings, jewelry) — these are part of the character's identity
- **Keep clothing plain and neutral** — plain black or white t-shirt, nothing distracting
- **Natural window light + smartphone** — even utility images need a real light source and camera anchor to avoid AI skin
- **Never use "flat even lighting"** — that's what AI does by default and reinforces the artificial look

---

## Image-to-JSON (Reverse Engineering)

Two methods:

### Standard Image-to-JSON
Analyze the image and produce a full analytical JSON. This is the scene graph paradigm — capture every observable element with object IDs, spatial positions, and relationships.

### Character Consistency Extraction
Extract the character's distinguishing features for reuse: face structure, skin texture, body proportions, signature accessories. Output a character reference block for future prompts.

---

## Aesthetic Modes

Different content types need different aesthetic approaches:

| Content Type | Aesthetic | Photography Texture |
|-------------|-----------|-------------------|
| UGC / TikTok / raw feel | Raw photorealism | "iPhone video frame, soft focus, video noise in shadows, slightly desaturated" |
| Lifestyle / fashion / aspirational | Social media realism | "Sharp focus, natural indoor lighting, social media realism, clean details" |
| Retro / nostalgic | Named camera aesthetic | "Canon IXUS point-and-shoot, direct flash, warm skin, dark background falloff" |
| Clean girl / viral slideshow | Curated realism | "Bright daylight, crisp details, styled but spontaneous feel" |
| **Storytelling / emotional narrative** | Lo-fi intimate | "Handheld iPhone, natural light only, no filters, no color grading, raw and unpolished" |

**Social media realism ≠ raw photorealism.** They're different aesthetics. Social media realism is bright, flattering, aspirational. Raw photorealism is gritty and imperfect. Match the aesthetic to the content goal.

### Storytelling Visual Style <!-- date: 2026-03 -->

When generating images for long-form personal storytelling scripts, use these visual rules:

**Opening frames (first 3 seconds)**:
- Full-screen close-up — eyes, skin, expression fill the frame
- Show exhaustion, dark circles, raw emotion. No makeup, no filters
- Lo-fi iPhone aesthetic: handheld, natural light, slight motion blur acceptable

**Symptom visuals**:
- Tired faces with visible dark circles
- Sitting up in bed at 3AM — dim blue-ish light, disheveled
- Sitting alone in car at night — dashboard glow, isolation
- No stock footage look, no filters, no brand overlays

**Key rules**:
- NO beauty descriptors at all — not "natural beauty" or "effortless." This is raw.
- Narrative clutter is critical — crumpled tissues, half-empty water glass, phone face-down
- Lighting must feel accidental (overhead kitchen light, bedside lamp, car dome light)
- Expression should be mid-emotion, not posed — caught crying, staring blankly, looking away

### NanoBanana Setting Swap Template <!-- date: 2026-04 -->

Master prompt for placing an existing avatar into new settings while keeping facial identity. Use when the brief asks to put an avatar in a store, kitchen, outdoor setting, or any location different from their default.

**Template:**
"Using the character from the attached image, create a detailed AI image prompt that places them in [new setting], wearing [clothing], [pose/position], with [props/objects]. Use natural iPhone photo style with [lighting]. Include specific background details and keep everything realistic with no blur. Make sure the character fills more of the frame with their torso and face occupying most of the image, while background elements remain visible but secondary. Position the camera at a comfortable height directly in front of them."

**Suggested locations for supplement content:**
- Supermarket (reviewing products on shelves)
- Drug store / pharmacy (holding up supplement bottles)
- Holistic herbs room (shelves of jars, crystals, dried herbs)
- Kitchen (baking, making tea, preparing recipes)
- Shed / garden (outdoor natural remedy setting)
- Open field (nature, walking, sunrise)

**Key rules:**
- Always use the approved avatar image as reference (character_reference block)
- The avatar must fill most of the frame — background is secondary
- Camera at comfortable height, directly in front
- Natural iPhone photo style, no blur, no studio lighting
- Include specific background details for the new setting

---

## Quality Checklist

Before delivering any prompt:

- [ ] Aspect ratio specified (default 9:16 for social)
- [ ] Subject is doing something specific — not just "standing" or "smiling"
- [ ] Hands are anchored (holding something, resting on a surface, in a pocket)
- [ ] Clothing is plain/solid colors (no complex patterns unless intentional)
- [ ] No beauty descriptors ("beautiful", "stunning", "porcelain", "flawless")
- [ ] Photography block is 5-6 lines of plain language (no f-stops, no focal lengths)
- [ ] Environment is a short list of elements, not nested object arrays
- [ ] At least 1-2 narrative clutter items for realism
- [ ] Face block is minimal — `preserve_original: true` + makeup level only
- [ ] Lighting is 1-2 sentences, not a multi-section diagram
- [ ] **UGC lighting uses 2+ mixed sources** — not a single perfect light. Include color temp mismatch and uneven illumination
- [ ] **UGC camera is off-center** — subject not dead center, phone propped imperfectly, slightly tilted
- [ ] **Wide smartphone lens distortion** mentioned in composition
- [ ] **Smartphone artifacts** included — grain in shadows, clipped highlights, auto white balance off
- [ ] **--no block includes anti-perfection terms** — perfectly centered, symmetrical, even lighting, color corrected, golden hour, studio softbox, ring light, editorial, magazine

See `reference/prompt-examples.md` for the full example library.

