# Sample PR Cleanup Receipt

Illustrative sample, not customer work.

## Request

A parser change passes on Linux but fails on Windows when the input contains `+` as a separator. The requested result is a focused fix with a test that proves both `.` and `+` separators work.

## Accepted Scope

- One parser helper
- One failing Windows-shaped fixture
- Focused unit coverage
- No dependency upgrade, release, or deployment work

## Finding

The helper split the input on `.` before normalizing platform-specific separators. Inputs containing `+` reached the fallback branch and produced an empty segment.

## Change

- Normalize the accepted separators before splitting.
- Preserve the existing empty-input behavior.
- Add focused cases for `.`, `+`, and an empty segment.

## Validation

```text
npm test -- parser-separators

PASS parser-separators.test.ts
  4 passed
```

## Remaining Risk

The protected deployment preview is not available from a contributor fork. The focused parser behavior is covered; deployment remains maintainer-owned.

## Next Decision

Run or approve the protected preview. If it passes, the scoped blocker is closed.

## Not Claimed

This receipt does not claim merge approval, deployment success, or third-party payment.
