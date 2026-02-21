# cat-subject-clarity

Scores how clearly a cat registers as the subject of a photograph. Returns a value from 0 to 1 reflecting whether the cat is immediately and undeniably the center of the image — without requiring the viewer to search, squint, or zoom in.

## Input

A single image (photograph) known or presumed to contain a cat. The function does not detect whether a cat is present — that is taken as given. It evaluates the perceptual clarity of that cat as the photograph's subject.

## Output

A scalar score between 0 and 1.

- **Near 1.0** — The cat is plainly, unmistakably the subject. It is in focus, prominent in the frame, and visually distinct from its surroundings. A viewer glancing at the image for a fraction of a second would immediately identify it as a picture *of* a cat.
- **Near 0.0** — The cat is difficult to find, visually subordinate, or lost in the scene. It may be out of focus, too small, camouflaged against the background, or overwhelmed by competing visual elements. The viewer must work to locate or identify the cat.

## Use Cases

- **Photo curation** — Adoption agencies, social media accounts, stock photography collections, and veterinary records all require images where the cat reads instantly. This score filters for photographs that meet that baseline.
- **Dataset quality** — Training data for cat detection or breed classification models benefits from images where the subject is cleanly presented. Scoring subject clarity allows researchers to rank, filter, and prioritize images, reducing noise in training pipelines.
- **Burst selection** — When choosing the best frame from a series of rapid-fire shots, subject clarity provides a consistent, repeatable signal for which image makes the cat pop.
- **Compositional feedback** — Photographers or automated systems can use the score to understand whether a composition succeeds at presenting the cat as the clear subject.

## What It Evaluates

The function decomposes subject clarity into three independently scored dimensions. Each sub-function receives the same cat photograph and evaluates a specific quality. The parent score is the weighted combination of all three.

### 1. Focus Distinction — [{{ .Task0 }}](https://github.com/{{ .Owner }}/{{ .Task0 }})

Evaluates how sharply the cat is rendered *relative to everything else* in the image. What matters is the gap in clarity between the cat and its surroundings — not absolute technical sharpness. A cat that is the crispest element in the frame while the background falls into softness scores highly. A cat that is equally sharp as its environment, or softer than its surroundings, scores poorly. The human eye is wired to seek out the sharpest element in a scene; this dimension measures whether the photograph leverages that instinct in the cat's favor.

### 2. Subject Prominence — [{{ .Task1 }}](https://github.com/{{ .Owner }}/{{ .Task1 }})

Evaluates how much visual weight the cat carries within the frame — its scale, placement, and the proportion of the composition it occupies. A close-up portrait where the cat fills the frame has maximum prominence. A wide landscape where the cat is a distant speck has almost none. Prominence is primarily about size and position, but a modestly sized cat at the natural focal point of the composition can still score well. The question is whether the cat registers as the subject at a glance or whether the frame overwhelms it.

### 3. Visual Isolation — [{{ .Task2 }}](https://github.com/{{ .Owner }}/{{ .Task2 }})

Evaluates how cleanly the cat separates from its surroundings across two dimensions. First, *background separation*: does the cat's color, texture, and form contrast against what is behind it, or does it camouflage into a similarly colored background? Second, *freedom from competition*: are there other visually demanding elements — other animals, people, bold patterns, bright objects — pulling the viewer's eye away? A cat alone on a contrasting surface scores highly. A cat buried in visual clutter scores poorly.

## Scoring Philosophy

Technical resolution and sharpness are secondary to perceptual clarity. A slightly soft image where the cat is still clearly the dominant visual element should score higher than a razor-sharp image where the cat is lost among distractions. This function measures whether the cat *owns* the photograph — whether a viewer can look at it and say, without hesitation, that it is a picture of a cat.