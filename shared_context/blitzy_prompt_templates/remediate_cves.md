Fix security vulnerabilities in [Project Name]. Address only the
identified vulnerabilities without modifying unrelated code.

VULNERABILITY ASSESSMENT

- What specific vulnerabilities need to be fixed?
  [CVE numbers, scanner findings, or pen test report items.]
- What is the severity of each?
  [Critical, High, Medium, Low - and potential business impact.]
- What compliance frameworks apply?
  [SOC 2, PCI-DSS, HIPAA, or internal security standards.]

SCOPE

- What components are affected?
  [List affected files, modules, or layers.]
- What must remain untouched?
  [Critical features or interfaces that cannot change.]

TECHNICAL IMPLEMENTATION

- How should fixes be implemented?
  [Patches, middleware, config changes, or architectural updates.]
- What dependencies need updating?
  [Vulnerable packages that need version upgrades.]

TESTING & VALIDATION

- What security tests should verify the fixes?
  [Pen test scenarios, scanner checks, or security-focused test cases.]
- What regression tests confirm existing functionality?
  [Existing test suites that must still pass.]

CONSTRAINTS

- Make only the minimal necessary changes to remediate each vulnerability.
- Do not modify code unrelated to the security findings.
- Use placeholder pattern (${SECRET_NAME}) for all credentials.