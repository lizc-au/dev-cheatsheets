# Coverage & Thresholds

- Coverage = how much code ran during tests (Statements, Branches, Functions, Lines).
- Thresholds = minimum %s enforced by the test runner; CI fails if any metric drops below.

How to check (Jest):
- Run: npm run test:coverage
- Open HTML report: coverage\lcov-report\index.html

Tips:
- Keep thresholds realistic; raise gradually as code stabilizes.
- Target red/uncovered lines first in the HTML report.
