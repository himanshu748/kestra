# Kestra #4811 test-report screenshots

These four PNGs are genuine browser captures of Gradle test reports from the
before/after fixture runs. Their bytes are unchanged from the original captures;
`manifest.json` records verified SHA-256 hashes and sanitized provenance.

| Class | Before | After |
| --- | --- | --- |
| `ConcurrencyLimitServiceTest` | [Baseline report](1-before-concurrency.png) | [Minimal-fixture report](2-after-concurrency.png) |
| `ExecutionControllerRunnerTest` | [Baseline report](1-before-execution-controller.png) | [Minimal-fixture report](2-after-execution-controller.png) |

## What the images show

Each image contains the original, unmodified Gradle HTML class report below a
clearly labelled context header. The header transcribes the recorded checkout
commit, working-tree diff hash, JUnit XML test results and durations, and whole
command wall time. The report itself is not recreated or restyled. XML suite
and Gradle HTML suite durations can differ; both remain exactly as recorded by
their respective reports. Per-method durations and outcomes are also visible.

These screenshots cover four concurrency-service tests and three execution-
controller tests, all passing in both runs. The separate replay test belongs to
the focused command but is not shown in these two class-report screenshots.
The command wall time spans both modules and includes Gradle overhead.

## Capture base and publication base

The screenshots were captured on checkout commit
`4caa156a807552ebdc128bd433f2db0e7cee0e20`. The baseline capture had an empty
recorded working-tree diff; the patched capture had the minimal-flow changes
in its working tree. Their visible commit labels intentionally remain those
of the actual capture runs.

The source patch was subsequently cleanly rebased onto publication base
`9b6c7adaea1ce70ddc9f893e0b89d9610a683576`, producing source commit
`0582fecd25d57903161ae37df0c613370433c873`. These earlier screenshots do not
claim to show a run on that newer commit. Verification of the rebased source
is reported separately in the pull request.

The screenshot runs were separate runs that included recompilation. Their
wall times are **excluded from the original three-run timing medians**. Use
the pull request's recorded three-run comparison for the reported performance
measurement; these images provide readable test-report evidence and context.

This evidence branch contains only the four screenshots, this README, and the
sanitized manifest. It contains no source-code changes or raw test logs.
