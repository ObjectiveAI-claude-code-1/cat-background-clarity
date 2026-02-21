# cat-background-clarity

## Overview

`cat-background-clarity` is a scalar function that evaluates the subject isolation of a cat in a photograph. Given an image, it returns a score between 0 and 1 measuring how completely the visual environment surrenders attention to the cat — how cleanly the cat separates from its surroundings and how free the image is from competing distractions.

This is not a measure of photographic beauty, artistic merit, or composition. It is purely a measure of isolation: does the image belong to the cat, or does the cat have to fight for it?

## Input

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `image` | image | Yes | A photograph containing a cat. |

The image can be anything from a professional studio portrait to a casual phone snapshot. It may be tightly cropped or capture an entire room. The function evaluates the full scene as presented.

## Output

A scalar score in the range **[0, 1]**:

- **Near 1.0** — The background is clean, quiet, and free of distracting elements. The cat stands forward as the singular, unambiguous focus. There is nothing else for the eye to latch onto.
- **Near 0.5** — The scene has moderate visual activity. The cat is identifiable as the primary subject, but the background or surrounding elements draw some attention away.
- **Near 0.0** — The scene is visually noisy, cluttered, or filled with competing elements. The cat is present but does not dominate — it is lost among distractions.

## What It Evaluates

The function scores each image across three distinct qualities, each examining a different dimension of the relationship between the cat and its surroundings:

### 1. Background Simplicity

How quiet, uniform, and visually undemanding is the space surrounding the cat?

- **High simplicity:** Solid-colored walls, soft bokeh, clear skies, plain surfaces — backgrounds that recede completely and draw no attention to themselves. If the cat were removed, the remaining scene would be unremarkable.
- **Low simplicity:** Patterned rugs, busy wallpaper, shelves of books, tangled cables, textured fabrics — backgrounds that are visually loud and assert themselves as participants in the image.

### 2. Element Competition

Are there discrete, identifiable objects or subjects in the frame that compete with the cat for the viewer's eye?

Competing elements include:
- Other animals or human faces (extraordinarily strong attention attractors)
- Brightly colored or saturated objects
- Text overlays, watermarks, or logos
- Screens, toys, food, or furniture with strong visual character

The function considers both the **quantity** and **attentional power** of competing elements. A single other animal can split attention in half. Text demands to be read. Zero competing elements means the cat reigns unchallenged.

### 3. Subject Emergence

Does the cat naturally and effortlessly emerge as the singular focal point of the image?

This is the holistic, perceptual verdict — where background simplicity and element competition converge into a single outcome. A cat may still emerge strongly from a moderately busy background if it is visually distinct through contrast, lighting, or spatial separation. Conversely, a cat may fail to emerge even against a simple background if it blends in or a powerful distraction dominates the foreground.

- **Strong emergence:** The viewer's eye lands on the cat immediately, without hesitation or wandering.
- **Weak emergence:** The viewer's gaze fragments, bounces between elements, or must search for the cat.

## Use Cases

- **Pet photography platforms** — Surface the most striking, distraction-free portraits in a gallery by ranking on subject isolation.
- **Social media tools** — Recommend which cat photos will perform well in fast-scrolling feeds, where strong subject isolation captures attention instantly.
- **Photo contests** — Filter submissions to separate clean, focused portraits from cluttered snapshots.
- **ML dataset curation** — Select training images where the cat is unambiguously the subject, reducing label noise in cat recognition datasets.
- **Content moderation** — Enforce visual quality standards for cat-focused platforms or communities.

## Scoring Philosophy

The function treats subject isolation as a measure of **visual generosity** — how much of the image's attention budget is given freely to the cat. A perfect score describes an image stripped of everything except the cat and silence. A score near zero describes an image where the cat is lost in a storm of visual noise. Most images fall somewhere in between, and it is in that middle ground where the function does its most meaningful work: drawing a precise line between clarity and clutter.