> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Fix Bugs

> Diagnose and fix a bug with regression tests

Start here when something is broken and you need a targeted fix with a regression test to prevent recurrence.

## How it works in Blitzy

**1. Describe the bug**

Paste the error message, the stack trace, and the reproduction steps. Tell Blitzy what should happen and what actually happens. The more specific the report, the more targeted the fix.

**2. Review the Agent action plan**

Blitzy traces the root cause and shows you its diagnosis - which files it will change, what it believes the underlying problem is - before writing any code.

**3. Generate and review**

Blitzy implements the fix and generates regression tests that fail before the fix and pass after. Review the PR like you would from any teammate.

**4. Merge or refine**

If the fix is right, merge it. If Blitzy addressed the symptom instead of the cause, update your description with what you learned and run again.

## What makes a good prompt?

A good bug fix prompt describes what is broken and what correct behavior looks like.

**Start with the symptoms.** "When a user submits the checkout form with an expired card, the page returns a 500 error instead of showing a validation message." That gives Blitzy the expected behavior, the actual behavior, and the trigger - all in one sentence.

**Include the error output.** Stack traces, error messages, and log entries tell Blitzy where to look. Paste them directly into your prompt.

**Say how to reproduce it.** If you can trigger the bug reliably, describe the exact steps. If it is intermittent, describe the conditions where it appears most often.

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first bug fix prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **Bug fix prompt template**
>
> ```
> Fix the following bug in [Project Name]. Address only the identified
> issue without modifying unrelated code.
>
> THE BUG
>
> - What is the expected behavior?
>   [What should happen.]
> - What actually happens?
>   [What goes wrong - include error messages and stack traces.]
> - How do you reproduce it?
>   [Step-by-step reproduction, or conditions where it appears.]
>
> SCOPE
>
> - What files or modules are likely involved?
>   [Where the bug lives, if known.]
> - What must remain untouched?
>   [Features or code paths that should not change.]
>
> REGRESSION TESTING
>
> - What tests should confirm the fix?
>   [Tests that fail before the fix and pass after.]
> - What existing tests must still pass?
>   [Test suites that validate unrelated functionality.]
>
> CONSTRAINTS
>
> - Fix the root cause, not the symptom.
> - Make only the minimal necessary changes.
> - Do not refactor or optimize code beyond the fix.
> - Include regression tests that prevent recurrence.
> ```

## What if something goes wrong?

> **Fix doesn't resolve the bug**
>
> Root cause may be misidentified. Add more detailed logging to trace execution flow, use debugger to inspect state at failure point, and verify reproduction steps trigger the actual issue.

> **Tests pass but bug persists in production**
>
> Test environment may differ from production. Review the [Environment Configuration](../setup/environment_config.md) guide to align test and production environments, and add integration tests with production-like data.

> **Fix introduces new bugs**
>
> Scope may be too broad. Add comprehensive regression tests before implementing fix, use feature flags for gradual rollout, and test against full suite of existing functionality.

> **Bug is intermittent and unreproducible**
>
> Add detailed logging at suspected failure points, implement distributed tracing for multi-service bugs, and analyze patterns in production logs to identify triggering conditions.

> **Performance degrades after bug fix**
>
> Fix may be inefficient. Profile code before and after fix, add the [Analyze Performance Impact](https://docs.blitzy.com/templates/rules/analyze-performance-impact) rule to your project on the platform, and consider alternative implementation approaches.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.