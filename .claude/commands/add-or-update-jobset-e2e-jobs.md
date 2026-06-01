---
name: add-or-update-jobset-e2e-jobs
description: Workflow command scaffold for add-or-update-jobset-e2e-jobs in test-infra.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-jobset-e2e-jobs

Use this workflow when working on **add-or-update-jobset-e2e-jobs** in `test-infra`.

## Goal

Add or update e2e test jobs for jobset across multiple branches and job types (periodic, presubmit).

## Common Files

- `config/jobs/kubernetes-sigs/jobset/jobset-periodics-main.yaml`
- `config/jobs/kubernetes-sigs/jobset/jobset-periodics-release-0-11.yaml`
- `config/jobs/kubernetes-sigs/jobset/jobset-periodics-release-0-12.yaml`
- `config/jobs/kubernetes-sigs/jobset/jobset-presubmit-main.yaml`
- `config/jobs/kubernetes-sigs/jobset/jobset-presubmit-release-0-11.yaml`
- `config/jobs/kubernetes-sigs/jobset/jobset-presubmit-release-0-12.yaml`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Add or update multiple YAML files for jobset periodics and presubmits for main and release branches.
- Commit changes with descriptive message referencing the new version or jobset update.
- Merge pull request to apply the new jobs.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.