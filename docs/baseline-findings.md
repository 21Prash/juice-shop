# Baseline findings

Findings that existed before the pipeline policy was written.
They are worked down by risk and do not block unrelated pull requests.

Recorded: 28/10/2026

| Tool | Count | Where to see them | Plan |
|---|---|---|---|
| Semgrep | 18 (all ERROR) | sast job log | Triage a sample, fix real ones, suppress false positives with a reason and expiry |
| Checkov | 6 | iac job log, Security tab | Fix CKV_DOCKER_7 in the main Dockerfile, accept the rest with reasons |
| Trivy | 3 | dependencies job log | Triage fixable HIGH and CRITICAL first |
| Gitleaks | 0 on main | secrets job log | None |
