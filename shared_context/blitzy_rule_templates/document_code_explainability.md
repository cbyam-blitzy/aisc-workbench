Generate code with documentation that explains both WHAT the code does and WHY specific implementation decisions were made, using docstrings and inline comments.

Docstring Requirements:
- Every new or modified function, class, and module entry point must include a docstring
- Each docstring must specify:
  - Purpose: What the function or class does
  - Parameters: Name, type, and description for each parameter
  - Return values: Type and description of what is returned
  - Exceptions or errors: Any that may be raised (where applicable)
- Follow the language's standard docstring format (JSDoc for JavaScript/TypeScript, Javadoc for Java, docstrings for Python, XML comments for C#, etc.)
- Trivial accessors (getters/setters with no logic) may use a single-line docstring

Inline Comment Requirements:
- Place comments adjacent to the code they explain
- Comments must explain WHY a decision was made, not WHAT the code does (the code already shows that)
- Each non-obvious implementation decision should document at least one of the following:
  - **Alternatives Considered:** What other approaches were evaluated and why this one was chosen
  - **Refactoring Rationale:** When replacing existing code, what was wrong with the old approach
  - **Assumptions:** What external contracts, data formats, or behaviors this code depends on
  - **Trade-offs:** What compromises were accepted (performance vs. readability, simplicity vs. flexibility, etc.)

Forbidden Patterns:
- Writing comments that restate what the code does (e.g., "// increment counter" next to counter++)
- Adding docstrings that omit parameters, return values, or purpose
- Leaving a non-obvious implementation choice undocumented when a reasonable alternative exists
- Using vague rationales ("this is better", "for performance") without specific justification

Validation Gate: Every new or modified function must have a docstring with purpose, parameters, and return values. Every non-obvious implementation decision must have an inline comment explaining why that approach was chosen using at least one of the categories above. Code missing either fails review.