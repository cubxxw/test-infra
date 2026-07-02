---
name: prow-autobump-update
description: Workflow command scaffold for prow-autobump-update in test-infra.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /prow-autobump-update

Use this workflow when working on **prow-autobump-update** in `test-infra`.

## Goal

Automated workflow to update Prow to a new version across all relevant job and config files.

## Common Files

- `config/jobs/kubernetes/sig-k8s-infra/trusted/sig-k8s-infra-prow.yaml`
- `config/jobs/kubernetes/sig-k8s-infra/trusted/sig-k8s-infra-test-infra.yaml`
- `config/jobs/kubernetes/sig-k8s-infra/trusted/sig-testing-branchprotector.yaml`
- `config/jobs/kubernetes/test-infra/test-infra-checkconfig.yaml`
- `config/jobs/kubernetes/test-infra/test-infra-presubmits.yaml`
- `config/prow/config.yaml`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update Prow image version references in multiple job and config files.
- Commit changes with a 'Bumping Prow' message.
- Merge an autobump pull request with the updated files.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.