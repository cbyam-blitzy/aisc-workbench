> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Start with Figma

> The 80/20 of authoring a Figma file for Blitzy - a handful of broadbrush habits that get you most of the way, plus what to expect from your output.

You don't need a perfect Figma file to get a great result from Blitzy. A handful of habits get you most of the way there - this page covers them. The deeper pages in this section are here for when you want to refine quality or work through a specific issue, but if you do the things below, **you're good to go.**

The one idea worth holding onto: Blitzy **makes meaning by grouping.** Group your screens with intent and most of the rest follows. (See [How Blitzy Reads Figma](https://docs.blitzy.com/design-with-blitzy/how-blitzy-reads-your-figma) for the full mental model.)

> [!NOTE]
>
> First time? You'll need to [connect Figma to Blitzy](https://docs.blitzy.com/integrations/figma) once - a single team token - before your first run.

***

## The handful that matters most

These five habits drive the majority of output quality. None of them takes long.

**1. Group your screens with intent**

Put variants of one UI together, lay flows out in order, and show a screen at multiple sizes when responsiveness matters. Grouping is how the platform reads states, flows, and responsive behavior. Anything that isn't inside a frame can't participate in this reading at all.

![Three grouped examples on a Figma canvas: card states (default, hover, selected), a three-step flow, and one screen at 1440 / 768 / 375 widths.](https://mintcdn.com/blitzy-c2eefe5a/EF5Q5dit_wx7TbA0/images/figma-group-screens-example.png?fit=max\&auto=format\&n=EF5Q5dit_wx7TbA0\&q=85\&s=6afbf73c824a46dd06dcf7d0695a310f)

**2. Name the components, not the noise**

You don't need to name every nested wrapper. The things that map to reusable UI - buttons, rows, cards - are worth a meaningful name, because that name carries straight through to the code: `AccountRow`, not `Frame 1247`. The auto-named wrappers underneath them are fine to leave as they are.

**3. Use auto-layout**

Reach for auto-layout on anything that flows, repeats, or resizes. It maps directly to how the UI responds to content and viewport changes - and it's the single most useful structural signal in a file.

**4. Draw the states you care about**

Default, hover, disabled, loading, error, empty - wherever they matter, draw them as proper component variants and group them together. And where your codebase already has names for them, mirror those in Figma (`Button/Primary` → `variant="primary"`) so the translation is exact rather than inferred.

**5. Mark up what isn't visible**

A screenshot can't carry behavior - state logic, conditional visibility, click-to-toggle, edge cases. Spec notes capture what the picture can't, and they're what keeps behavior from getting dropped between design and code. Both forms count: a text frame placed next to the screen, or a note placed directly on it.

> [!NOTE]
>
> What you draw is what gets built.

> [!TIP]
>
> That's the 80%. Do these and most runs land as a strong, on-brand starting point.

***

## What output to expect

Output quality tracks two things: **how completely your Figma communicates intent** and **how mature your codebase design system is.** They compound - the strongest results come when both are in good shape, and a gap on either side pulls the result down a little.

In practice, expect a run to give you:

> **Accurate structure**
>
> Component hierarchy and layout that reflect what you drew.

> **On-brand styling**
>
> Where your Figma and code speak the same language - shared tokens, matching component names.

> **A few predictable gaps**
>
> A font substitution, a token that falls back to hex, a default-library CTA - all closable, and all visible in the Agent action plan (The platform's plan you review and approve before any code is written.) before any code is written.

The more completely your file is authored, the closer the output lands to pixel-final. For the full picture of what each level looks like - and the concrete steps between them - see [How to Move Up in Fidelity](https://docs.blitzy.com/design-with-blitzy/improving-fidelity).

***

## Starting checklist

A quick pass before your first run. If most of these are true, you're in good shape.

**Your file**

* Screens are grouped with intent - variants together, flows in order, breakpoints shown where they matter.
* Components are named for what they are; auto-named wrappers underneath are fine.
* Auto-layout is applied to anything that flows or resizes.
* The states you care about are drawn as component variants.
* Behavior that can't be drawn - conditional visibility, toggles, edge cases - is captured in spec notes.
* Copy is real, not `Lorem ipsum`.
* Where your code already has component or token names, Figma mirrors them.

**Before you run**

* The codebase is ingested into Blitzy.
* Your prompt is ready and scoped - short, and free of contradictions with the file.

> [!TIP]
>
> Most of these true? You're good to go - run it, and use the deeper pages below only if you want to refine.

***

## When you want to go deeper

Hit a specific issue, or want to push quality further? These are the reference pages:

> **[File & Layer Setup](https://docs.blitzy.com/design-with-blitzy/file-setup)**
>
> Page organization, frame hierarchy, and semantic naming in depth.

> **[Auto-Layout](https://docs.blitzy.com/design-with-blitzy/auto-layout)**
>
> Responsive frames, flows, and absolute positioning.

> **[Components & Variables](https://docs.blitzy.com/design-with-blitzy/components-variables)**
>
> State matrices, variant properties, assets, and tokens.

> **[Pre-Flight Checklist](https://docs.blitzy.com/design-with-blitzy/pre-flight)**
>
> The full audit before a run, plus how to review the AAP.

> **[Attaching Frames & Scoping](https://docs.blitzy.com/design-with-blitzy/attaching-and-scoping)**
>
> How to attach frames to a run and size the work.

> **[Avoiding Common Issues](avoiding_common_issues.md)**
>
> The eleven most common output gaps and how to fix them.

> **[How to Move Up in Fidelity](https://docs.blitzy.com/design-with-blitzy/improving-fidelity)**
>
> The leveling-up guide - where you sit today and the next step up.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.