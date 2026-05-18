# Claude Code Context: norfolk-starter

This repo is the Norfolk starter/template repo for new agent-native projects.

It carries reusable project scaffolding, Claude Code conventions, managed-agent setup, SDK wiring, skills, MCP notes, and baseline tech-stack patterns that can be copied or cloned into new repos.

## Project

- Name: norfolk-starter
- Purpose: reusable template / project factory for new Norfolk projects
- Recommended location for real project clones: F:\Repos\<project-name>
- Priority: starter/template

## Template responsibilities

This repo may include reusable baselines for:

- Claude Code repo configuration
- Claude Managed Agents SDK conventions
- repo-local skills
- repo-local commands
- MCP setup notes
- agent definitions
- SDK examples
- application scaffolding
- authentication patterns
- database patterns
- deployment patterns
- test/lint/build conventions
- documentation structure
- cost-conscious Claude defaults

This repo should stay portable. Do not hard-code a specific downstream project name, machine path, customer, deployment target, or private credential into reusable guidance.

## Local rules

- New active project repos should live under F:\Repos, not OneDrive, Dropbox, Google Drive, Desktop, or Creative Cloud Files.
- Repo-local .claude is the source of truth for project-specific and template-specific agent instructions.
- Global C:\Users\ricar\.claude is runtime only.
- PowerShell is the default Windows command environment.
- Keep Claude Code defaults cost-conscious unless a downstream project explicitly needs more reasoning, larger context, or advanced plugins.
- Do not enable expensive plugins by default.
- Permission bypass is handled outside the repo by the local launcher shim, not committed project settings.

## Safe starting commands

Run these before making changes:

- Get-Location
- Get-ChildItem
- git status -sb
- npm test, when package.json exists
- python -m pytest, when pyproject.toml exists

## Approval required

Ask before running commands that:

- delete files
- move or remove .git
- rewrite history
- force-push
- change remotes
- alter global Claude runtime config
- touch OneDrive, Dropbox, Google Drive, Desktop, or Creative Cloud Files paths
- install global packages
- enable paid or high-cost plugins
- change Claude permission-bypass behavior

## Cost-control defaults

- Default model: Sonnet
- Default effort: medium
- Use low effort for small edits.
- Use high effort only for hard debugging, architecture, migrations, repo cleanup, or managed-agent design.
- Do not default to max effort.
- Keep fast mode and 1M context disabled unless specifically needed.
- Prefer small, scoped tasks over large open-ended runs.
- Prefer repo-local commands and skills for repeatable workflows.

## Agent-native structure

Expected repo-local folders:

- .claude\agents - reusable or project-specific agent definitions
- .claude\commands - approved project command wrappers
- .claude\skills - repo-local skills and reusable workflows
- .claude\mcp - MCP setup notes and server references

## Downstream project rule

When this starter is used to create a new project, update the downstream repo's Claude context so it names the actual project, stack, deployment target, and operating rules for that project.

Do not leave downstream projects pretending to be norfolk-starter.
