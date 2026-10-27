# Test a behaviour change first

1. Make one observable behaviour check from the issue's done test, using safe
   inputs and agreed figures rather than deriving expectations from code.
2. Run before the fix. Observe the expected failure and reason. An import error
   or missing tool does not demonstrate incorrect behaviour.
3. Make the smallest change that passes. Run the check and relevant nearby checks.
4. Improve structure only as needed, keeping behaviour checks passing.
5. Ask whether the check could pass while the person's task stays broken. Add a
   boundary or integration check where this exposes a real gap.
6. Record commands, failing and passing results, commit and proof limits.

Never invent a failure, plant a credential or weaken an expectation. Mechanical
prose edits need appropriate review rather than artificial behaviour tests.
Acceptance is separate. Attribution is in [NOTICE](../NOTICE.md).
