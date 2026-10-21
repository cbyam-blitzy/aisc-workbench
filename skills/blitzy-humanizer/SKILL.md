---
name: blitzy-humanizer
description: Edit text to remove signs of AI-generated writing and make it sound natural and human. Use when the user asks to humanize, de-AI, or make text sound less like AI, ChatGPT, or Claude; when a draft is robotic, generic, or AI-istic; or when they want a rewrite in their own voice from a sample.
---

# Blitzy Humanizer

Read and follow `shared_context/standards/file_naming_directives.md` when delivering files. Locate it in the working repository when this skill is loaded from a plugin cache.

Edit writing so it sounds like a person wrote it without changing its meaning. Remove AI-writing tells, then restore an appropriate human voice. Do not make formal material performatively casual: match the document's register.

## Workflow

1. Read [the pattern guide](references/patterns.md) before editing.
2. Read and follow `shared_context/standards/writing_style_guide.md` before drafting. It is the repository's current source of truth for Blitzy voice and claims.
3. If the user provides a writing sample, calibrate to it before rewriting. Note its sentence rhythm, word choice, openings, punctuation, recurring phrases, and transitions.
4. Rewrite the problem sections. Prefer plain, specific language over generic polish. Keep the original message, facts, intended tone, and format intact.
5. Review the rewrite aloud in effect: vary rhythm where natural, use simple verbs such as “is,” “are,” and “has” where they fit, and remove remaining slogan-like or evenly paced phrasing.
6. Do a second pass. Ask: “What still makes this sound obviously AI-generated?” Remove those remaining tells before finalizing.

## Blitzy reference context

For text about Blitzy, consult `shared_context/platform/glossary.md` for unclear terminology and the relevant overview page when a wording change could alter a capability or workflow claim. Preserve the source meaning and do not add platform claims merely to enrich the rewrite. Flag material discrepancies separately instead of silently changing facts. Ordinary prose editing does not require loading the overview library.

## Facts and voice

Humanizing changes expression, not truth. Use a specific detail only when it appears in the user's text or writing sample. Otherwise cut the vague claim or qualify it honestly. Never invent studies, quotes, statistics, people, or dates.

With a writing sample, replace AI patterns using that voice rather than merely deleting them. Without one, use clear, restrained prose. A little personality can work in an email, blog post, or opinion piece; for contracts, technical specifications, formal reports, and customer deliverables, use plain and specific neutral prose instead. The Blitzy style guide controls when it conflicts with a source style preference.

## Output

Unless the user asks for only the finished version, provide the following in order:

1. **Draft rewrite**
2. **What makes the below so obviously AI generated?** Brief bullets on any remaining tells.
3. **Final rewrite**
4. **Summary of changes** when it helps explain the edits.

If the user asks for the clean version only, provide only the final rewrite.

## Source

This workflow is adapted from Wikipedia's “Signs of AI writing” guidance maintained by WikiProject AI Cleanup. The reference guide records the patterns used for edits.
