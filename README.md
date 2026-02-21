# cat-subject-clarity

Evaluates how clearly a cat serves as the undeniable subject of a photograph. Scores three dimensions of perceptual clarity — focus dominance, subject prominence, and visual separation — to determine whether the cat commands the image at first glance without requiring the viewer to search or squint.

## Input

The function accepts a single **image** input: a photograph presumed to contain a cat.

The function does not detect whether a cat is present. It evaluates how clearly and confidently the cat presents itself as the subject of the image. The photograph may be of any resolution, aspect ratio, or photographic style — what matters is whether the cat is perceptually dominant within it.

## Output

A **scalar score between 0 and 1**.

- A score near **1** means the cat plainly, unmistakably commands the photograph. It is the first thing the viewer notices and there is no ambiguity about what the image depicts.
- A score near **0** means the cat is diminished, hidden, camouflaged, or competing with other elements. The viewer must work to find or identify the cat within the frame.

## What It Evaluates

Subject clarity is not a single property. It emerges from three distinct perceptual qualities, each evaluated by a dedicated sub-function:

### 1. Focus Dominance — [cat-focus-dominance](https://github.com/ObjectiveAI-claude-code-1/cat-focus-dominance)

Scores whether the cat is the sharpest and most crisply rendered element in the image relative to its surroundings. A cat in clear focus against a softer background draws the eye naturally. A cat that is blurry, soft, or no sharper than everything else loses its focal authority.

This evaluation measures *relative* focus, not absolute sharpness. A slightly soft image where the cat still holds the focal advantage scores higher than a uniformly sharp image where the cat enjoys no such advantage. What matters is whether the optics of the photograph direct the viewer's attention toward the cat.

### 2. Subject Prominence — [cat-compositional-prominence](https://github.com/ObjectiveAI-claude-code-1/cat-compositional-prominence)

Scores whether the cat occupies enough of the frame, with sufficient size and intentional placement, to register immediately as the subject. A cat that fills a commanding portion of the frame reads as the reason the photograph was taken. A cat that is tiny, marginal, or dwarfed by its environment reads as incidental.

This evaluation considers the cat's size relative to the frame, its compositional placement, and whether the spatial relationship between the cat and the borders of the image communicates intentionality.

### 3. Visual Separation — [cat-visual-separation](https://github.com/ObjectiveAI-claude-code-1/cat-visual-separation)

Scores whether the cat is visually distinct from the background and free from competing elements. A gray cat on a gray couch becomes texture. A tabby on a patterned rug becomes camouflage. A black cat in a dark room becomes a shadow. This evaluation measures how well the cat stands apart through contrast in color, tone, texture, and spatial boundaries.

It also accounts for visual clutter — other animals, people, bright objects, or bold patterns that pull the viewer's gaze away from the cat. The cat should not have to compete for attention.

## Use Cases

- **Adoption platforms** — Ensure uploaded cat photos clearly show the animal so prospective adopters can see what the cat looks like.
- **Breed identification** — Gate photographs before passing them to breed classifiers, filtering out images where the cat is too obscured to classify reliably.
- **Content quality** — Score cat photos on social platforms to surface images where the cat is the clear subject, improving feed and recommendation quality.
- **Veterinary records** — Validate that submitted photos are usable for visual health assessments by confirming the cat is clearly visible.
- **Downstream quality gate** — Use as a pre-filter before any image analysis pipeline that depends on the cat being clearly present and identifiable in the frame.

## Philosophy

This function measures *visual presence* — not photographic beauty, artistic merit, or technical perfection. A photograph with strong subject clarity produces instant, effortless recognition: *that is a cat*. A photograph with weak subject clarity introduces hesitation, confusion, or the need to search. The evaluation is perceptual, not technical. It describes what the human eye experiences in the first fraction of a second of looking, before conscious analysis begins.

A cat with strong subject clarity does not ask to be noticed. It insists.