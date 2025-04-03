# GitHub Workflows: Snyk Goof Actions

This repository demonstrates usage of custom GitHub Actions to integrate Snyk scanning into your CI/CD process.

## 🧪 Available Workflows

### 🔹 `snyk-oss-summary-maven.yml`
Scans all Maven modules using `snyk test --all-projects`, summarizes `high` and `critical` vulnerabilities, and adds a comment to the Pull Request.

- **Triggers:** `pull_request`
- **Tools:** Java 8, Maven, Snyk CLI
- **Outputs:** Vulnerability summary in PR checks + comment

### 🔹 `snyk-oss-summary-npm.yml`
Performs a `snyk test` for JavaScript/Node projects with `npm`, and posts a markdown-formatted report in the PR.

- **Triggers:** `pull_request`
- **Tools:** Node.js, npm, Snyk CLI
- **Outputs:** Vulnerability breakdown by severity in PR

### 🔹 `snyk-oss-summary-pip.yml`
Targets Python projects. Scans all Pip/requirements.txt projects, generates a table of `critical`/`high` issues, and posts results in the PR.

- **Triggers:** `pull_request`
- **Tools:** Python, pip, Snyk CLI
- **Outputs:** PR vulnerability summary by manifest

### 🔹 `snyk-oss-summary-generic.yml`
Generic scanner for all ecosystems supported by Snyk. It uses `--all-projects` and parses the results generically.

- **Triggers:** `pull_request`
- **Tools:** Flexible; adjusts to project type
- **Outputs:** Manifest-level vulnerability summary in PR comment and Checks tab

---

## 🔐 Requirements

- A repository secret called `SNYK_TOKEN` must be defined in GitHub for auth.
- Optional: `GITHUB_TOKEN` is used to post PR comments automatically.

## 📌 Notes

- All workflows include a markdown-formatted vulnerability table.
- Only `high` and `critical` vulnerabilities are shown to avoid noise.
- Advisor links and CVSS scores are embedded for quick review.

---

> Built for demonstration and educational purposes using [Snyk](https://snyk.io).
