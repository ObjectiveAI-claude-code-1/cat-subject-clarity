# cat-subject-clarity

Scores how well a cat serves as the clear, undeniable subject of a photograph. Evaluates three dimensions — focus clarity, subject prominence, and visual separation — to determine whether the cat commands the image instantly or is lost to blur, small size, camouflage, or competing elements. Returns a scalar between 0 and 1.

## Purpose

Not all photographs that contain cats are photographs *of* cats. A cat may appear in the distant background of a landscape, curl into a dark corner of a cluttered room, or share the frame with a dozen other animals. In each case, a cat is technically present — but the photograph does not belong to it.

`cat-subject-clarity` draws the line. It answers one question: **Does the cat own this image?**

This is not a judgment of photographic merit, artistic composition, or technical quality. It is a perceptual evaluation — an attempt to replicate the instant, instinctive impression a human viewer forms in the first fraction of a second: *Is the cat plainly, unmistakably there?*

## Input

| Field | Type | Description |
|-------|------|-------------|
| *(root)* | `image` | A cat photograph to evaluate for subject clarity — whether the cat is in focus, visually distinct, and immediately recognizable as the center of the image. |

The function accepts a single image from any source: a professional portrait, a phone snapshot, a video frame, or a social media upload. The photograph may vary in resolution, lighting, color palette, and environment. What matters is not the technical properties of the image, but how clearly the cat asserts itself as the subject within it.

## Output

A scalar score between **0** and **1**.

| Score Range | Interpretation |
|-------------|----------------|
| **0.8 – 1.0** | The cat is plainly, unmistakably the subject. Sharp, prominent, and visually dominant — the cat commands the photograph instantly. |
| **0.5 – 0.8** | The cat is recognizable as the subject but with some weakness — mild softness, moderate size, or partial visual competition from other elements. |
| **0.2 – 0.5** | The cat is present but struggles to assert itself. It may be small, partially blurred, blending into the background, or sharing attention with competing elements. |
| **0.0 – 0.2** | The cat is nearly lost. It may be a tiny speck in the frame, severely out of focus, camouflaged against the background, or completely overshadowed by other visual elements. |

## Evaluation Dimensions

The final score is a weighted combination of three independent sub-evaluations, each targeting a specific dimension of subject clarity.

### 1. Focus Clarity — [cat-focus-clarity](https://github.com/ObjectiveAI-claude-code-1/cat-focus-clarity)

Evaluates how sharply and crisply the cat is rendered *relative to the rest of the image*. This is a measure of relative focus, not absolute resolution. A photograph from a modest camera can score highly if the cat is the sharpest thing in the frame; a high-resolution image can score poorly if the cat is out of focus while the background is tack-sharp.

**What it looks for:**
- The texture of the cat's fur, facial details, and body edges rendered with more precision than surrounding elements
- The cat functioning as the perceptual anchor — the element the lens chose to render most clearly
- Whether the cat emerges from the image through sharpness, or recedes into it through blur

### 2. Subject Prominence — [cat-frame-prominence](https://github.com/ObjectiveAI-claude-code-1/cat-frame-prominence)

Evaluates how much visual real estate and commanding presence the cat holds within the frame. The cat should feel like the reason the photograph was taken.

**What it looks for:**
- The cat's size relative to the overall frame — generous and substantial, or tiny and dwarfed
- Positioning with intention — centered or placed where the eye naturally falls, versus tucked into a corner
- Visual weight relative to context — a cat against a simple background can feel prominent at smaller sizes, while a cat in a busy environment needs greater size to avoid being swallowed by visual noise

### 3. Visual Separation — [cat-figure-ground-separation](https://github.com/ObjectiveAI-claude-code-1/cat-figure-ground-separation)

Evaluates how distinctly the cat stands apart from its surroundings and from competing visual elements. This operates on two levels:

**Level 1 — Separation from background:**
- Does the cat contrast with its environment through color, brightness, or texture?
- Or does it blend, camouflage, or merge — like a black cat on a black couch, or a white cat against snow?

**Level 2 — Separation from competing elements:**
- Are there other animals, people, bold objects, or dramatic scenery pulling the viewer's eye away?
- Is the cat the singular focal point, or must it share attention?

## Use Cases

- **Cat photography platforms** — Surface the most compelling images where the cat is genuinely the star, ensuring community feeds showcase cats rather than incidental background appearances.
- **Machine learning dataset curation** — Filter training data to retain only images where the cat is unambiguously the subject, improving model quality by excluding noisy, unclear, or cat-as-afterthought images.
- **Personal photo selection** — Help users find the best, clearest portraits of their cat from a library of thousands — not blurry accidents or shots where only a tail is visible at the edge of the frame.
- **Editorial and commercial use** — Assist publishers, brands, and animal shelters in selecting images where the cat commands attention instantly — critical when the viewer's attention is fleeting and the photograph has only a moment to make its case.

## Philosophy

Technical resolution and sharpness are secondary to perceptual clarity. A slightly soft image where the cat is still clearly the dominant visual element should score higher than a razor-sharp image where the cat is lost among distractions. This function is not a measure of camera quality or photographic technique — it is a measure of whether, at first glance, the cat is the undeniable subject of the photograph.

*The cat should never have to compete for its own photograph.*