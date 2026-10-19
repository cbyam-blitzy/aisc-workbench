---
name: blitzy-write-follow-up-email
description: Turn a customer meeting transcript or notes into a short follow-up email draft in Blitzy's writing style - a few sentences on key items discussed, decisions made, and blockers cleared, followed by an owner-first action items list. Use this whenever the user asks to recap, summarize, or follow up on a call or meeting with any customer or prospect, pastes or points to a transcript, or says things like "write the recap", "draft the follow-up email", "send notes from today's call", or "what did we agree on" - even if they don't say "email".
---

# Meeting Recap Email

Read and follow `shared-context/file_naming_directives.md` when delivering files. Locate it in the working repository when this skill is loaded from a plugin cache.

Produce a short, scannable follow-up email the user can send to the customer after a call. Customers skim these. The goal is that someone who missed the meeting knows in 20 seconds what was decided and who owes what.

## Step 1: Find and read the sources

**The transcript.**
- If the user names or attaches a transcript, use it. Otherwise look in the project folder for transcripts (commonly a `Transcripts/` folder, files often named `{M-D}-{Meeting Name}`). If several match and the user did not specify, pick by meeting name or date. If still ambiguous, ask.
- If the requested transcript doesn't exist, say so. Don't substitute another meeting or invent content.
- Read the whole transcript before writing. Decisions and commitments often land in the last minutes.
- Transcripts are auto-generated and garbled (names misspelled, numbers wrong, speakers mislabeled). Use the Participants section to resolve names. If a figure, date, or name is ambiguous, flag it in the note after the email instead of guessing.

**The Blitzy Writing Style Guide.** Read and follow
`shared-context/blitzy_writing_style_guide.md` before drafting. It is the
project-wide source of truth for voice, structure, formatting, and claims.
The fixed subject format in Step 2 takes precedence over the guide's general
subject-line guidance.

## Step 2: Draft the email

Deliver the draft in chat, not as a file, unless the user asks for a file.

```
Subject: {Meeting name} - {Month D, YYYY} - Follow Up

Hi {customer attendee first names, or "team"},

{One line: thanks + the goal, e.g. "Thanks for the time today. Here is where we landed and what each side owns to keep the POV on track."}

{2-4 sentences: key items discussed, decisions made, blockers cleared. Lead with the most important outcome.}

Blitzy actions:
- **{Owner first name}** to {action}.
- ...

{Customer} actions:
- **{Owner first name}** to {action}.
- ...

{Short close, e.g. "We'll start on our side in parallel. Anything I've missed, let me know."}

Best,
{User's first name}
```

Why each piece looks this way:

- **Subject line is deliberately plain**: the meeting's name as it appears in the transcript title, then the meeting date with the month spelled out, then "Follow Up". Example: "ExampleCo & Blitzy - Technical Discussion (Access and Security) - October 5, 2026 - Follow Up". The user wants a simple, predictable subject that threads cleanly, so don't add a headline or outcome to it.
- **Opening in one line** (thanks plus the goal) follows the style guide. Don't add a second pleasantry.
- **The summary is prose, not bullets.** It reads like a person wrote it. Prioritize outcomes (decisions, unblocked items, agreed scope) over a play-by-play, because the customer attended and only needs what changes their next step. If the call produced an open blocker, state it in one neutral clause paired with the next step to resolve it.
- **Action items are owner-first bullets**: "**Owner** to action." Name the owner exactly as the transcript shows them volunteering or being assigned. Never infer from job title or role, since a wrong owner in a customer-facing email is worse than a missing one. If no one clearly owns an action, write "Owner TBD" and mention it in the note. Never use a vague owner like "Blitzy team" if a person spoke up.
- **Group asks under one header per side** (ours first, then the customer's). Use a single "Actions:" header only if one side has nothing. Keep the list to what the call actually committed. If a call produced a long tail of minor items, keep the ones that gate progress and fold the rest into a single bullet or leave them out.
- **Dates only when committed on the call.** Don't invent deadlines. Spell out the month and include the year, since customers are often international and 10/5 is ambiguous.
- **Keep the send clean.** Skip optional offers (runbooks, extra calls) unless they were the point of the meeting. Fit the whole email on one screen.
- **Don't leak internal content.** Leave out internal-only commentary, pricing strategy, candid opinions about the customer, anything said off the record, and internal-side logistics like who joined late.

## Step 3: Add a brief note to the user, outside the email

After the draft, add 1-3 short lines only if useful: ambiguities you resolved or couldn't (garbled names, figures), owners you assumed, or risks you left out of the email on purpose. Skip the note if there is nothing to flag. Separate it clearly from the draft so the user can copy the email without editing.

## Reusing across accounts

Nothing here is account-specific. Pull the customer name, attendees, and our company from the transcript header. If the project folder also contains an account-specific recap format or sample, follow it where it conflicts with the defaults above and tell the user you did.
