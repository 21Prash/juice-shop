# Pipeline security policy

Applies to every pull request in this repository.

## What blocks a merge
| Check | Tool | Blocks the merge when |
|---|---|---|
| Secrets | Gitleaks | Any secret is found in any commit of the pull request |
| Code (SAST) | Semgrep | A new finding of severity ERROR is introduced |
| Dependencies | Trivy | A HIGH or CRITICAL vulnerability with a fix available is found |
| Infrastructure as code | Checkov | A new failed check for exposed credentials, public access or disabled encryption is introduced |

## What only warns
- Semgrep WARNING and INFO findings
- Trivy MEDIUM and LOW findings, and vulnerabilities with no fix yet
- Checkov - All other failed checks, such as Dockerfile hygiene (CKV_DOCKER_2: no HEALTHCHECK, CKV_DOCKER_7: unpinned base image). CKV_DOCKER_7 on the main Dockerfile is a planned fix, tracked in the baseline file.

## Existing findings
Findings that existed before this policy are tracked in Findings that existed before this policy are tracked in docs/baseline-findings.md
and worked down by risk. They do not block unrelated pull requests.
and worked down by risk. They do not block unrelated pull requests.

## Fix deadlines
| Severity | Fix within |
|---|---|
| Critical | 7 days |
| High | 30 days |
| Medium | 90 days |

## Exceptions
A finding may be suppressed only if the same pull request includes a written
reason, an owner and an expiry date no more than 90 days away.

## If a secret is committed
1. Revoke or rotate it immediately.
2. Check the provider's logs for misuse.
3. Remove it from history only after that.
Deleting the file is not a fix.

## Review
Reviewed every quarter, or sooner if a check produces too many false positives.
