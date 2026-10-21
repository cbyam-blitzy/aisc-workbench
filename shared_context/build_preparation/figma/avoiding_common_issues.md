> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Avoiding Common Issues

> The eleven most common output-quality issues - what causes them, the warning signs to watch for, and how to fix them before code generation.

Output quality issues in Blitzy follow patterns. The same eleven quirks appear across engagements because they share the same root causes: ambiguous specs, visibility-toggled states, mismatched icon libraries, token drift, and single-viewport frames. Recognizing the pattern before code generation is the highest-leverage intervention - a condition caught in the AAP costs minutes; the same condition caught in code review costs hours.

Use this catalog in two ways: **before running**, to eliminate conditions that produce known quirks; **during AAP review**, to recognize signals that predict them.

***

## The catalog

> **Q1 - Hallucinated UI elements**
>
> **Extra dividers, close buttons, dropdowns, badges, dialogs, panels, or branded marks that weren't in the design.**
>
> The single most common failure mode. When the spec is ambiguous - an unlabeled frame, a partially-drawn interaction, a missing state - the platform adds plausible UI rather than leaving a gap. The additions are contextually reasonable; they're just not what you designed.
>
> **Root cause:** ambiguity in the spec. The platform fills uncertainty with inference.
>
> **AAP signal:** component descriptions that include elements not present in your Figma, or behavioral directives that reference UI you didn't draw.
>
> **Mitigation:** close the spec before running. Every state drawn, every behavior annotated. Ambiguity is the input; hallucination is the output.

> **Q2 - Hidden-state leakage**
>
> **Hover, selected, or disabled states bleed through into the default render.**
>
> States authored as visibility-toggled layers inside a single frame are all present in the node tree, regardless of their visibility setting. The platform's structural reader sees them. When the screenshot and the node tree disagree about what's visible, the screenshot wins - but the structural read still influences conditional rendering logic, and the wrong state can surface.
>
> **Root cause:** states modeled as overlay layers rather than proper component variants.
>
> **AAP signal:** the platform enumerates states it "detected" that you didn't intend as independent states.
>
> **Mitigation:** model all states as component variants with named variant properties. Remove toggled layers from export frames entirely.

> **Q3 - Icon fidelity**
>
> **Wrong icon, wrong size, wrong color, or wrong icon family in the output.**
>
> The most-cited single category across documented engagements. Caused by a mismatch between the icon family used in Figma and the library installed in the codebase, or by detached icon instances that were manually edited after detaching.
>
> **Root cause:** Figma and code use different icon families, or icons in Figma are detached and modified.
>
> **AAP signal:** asset references that name icons not present in the codebase's installed library.
>
> **Mitigation:** use the same icon family in Figma as exists in code (`lucide-react`, `heroicons`, `@phosphor-icons`, etc.). Finalize icon choices before running - substitutions after the run require a new run.

> **Q4 - Asset reproduction issues**
>
> **Illustrations, photos, custom graphics, or geometric shapes degrade or get replaced.**
>
> Blitzy downloads assets directly from Figma rather than reconstructing them from screenshots. Complex Figma constructs - multiple boolean operations, stacked effects, complex masks - can't always be preserved through the asset pipeline. The output substitutes or drops them.
>
> **Root cause:** Figma assets built from complex constructs the pipeline can't pass through cleanly.
>
> **Mitigation:** flatten complex decorative assets to a single exportable layer before running. For illustrations and photography, ensure they're attached as clean, exportable frames - not Figma-native constructs.

> **Q5 - Color fidelity drift**
>
> **Semantic colors (success-green, danger-red) and brand hex values render slightly off.**
>
> Caused by design tokens defined in Figma Variables but not in code, or by hardcoded hex values in the Figma that don't correspond to the codebase's token system. The platform produces what it finds; if the values don't match, the output reflects the mismatch.
>
> **Root cause:** token systems in Figma and code that disagree, or Figma values that don't have code equivalents.
>
> **AAP signal:** color values appearing as raw hex in the AAP instead of token references.
>
> **Mitigation:** resolve the token mapping before running. If Figma Variables are not yet mirrored in code, document the mapping in a spec note adjacent to the frame.

