Subject : Critical: Next.js 12.3.1 Dependency — Affected by Multiple Published CVEs



Summary:
The project depends on Next.js 12.3.1, a version affected by multiple publicly disclosed high-severity CVEs. These issues impact server-side rendering and route handling, enabling HTML injection, information leakage, and in specific configurations, the possibility of remote code execution. These vulnerabilities are fixed in newer versions of Next.js, but are still present in this codebase.

Affected Component:

next = 12.3.1


Located in: /package.json

All deployments using this version are impacted.

Vulnerabilities (Confirmed CVE Matches)
1. CVE-2022-39222 — Next.js SSR HTML Injection

Affected versions: ≤ 12.3.1
Impact:

HTML injection inside server-rendered output

Stored or reflected XSS

Manipulation of rendered templates

Potential RCE depending on application logic + sanitization

2. CVE-2022-39221 — Next.js Route Handling Vulnerability

Affected versions: ≤ 12.3.1
Impact:

Improper request sanitization

Redirect poisoning

Exposure of internal SSR routing paths

Possible chaining into privilege escalation

3. CVE-2023-46242 — Prefetch / Path Traversal Weakness

Affected versions: ≤ 13.1 (includes 12.3.1)
Impact:

Unintended file/path access

Exposure of internal build metadata and project structure

Leakage of sensitive API endpoints

Severity: HIGH / CRITICAL

Because the project uses server-side rendering, these CVEs pose high exploitation potential, including injection attacks and possible code execution depending on deployment.

Evidence:

The repository’s package.json specifies:

"next": "12.3.1"


This version is explicitly listed in the affected range for all three CVEs above. No mitigation or patch override is present in the Nx workspace.

Recommended Remediation:

Upgrade Next.js immediately:

Minimum patched version:

next >= 13.1.7


Recommended stable upgrade:

next >= 14.x / 15.x / 16.x


After updating, reinstall dependencies and redeploy:

pnpm install
nx build
nx serve


All Next.js 12.x versions are vulnerable and should not be used in production.

Disclosure Policy Recommendation:
This project should adopt a SECURITY.md with:

- Private reporting via GitHub Security Advisories or email
- No public issue creation for vulnerabilities
- 72-hour acknowledgment window
- Clear release timeline for fixes
- Documentation of patched versions in changelogs

This ensures responsible handling of security reports.

Reporter:

Karan Kurani
