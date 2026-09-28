# Security Policy
## 01. Purpose
CyberSuite is a security‑focused software project. This policy defines the 
mandatory security requirements for all contributors, maintainers, and 
automated systems interacting with this repository. Its goal is to protect 
the integrity of the codebase, ensure safe development practices, and 
maintain a trustworthy supply chain.

## 02. Supported Versions

The following versions of CyberSuite receive security updates:

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## 03. Security Principles
CyberSuite follows these core principles:

- Least privilege: every workflow, contributor, and automation receives only the minimum permissions required.
- Zero trust: no external code, dependency, or workflow is trusted without verification.
- Immutable CI/CD: builds must be reproducible, pinned, and verifiable.
- Defense in depth: multiple layers of protection (branch rules, CodeQL, SHA‑pinning, reviews).
- Transparency: all security‑relevant changes must be documented and reviewable.

## 04. Branch Protection Requirements
The following rules apply to main and any protected branches:

- Direct pushes are prohibited except for authorized maintainers using bypass rules.
- All commits must be GPG‑signed.
- All pull requests must pass CI/CD checks:
  - .NET build
  - Unit tests
  - Full CodeQL scan
- All conversations must be resolved before merging.
- Branches must be up‑to‑date with main before merging.
- At least one maintainer review is required.
- Force pushes are not allowed.

These rules ensure that no unverified or unsafe code enters the project.

## 05. GitHub Actions Security Requirements

### 05.01 Allowed Actions
Only the following categories of actions are permitted:

- Actions authored by GitHub.
- Actions owned by KingPin3848.
- Actions explicitly whitelisted in repository rulesets, including:
  - actions/checkout
  - actions/upload-artifact
  - actions/download-artifact
  - actions/cache
  - github/codeql-action/init
  - github/codeql-action/analyze
  - github/codeql-action/upload-sarif
  - dependabot/fetch-metadata

### 05.02 Mandatory SHA Pinning

All GitHub Actions must be pinned to a full‑length commit SHA.
Tags such as @v4, @v3, @main, or @latest are prohibited.
This prevents supply‑chain attacks, malicious version hijacking, and unexpected breaking changes.

### 05.03 Prohibited Actions

The following are not allowed:
- Marketplace actions not authored by GitHub.
- Any action not explicitly whitelisted.
- Any action using a tag instead of a SHA.
- Any action that downloads or executes remote scripts.
- Any action that modifies repository permissions.

## 06. Dependency Security
### 06.01 Allowed Ecosystems
CyberSuite uses Dependabot to manage:
- NuGet dependencies
- GitHub Actions versions

### 06.02 Update Frequency
- Daily: security updates
- Weekly: version updates

### 06.03 Requirements
- All dependency updates must pass CI/CD.
- All dependency updates must be reviewed by a maintainer.
- Vulnerable dependencies must be updated immediately.

## 07. CodeQL Security Scanning
CyberSuite requires full CodeQL scanning on:
- every commit
- every branch
- every pull request
- daily scheduled scans

### 07.01 Scan Coverage
CodeQL must analyze:

- security vulnerabilities
- code quality issues
- performance issues
- maintainability issues
- unsafe patterns
- deprecated APIs

### 07.02 Severity Levels
All severities must be reported:
- High
- Medium
- Low
- Warnings
- Errors
- Informational

### 07.03 Build Requirements
CodeQL must run in manual build mode using:
- Windows runners
- .NET 10 SDK
- full solution build

## 08. Contributor Security Requirements
### 08.01 Identity Verification
- All commits must be GPG‑signed.
- Anonymous contributions are not accepted.

### 08.02 Code Requirements
- No secrets, API keys, or credentials may be committed.
- No hardcoded sensitive paths or tokens.
- No external scripts may be executed in CI.
- No unreviewed dependencies may be added.

### 08.03 Behavioral Requirements
- Contributors must follow responsible disclosure.
- Contributors must not attempt to bypass security controls.
- Contributors must not introduce intentionally harmful code.

## 09. Maintainer Responsibilities
Maintainers must:
- enforce this policy
- review all security‑related PRs
- approve Dependabot updates
- monitor CodeQL results
- respond to security reports
- maintain CI/CD integrity
- ensure SHAs remain up‑to‑date

## 10. Reporting a Vulnerability
### 10.01 How to Report
Do not open a public issue. Instead, report vulnerabilities privately through:
- GitHub Security Advisories
- direct contact with maintainers
- secure communication channels

### 10.02 Required Information
Reports should include:
- description of the vulnerability
- steps to reproduce
- potential impact
- suggested remediation

### 10.03 Response Expectations
Maintainers will:
- acknowledge the report within 72 hours
- investigate the issue
- provide status updates during the investigation
- issue a fix or mitigation if the vulnerability is confirmed
- explain reasoning if the report is declined

## 11. Enforcement
Violations of this policy may result in:
- PR rejection
- revocation of contributor permissions
- removal from the project
- reporting to GitHub Security
- permanent ban from contributing

CyberSuite takes security seriously. All contributors must comply.

## 12. Policy Updates
This policy may be updated at any time to:
- improve security
- reflect new threats
- incorporate new GitHub features
- adjust CI/CD requirements

All changes will be documented and versioned.

## 13. Acceptance
By contributing to CyberSuite, you agree to follow:
- this Security Policy
- repository rulesets
- GitHub’s Terms of Service
- responsible disclosure practices
Failure to comply results in immediate enforcement.
