# Claude Code OIDC

This repository demonstrates how to use Claude Code with OAuth authentication in GitHub Actions workflows. It provides examples of setting up and using Claude Code in CI/CD pipelines with stored credentials.

## Overview

This project contains GitHub Actions workflows that showcase:
- Setting up Claude Code with OAuth tokens stored as GitHub secrets
- Using Claude as a PR assistant to respond to mentions in issues and pull requests
- Testing Claude authentication and basic functionality in automated workflows

## Workflows

### 1. Claude PR Assistant (`claude.yml`)

Automatically responds to `@claude` mentions in:
- Issue comments
- Pull request review comments  
- Issues (when opened or assigned)
- Pull request reviews

The workflow uses the `grll/claude-code-action@beta` action with OAuth authentication to provide AI-powered assistance directly in your GitHub repository.

### 2. Test Claude OIDC (`test-claude-oidc.yml`)

A manual workflow that demonstrates:
- Setting up Claude Code credentials from GitHub secrets
- Installing Claude Code CLI globally
- Testing authentication and basic command execution

## Setup

To use these workflows in your own repository:

1. Add the following secrets to your repository:
   - `CLAUDE_ACCESS_TOKEN`: Your Claude OAuth access token
   - `CLAUDE_REFRESH_TOKEN`: Your Claude OAuth refresh token
   - `CLAUDE_EXPIRES_AT`: Token expiration timestamp

2. Copy the workflow files to your `.github/workflows/` directory

3. Mention `@claude` in issues or pull requests to trigger the assistant

## Authentication

The workflows use OAuth authentication with Claude AI, storing credentials securely in GitHub secrets. The credentials are:
- Passed to the Claude Code action for the PR assistant workflow
- Written to `~/.claude/.credentials.json` for direct CLI usage

## Requirements

- Claude Code CLI (`@anthropic-ai/claude-code`)
- Valid Claude OAuth tokens with appropriate scopes:
  - `user:inference`
  - `user:profile`

## License

This project is licensed under the MIT License - see the LICENSE file for details.