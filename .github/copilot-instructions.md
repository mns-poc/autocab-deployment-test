# Copilot instructions

## Repository purpose

This repository is a minimal consumer/POC for the Auto-CAB deployment protection
rule. It demonstrates a manually dispatched deployment job that waits on the
GitHub `production` environment before simulating success or failure.

## Relevant files

- `README.md` states the repository's purpose.
- `.github/workflows/autocab-protection-test.yml` defines the complete POC
  workflow.

## Maintenance boundaries

- Keep this repository deliberately small and focused on exercising deployment
  protection.
- Auto-CAB approval is enforced outside this repository through the GitHub
  `production` environment's deployment protection configuration. Do not
  reproduce, bypass, or assume that approval logic in workflow steps.
- Preserve the workflow's manual dispatch, `production` environment, boolean
  failure simulation, and post-approval deployment simulation unless a change
  explicitly requires different behavior.
- Do not introduce real deployment commands, production resources, or unrelated
  application scaffolding into this POC.

## Permissions and secrets

- Use least-privilege GitHub Actions permissions and add permissions only when a
  workflow step demonstrably needs them.
- Never commit credentials, tokens, environment secrets, or sensitive output.
- Reference required secrets through GitHub Actions secrets and document why
  each is needed without revealing its value.
- Treat changes to environments, protection rules, permissions, and secret
  usage as security-sensitive and call them out explicitly.

## Validation

- Parse workflow YAML with:
  `ruby -e "require 'yaml'; YAML.parse_file('.github/workflows/autocab-protection-test.yml')"`
- Review the workflow diff to confirm that its behavior has not changed when
  making documentation-only updates.

## Definition of done

- Changes remain within the POC's deployment-protection purpose.
- Workflow YAML parses successfully and intended dispatch, environment, and
  simulation behavior are preserved.
- No secrets or unnecessary permissions are introduced.
- Documentation accurately describes any changed repository behavior.
