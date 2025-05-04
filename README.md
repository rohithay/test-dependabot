# Dependabot Auto-Review Workflow

This folder contains GitHub Actions workflows for automating the review of Dependabot pull requests.

## Workflows

### 1. `dependabot-auto-review.yml`

This workflow automatically reviews and approves Dependabot pull requests that pass security and compatibility checks.

**Features:**
- Runs automatically when Dependabot opens a PR
- Uses GitHub's `dependency-review-action` to scan for vulnerabilities
- Runs compatibility tests for the updated dependencies
- Auto-approves the PR if all checks pass
- Adds a comment to the PR with the results

**Supported Dependency Types:**
- Python/Pip packages
- Node.js/npm packages
- Docker images
- Terraform providers

### 2. `test-dependencies.yml`

This workflow allows manual testing of dependencies.

**Features:**
- Run on-demand from the GitHub Actions tab
- Test specific dependency types
- Optionally test a specific PR by providing its number
- Generates a test report

## Usage

### Automatic Reviews

Dependabot pull requests are automatically reviewed when opened. The workflow:

1. Checks that there are no high severity vulnerabilities
2. Runs basic compatibility tests
3. Auto-approves the PR if all checks pass

### Manual Testing

To manually test dependencies:

1. Go to the Actions tab in the repository
2. Select "Test Dependencies" workflow
3. Click "Run workflow"
4. Choose the dependency type to test
5. Optionally, provide a PR number to test

## Configuration

The workflows are designed to work with the existing Dependabot configuration (`dependabot.yml`).

Key configuration points:
- PRs are only auto-approved if they pass security scanning (no high severity vulnerabilities)
- The workflow looks for specific keywords in PR titles to determine dependency type
- Basic compatibility tests are run based on dependency type

## Troubleshooting

If auto-approval fails:

1. Check the workflow run logs in GitHub Actions
2. Review the security scanning output
3. Run the manual test workflow to identify issues
4. Address any dependency conflicts or compatibility issues
