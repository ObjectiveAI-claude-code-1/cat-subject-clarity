# cat-subject-clarity

Evaluates how clearly a cat serves as the undeniable subject of a photograph. Scores three dimensions — focus distinction, subject prominence, and visual separation — to determine whether the cat commands the image at first glance, without requiring the viewer to search, squint, or zoom in.

## Purpose

`cat-subject-clarity` answers one question: **does this photograph belong to the cat?**

Not whether a cat appears somewhere in the image. Not whether a cat can be located upon careful inspection. The question is whether the cat is the immediate, commanding subject of the photograph — the thing your eye lands on before your brain has finished processing the scene. It is the difference between a photograph *of* a cat and a photograph that merely *contains* one.

This is a perceptual evaluation, not a technical one. The function does not care about resolution, camera quality, or artistic composition. It cares about whether the cat hits the viewer instantly. A slightly soft image where the cat is clearly the dominant visual element scores higher than a razor-sharp image where the cat is lost among distractions.

## Input

The function accepts a single **image** input: a photograph in which a cat is expected to be present.

The function does not perform cat detection — it assumes a cat exists in the image. What it evaluates is how well that cat functions as the subject. The photograph can be of any style, resolution, or composition, from a professional studio portrait to a hastily snapped phone picture. The function works across all contexts because subject clarity is about perceptual immediacy, not photographic perfection.

## Output

A **scalar score between 0 and 1**.

- **High scores (near 1.0):** The cat is sharp, prominent, and visually uncontested. It commands the frame and is the first thing any viewer would notice.
- **Low scores (near 0.0):** The cat is blurry, tiny, camouflaged, or visually buried among competing elements. The viewer must search, squint, or zoom to find or identify the cat.

The final score is a weighted aggregation of three independent sub-function evaluations, each measuring a distinct dimension of subject clarity.

## What It Evaluates

Subject clarity is not a single property. It emerges from three independent qualities, each addressing a different way a cat can be lost in its own photograph.

### 1. Focus Distinction — [cat-depth-separation](https://github.com/ObjectiveAI-claude-code-1/cat-depth-separation)

Scores how sharply the cat is rendered **relative to everything else** in the frame. What matters is the gap in clarity between the cat and its surroundings — not absolute sharpness.

- **Scores high** when the cat is the sharpest element in the frame and the background falls into softness, creating a natural depth-of-field hierarchy that draws the eye.
- **Scores low** when the cat is out of focus, when focus is locked on a non-cat element, or when uniform sharpness across the entire image leaves the cat with no focus-based advantage.

### 2. Subject Prominence — [cat-prominence-in-frame](https://github.com/ObjectiveAI-claude-code-1/cat-prominence-in-frame)

Scores how much the cat occupies and commands the physical space of the frame. This evaluates size, position, and visual weight — whether the cat feels like the reason the photograph was taken.

- **Scores high** when the cat is large in the frame, positioned at a natural focal point, and feels like the gravitational center of the composition.
- **Scores low** when the cat is tiny, distant, cropped awkwardly, pushed to an extreme edge, or dwarfed by the scale of its surroundings.

### 3. Visual Separation — [{{ .Task2 }}](https://github.com/ObjectiveAI-claude-code-1/{{ .Task2 }})

Scores how well the cat stands apart from its background and from competing visual elements. This has two dimensions: contrast against the environment, and absence of visual competition.

- **Scores high** when the cat's form, color, and texture create a clear boundary against its surroundings and no other elements compete for the viewer's attention.
- **Scores low** when the cat camouflages into a similarly colored or textured background, or when the scene is visually crowded with other animals, people, bright objects, or bold patterns that rival the cat for attention.

## Use Cases

- **Content curation platforms** — Distinguish between striking, subject-clear cat images and ambiguous images where the cat is incidental to the scene.
- **Machine learning datasets** — Filter training images to ensure cats appear as clear, dominant subjects rather than tiny, half-hidden figures in cluttered backgrounds.
- **Pet adoption services** — Evaluate profile photographs to ensure an animal's photo will stop someone mid-scroll and create an immediate connection.
- **Upload quality gates** — Validate that user-submitted cat photographs actually *work* as photographs of a cat, beyond merely containing one.

## Philosophy

The guiding principle of `cat-subject-clarity` is **perceptual immediacy**. When a viewer glances at a photograph, the cat should be the first thing they see, the thing they cannot miss, the undeniable subject of the image. The cat should never have to compete for its own photograph.