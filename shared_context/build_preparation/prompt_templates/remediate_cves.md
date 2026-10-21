> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Fix Security Vulnerabilities

> Remediate vulnerabilities from a scan, audit, or pen test

Start here when a scanner, audit, or pen test has identified specific vulnerabilities to fix.

## How it works in Blitzy

**1. Describe the findings**

Paste the CVE numbers, the pen test report, or the scanner output. Tell Blitzy which vulnerabilities to fix and which compliance frameworks apply.

**2. Review the Agent action plan**

Blitzy maps every vulnerability to a specific code change - parameterized queries for SQL injection, token validation for auth bypasses, secret rotation for hardcoded credentials - before writing any code.

**3. Generate and review**

Blitzy implements the fixes and generates security tests that verify each vulnerability is closed. Review the PR with your security team.

**4. Validate and merge**

Run your security scanners against the fixed code to confirm remediation. Merge when the findings are clean.

## What makes a good prompt?

A good security prompt describes what needs to be fixed and what standard the fix must meet.

**Start with the findings.** Paste CVE numbers, CWE categories, or the specific vulnerabilities from your pen test report. "Fix CVE-2024-1234 in the authentication module" gives Blitzy a precise target.

**Name the compliance framework.** If the fixes need to satisfy SOC 2, PCI-DSS, or HIPAA, say so. Blitzy generates documentation that maps each fix to specific compliance controls.

**Never include real credentials.** Use the placeholder pattern (`${SECRET_NAME}`) for all secrets. Share actual credentials with your Blitzy consultant through secure channels, not in prompts.

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first security prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **Security fix prompt template**
>
> ```
> Fix security vulnerabilities in [Project Name]. Address only the
> identified vulnerabilities without modifying unrelated code.
>
> VULNERABILITY ASSESSMENT
>
> - What specific vulnerabilities need to be fixed?
>   [CVE numbers, scanner findings, or pen test report items.]
> - What is the severity of each?
>   [Critical, High, Medium, Low - and potential business impact.]
> - What compliance frameworks apply?
>   [SOC 2, PCI-DSS, HIPAA, or internal security standards.]
>
> SCOPE
>
> - What components are affected?
>   [List affected files, modules, or layers.]
> - What must remain untouched?
>   [Critical features or interfaces that cannot change.]
>
> TECHNICAL IMPLEMENTATION
>
> - How should fixes be implemented?
>   [Patches, middleware, config changes, or architectural updates.]
> - What dependencies need updating?
>   [Vulnerable packages that need version upgrades.]
>
> TESTING & VALIDATION
>
> - What security tests should verify the fixes?
>   [Pen test scenarios, scanner checks, or security-focused test cases.]
> - What regression tests confirm existing functionality?
>   [Existing test suites that must still pass.]
>
> CONSTRAINTS
>
> - Make only the minimal necessary changes to remediate each vulnerability.
> - Do not modify code unrelated to the security findings.
> - Use placeholder pattern (${SECRET_NAME}) for all credentials.
> ```

## What if something goes wrong?

> **Security scanners still report vulnerabilities**
>
> Vulnerability may not be fully remediated. Re-run scanners with verbose output, review CVE remediation guidance, and add the [Catalog Security Vulnerabilities](https://docs.blitzy.com/templates/rules/catalog-security-vulnerabilities) rule to your project on the platform for comprehensive coverage.

> **Secrets still appear in logs or errors**
>
> Logging may not be fully masked. Implement custom log formatters that pattern-match sensitive data (tokens, keys, passwords), ensure error messages truncate or redact secrets, and review all log output.

> **Authentication still vulnerable after OAuth implementation**
>
> Token validation may be incomplete. Verify signature validation, expiration checks, issuer validation, and scope enforcement. Add tests for token manipulation attempts.

> **Compliance audit fails after security fixes**
>
> Documentation may be incomplete. Map each security control to specific compliance requirements, update security documentation with implementation details, and provide audit trail of security changes.

> **Performance degrades after security implementation**
>
> Security controls may be inefficient. Profile authentication/authorization paths, implement caching for token validation, optimize encryption operations, and add the [Analyze Performance Impact](https://docs.blitzy.com/templates/rules/analyze-performance-impact) rule to your project on the platform.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.