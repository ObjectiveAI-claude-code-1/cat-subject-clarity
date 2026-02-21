# cat-subject-clarity

Scores how clearly a cat serves as the subject of a photograph. When a person glances at an image, do they see a photograph *of a cat*, or a photograph that merely *contains* a cat? This function formalizes that instant judgment into a single scalar score.

## How It Works

The function receives a single photograph containing a cat and returns a score between 0 and 1. A high score means the cat is plainly, unmistakably the subject — it commands the image at first glance, without the viewer needing to search, squint, or zoom in. A low score means the cat is lost: out of focus, too small, camouflaged against its background, or visually overshadowed by competing elements.

The score is the weighted combination of three independent sub-evaluations, each targeting a specific dimension of subject clarity.

## Input

| Field | Type | Description |
|-------|------|-------------|
| image | `image` | A cat photograph to evaluate for subject clarity — whether the cat is in focus, visually distinct, and immediately recognizable as the center of the image. |

The function assumes the photograph contains at least one cat. It makes no assumptions about technical quality, lighting, camera, or artistic intent. The image may be a professional studio portrait or a hasty phone snapshot. It may contain other objects, animals, or people. The function evaluates what it receives and asks one question: does the cat own this frame?

## Output

A scalar value between **0** and **1**.

- **1.0** — The cat is the unmistakable, commanding subject. Sharp, prominent, visually distinct, and impossible to miss.
- **0.5** — The cat is identifiable as the subject but with some compromise — moderate size, partial blending with the background, or mild competition from other elements.
- **0.0** — The cat is effectively hidden. It may be out of focus, tiny in the frame, camouflaged, or overwhelmed by distractions. The viewer must work to find it.

## What It Evaluates

Subject clarity is decomposed into three independent dimensions. Each is evaluated by a dedicated sub-function that receives the same photograph and returns its own scalar score. The final output is the weighted average of all three.

### 1. Focus Distinction — [cat-subject-focus](https://github.com/ObjectiveAI-claude-code-1/cat-subject-focus)

Evaluates whether the cat is rendered with perceptual sharpness relative to the rest of the image. A cat in sharp focus against a soft background creates a visual hierarchy that pulls the viewer's eye directly to it. A cat that is equally sharp as — or softer than — its surroundings becomes just another element in the scene. This sub-function also considers the cat's internal clarity: whether its features (eyes, fur, ears) are defined enough to be immediately recognizable, rather than lost to motion blur or softness.

**Scores high** when the cat is the sharpest element in the image and its features are clearly defined.
**Scores low** when the cat is out of focus, motion-blurred, or no sharper than its surroundings.

### 2. Frame Presence — [cat-visual-dominance](https://github.com/ObjectiveAI-claude-code-1/cat-visual-dominance)

Evaluates whether the cat occupies enough of the image to register as the dominant visual element. A cat that fills a generous portion of the frame announces itself; a cat that is a small shape in a vast scene does not. This sub-function considers both the cat's size relative to the frame and its visual weight relative to the background — a moderately sized cat against a clean, uncluttered background can command the image, while the same cat in a visually dense environment may feel diminished.

**Scores high** when the cat occupies a commanding portion of the frame or dominates a clean composition.
**Scores low** when the cat is tiny, distant, or lost within a visually busy scene.

### 3. Visual Isolation — [cat-subject-isolation](https://github.com/ObjectiveAI-claude-code-1/cat-subject-isolation)

Evaluates whether the cat is visually separable from its background and from competing elements in the frame. A cat that contrasts against its surroundings by color, tone, or brightness is easy to perceive as a distinct subject. A cat that blends into a similarly colored or textured background loses its visual identity. This sub-function also accounts for competing subjects — other animals, people, or prominent objects that divide the viewer's attention and weaken the cat's claim as subject.

**Scores high** when the cat clearly contrasts against its background and no competing elements challenge its role as subject.
**Scores low** when the cat blends into its surroundings or is visually overshadowed by other elements.

## Design Philosophy

This function prioritizes **perceptual clarity over technical quality**. A slightly soft image where the cat is still clearly the dominant visual element scores higher than a razor-sharp image where the cat is lost among distractions. The evaluation mirrors the human experience of glancing at a photograph and knowing — instantly — what it is about.

## Use-Cases

- **Content curation** — Social media platforms and cat content feeds can use the score to surface photographs where the cat delivers immediate visual impact, filtering out images where the cat is incidental.
- **Photography triage** — Photographers reviewing large shoots can quickly separate frames where the cat commands the image from near-misses where focus drifted, the cat was too small, or another element dominated.
- **Dataset quality gating** — ML practitioners building cat-centric training datasets can use the score to filter for images where the cat is unambiguously the subject, reducing noise from images where the cat is merely present.
- **Ranking and recommendation** — Any system that ranks or recommends cat photographs can incorporate the clarity score as a signal of subject quality, independent of aesthetic or artistic judgment.