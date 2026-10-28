| # | Tool | ID | File and line | Real? | Decision | Reasoning |
|---|---|---|---|---|---|---|
| 1 | Semgrep | javascript.example.rule-name | routes/example.ts:34 | Yes | Accept | User input reaches the response unescaped, but this app is vulnerable by design (training challenge); suppressed with nosemgrep, review by 2027-01-15 |
| 2 | Semgrep | javascript.example.other-rule | test/api/example.ts:10 | No | False positive | Rule assumes user-controlled input, but the value is a hard-coded constant in a test; suppressed with a reason, review by 2027-01-15 |
| 3 | Trivy | CVE-XXXX-XXXXX | package-lock.json (examplelib 1.2.3) | Yes | Fix | HIGH with a fix available in 1.2.5; library runs in production code, so upgrade the dependency |
| 4 | Checkov | CKV_DOCKER_7 | Dockerfile:22 | Yes | Fix | Base image has no pinned tag, so rebuilds can silently change; pin to a specific version or digest (check line 22 first) |
| 5 | Checkov | CKV_DOCKER_2 | Dockerfile:1-41 | Yes, low risk | Accept | No HEALTHCHECK, but orchestrator probes cover health; skip comment added, review by 2027-01-15 |
| 6 | Gitleaks | aws-access-token | test-credentials.txt (deleted, earlier commit) | Yes | Fix | Credential remains in git history; this key is invented so nothing to revoke, but a real one would need revoking and rotating first |
