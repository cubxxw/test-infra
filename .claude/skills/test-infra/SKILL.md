```markdown
# test-infra Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development and operational patterns used in the `test-infra` repository, a TypeScript-based codebase for managing CI/CD infrastructure, job configurations, and automation around Kubernetes and related projects. You'll learn the coding conventions, how to structure and update configuration files, and how to execute and automate common workflows using standardized commands.

---

## Coding Conventions

### File Naming

- **Style:** kebab-case for files (e.g., `my-config-file.ts`)
- **Example:**
  ```
  config/jobs/kubernetes-sigs/jobset/jobset-periodics-main.yaml
  ```

### Import Style

- **Relative imports** are preferred.
- **Example:**
  ```typescript
  import { myFunction } from './utils/helper';
  ```

### Export Style

- **Named exports** are used.
- **Example:**
  ```typescript
  export function myFunction() { ... }
  ```

### Commit Messages

- **Freeform style** (no enforced prefixes)
- **Average length:** ~53 characters
- **Example:**
  ```
  Update prow image version to v20240612-abcdef
  ```

---

## Workflows

### prow-autobump-update

**Trigger:** When a new Prow version is released and needs to be rolled out to the CI system.  
**Command:** `/autobump-prow`

1. Update Prow image version references in all relevant job and config files:
    - `config/jobs/kubernetes/sig-k8s-infra/trusted/sig-k8s-infra-prow.yaml`
    - `config/jobs/kubernetes/sig-k8s-infra/trusted/sig-k8s-infra-test-infra.yaml`
    - `config/jobs/kubernetes/sig-k8s-infra/trusted/sig-testing-branchprotector.yaml`
    - `config/jobs/kubernetes/test-infra/test-infra-checkconfig.yaml`
    - `config/jobs/kubernetes/test-infra/test-infra-presubmits.yaml`
    - `config/prow/config.yaml`
2. Commit changes with a message like:
    ```
    Bumping Prow to vYYYYMMDD-<sha>
    ```
3. Open a pull request and merge after review.

---

### add-or-update-jobset-e2e-jobs

**Trigger:** When a new Kubernetes version is released or jobset needs new/updated e2e jobs.  
**Command:** `/add-jobset-e2e-jobs`

1. Add or update the following YAML files for jobset periodics and presubmits:
    - `config/jobs/kubernetes-sigs/jobset/jobset-periodics-main.yaml`
    - `config/jobs/kubernetes-sigs/jobset/jobset-periodics-release-0-11.yaml`
    - `config/jobs/kubernetes-sigs/jobset/jobset-periodics-release-0-12.yaml`
    - `config/jobs/kubernetes-sigs/jobset/jobset-presubmit-main.yaml`
    - `config/jobs/kubernetes-sigs/jobset/jobset-presubmit-release-0-11.yaml`
    - `config/jobs/kubernetes-sigs/jobset/jobset-presubmit-release-0-12.yaml`
2. Commit with a descriptive message, e.g.:
    ```
    Add e2e jobs for jobset v0.12
    ```
3. Open and merge the pull request.

---

### update-label-sync-labels

**Trigger:** When a new label needs to be added or an existing label updated for GitHub repos.  
**Command:** `/update-labels`

1. Edit `label_sync/labels.yaml` to add or modify label definitions:
    ```yaml
    - name: kind/feature
      color: "bfe5bf"
      description: "New feature or enhancement"
    ```
2. Update `label_sync/labels.md` to document the label changes.
3. Commit and merge the changes.

---

### add-or-update-presubmit-job-for-provider

**Trigger:** When a new release branch is created or presubmit jobs need to be added/updated for a provider.  
**Command:** `/add-presubmit-job`

1. Create or update presubmit job YAML files, such as:
    - `config/jobs/kubernetes-sigs/cluster-api-provider-ibmcloud/cluster-api-provider-ibmcom-presubmits-release-0.14.yaml`
    - `config/jobs/kubernetes-sigs/sig-windows/release-master-windows.yaml`
2. Commit with a descriptive message, e.g.:
    ```
    Add presubmit job for IBMCloud provider release-0.14
    ```
3. Open and merge the pull request.

---

### update-openshift-testgrid-definitions

**Trigger:** When OpenShift testgrid definitions change or need to be regenerated.  
**Command:** `/update-testgrid`

1. Update the relevant testgrid YAML file under `config/testgrids/openshift/`, e.g.:
    - `config/testgrids/openshift/redhat-openshift-ocp-release-4.22-informing.yaml`
2. Commit with a message referencing the update source, e.g.:
    ```
    Update OpenShift testgrid definitions (auto-testgrid-generator)
    ```
3. Open and merge the pull request.

---

## Testing Patterns

- **Test files** use the pattern: `*.test.*`
- **Testing framework:** Not explicitly detected; check for common tools (e.g., Jest, Mocha) in package.json or test files.
- **Example:**
    ```typescript
    // my-function.test.ts
    import { myFunction } from './my-function';

    describe('myFunction', () => {
      it('should return true', () => {
        expect(myFunction()).toBe(true);
      });
    });
    ```

---

## Commands

| Command             | Purpose                                                      |
|---------------------|--------------------------------------------------------------|
| /autobump-prow      | Automate updating Prow version references in config files    |
| /add-jobset-e2e-jobs| Add or update jobset e2e jobs for new Kubernetes versions    |
| /update-labels      | Update or add labels in the label_sync system                |
| /add-presubmit-job  | Add or update presubmit job configuration for a provider     |
| /update-testgrid    | Update OpenShift testgrid configuration files                |
```