> **Q6 - Spacing, sizing, and dimension drift**
>
> **Non-standard pixel values get rounded; button widths over-extend; font weights heavier than designed; line weights heavier.**
>
> The platform rounds Figma values to the nearest step in the codebase's spacing scale. A `14px` gap in Figma against a `4px`-base spacing system rounds to `16px`. A font weight of `550` rounds to `600`. Drift compounds across a dense layout.
>
> **Root cause:** Figma values that don't snap to the codebase's spacing and type scale.
>
> **Mitigation:** design on the codebase's scale from the start. If your Figma uses arbitrary values, document intended code equivalents in spec notes (`gap: 14px → gap-3 in Tailwind`).

> **Q7 - Responsive behavior gaps**
>
> **Locked widths (often 1440px), missed breakpoints, single-viewport implementation.**
>
> The platform extrapolates responsive behavior from a single frame. The extrapolation is approximate - it reflects the platform's training average for responsive patterns, not your specific design decisions.
>
> **Root cause:** single-viewport Figma submissions.
>
> **Mitigation:** provide frames at each breakpoint that matters. One screen at three breakpoints outperforms five screens at one breakpoint for fidelity. See [Auto-Layout](https://docs.blitzy.com/design-with-blitzy/auto-layout) for frame labeling conventions.

> **Q8 - Typography fidelity drift**
>
> **Font family substituted, italicization flipped, weight heavier than designed.**
>
> The platform substitutes the closest available font when the designed typeface is not installed in the codebase. The closest match is usually wrong for brand - particularly for display typefaces, custom fonts, and variable fonts.
>
> **Root cause:** fonts in Figma that aren't shipped in the codebase.
>
> **AAP signal:** typography references that name a font family not present in the codebase's font loading.
>
> **Mitigation:** confirm your primary and display typefaces are loaded in the codebase before running. Document intended fallbacks in a spec note if brand fonts aren't available yet.

> **Q9 - Charts and data visualization gaps**
>
> **Graph paths off, axis labels overlapping, chart styling missed or approximate.**
>
> The visualization library installed in code constrains what's achievable. The platform maps Figma chart frames to the nearest library equivalent - if the library can't express the design, the output is the best approximation it can produce.
>
> **Root cause:** the visualization library's API doesn't support what the Figma shows.
>
> **Mitigation:** design charts against the API surface of your installed library. If the design requires capabilities the library doesn't have, document that gap in the spec before running so the AAP reflects it explicitly.

> **Q10 - Wizard and form interaction gaps**
>
> **Active-state semantics fragile, form validation copy concatenated, step indicators dropped or duplicated.**
>
> Multi-step interactions require explicit annotation. The platform's inference is weaker on sequential interaction patterns than on single-screen layouts - it can detect step structure from frame sequencing but can miss the conditional logic that governs transitions.
>
> **Root cause:** complex interaction patterns without behavioral annotation.
>
> **Mitigation:** annotate every step transition: trigger, condition, and destination. Annotate form validation: which fields validate on blur vs on submit, what the error strings are, whether validation is inline or summary. Don't leave these to inference.

> **Q11 - Tokens that aren't really tokens**
>
> **CSS variables in the output appear as token bindings but silently resolve to hardcoded hex fallbacks.**
>
> Some codebases use the pattern `var(--name, #fallback)` where `--name` is never defined in `:root`. The browser falls through to the hex fallback. The platform reproduces the pattern exactly - so the output looks like token usage but renders the literal hex.
>
> ```css theme={null}
> /* Looks like a token binding. Isn't. */
> color: var(--text-text-secondary, #333333);
> /*           ↑ never defined in :root      ↑ this is what renders */
> ```
>
> **Root cause:** codebase patterns that look like tokenization but aren't.
>
> **Mitigation:** this is a codebase issue, not a Figma issue. Document it as a known behavior before the run so reviewers understand why hardcoded hex appears in the output. Fixing the pattern is a separate codebase task.

***

## The platform reads literally

Underlying all eleven quirks is a single platform behavior: **Blitzy follows instructions to the letter**. A senior developer recognizes a typo or minor inconsistency and makes a reasonable judgment call. The platform does not. Whatever you specify, it honors. If you specify something twice with a slight variation, it treats each as a distinct intentional instruction and tries to honor both.

This puts the responsibility on the designer to audit the spec for internal consistency before running - not after.

***

## Related

> **[Components & Variables](https://docs.blitzy.com/design-with-blitzy/components-variables)**
>
> Authoring states, assets, and tokens

> **[Spec Notes & Prompting](https://docs.blitzy.com/design-with-blitzy/spec-notes)**
>
> Conflicting signals and literal reading behavior

> **[Pre-Flight Checklist](https://docs.blitzy.com/design-with-blitzy/pre-flight)**
>
> Consolidated audit


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.