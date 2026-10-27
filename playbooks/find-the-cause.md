# Find the cause before changing behaviour

1. Record expected and observed behaviour with safe inputs. Reproduce the failure
   and record command and result. If reproduction fails, say unknown.
2. Trace the first divergence. Inspect recent relevant changes and compare one
   working case with the failing case.
3. State one cause hypothesis and what would disprove it. Change one variable in
   a small experiment; preserve the original evidence.
4. Confirm the cause, then write a regression check that fails for it. Follow
   [test first](test-first.md), fix minimally and run relevant checks.
5. If experiments repeatedly contradict the explanation, stop patching. Revisit
   the model with the owner and record evidence and uncertainty.
6. Report cause, change, failing and passing evidence, and limits of proof.

Never weaken checks or use private data without authority. Attribution is in
[NOTICE](../NOTICE.md).
