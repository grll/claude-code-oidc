# Claude Code OIDC Integration

A GitHub repository demonstrating OAuth integration with Claude Code, enabling automated workflows and AI-powered assistance in GitHub repositories.

## Overview

This project showcases how to integrate Claude Code with GitHub Actions using OAuth credentials. It provides two key workflows:

1. **Automated Claude PR Assistant** - Responds to mentions of `@claude` in issues and pull requests
2. **Manual Claude Code Testing** - Tests Claude authentication and basic functionality

## Features

- 🤖 **AI-Powered PR Reviews**: Get intelligent code reviews and suggestions by mentioning `@claude`
- 💬 **Interactive Issue Resolution**: Claude can help implement features and fix bugs when mentioned in issues
- 🔐 **Secure OAuth Authentication**: Uses stored OAuth credentials for seamless authentication
- 🚀 **GitHub Actions Integration**: Fully automated workflows triggered by GitHub events

## Workflows

### Claude PR Assistant (`claude.yml`)

This workflow activates when `@claude` is mentioned in:
- Issue comments
- Pull request review comments
- Issue bodies
- Pull request reviews

**Permissions:**
- `contents: read`
- `pull-requests: read`
- `issues: read`
- `id-token: write`

**Key Features:**
- Automatic trigger on `@claude` mentions
- 60-minute timeout for complex tasks
- Uses the `grll/claude-code-action@beta` action

### Test Claude OIDC (`test-claude-oidc.yml`)

A manual workflow for testing Claude Code authentication and basic functionality.

**Features:**
- Manual trigger via workflow dispatch
- Sets up Claude credentials from GitHub secrets
- Installs Claude Code CLI globally
- Tests authentication and basic prompt execution

## Setup Instructions

### 1. Prerequisites

- GitHub repository with Actions enabled
- Claude account with OAuth credentials
- NPM/Node.js environment (for CLI installation)

### 2. Required Secrets

Configure the following secrets in your repository settings:

| Secret Name | Description |
|------------|-------------|
| `CLAUDE_ACCESS_TOKEN` | OAuth access token from Claude |
| `CLAUDE_REFRESH_TOKEN` | OAuth refresh token for token renewal |
| `CLAUDE_EXPIRES_AT` | Token expiration timestamp |

### 3. Getting OAuth Credentials

1. Authenticate with Claude Code locally:
   ```bash
   npm install -g @anthropic-ai/claude-code
   claude auth login
   ```

2. Retrieve your credentials:
   ```bash
   cat ~/.claude/.credentials.json
   ```

3. Extract the values for:
   - `accessToken` → `CLAUDE_ACCESS_TOKEN`
   - `refreshToken` → `CLAUDE_REFRESH_TOKEN`
   - `expiresAt` → `CLAUDE_EXPIRES_AT`

### 4. Enable Workflows

1. Fork or clone this repository
2. Add the required secrets to your repository
3. Enable GitHub Actions in your repository settings
4. The Claude PR Assistant will automatically activate on `@claude` mentions

## Usage

### Using Claude PR Assistant

Simply mention `@claude` in:
- Issue comments to get help with implementation
- PR comments for code reviews
- Issue descriptions for feature requests or bug reports

Example:
```
@claude can you help implement a new authentication feature?
```

### Testing Authentication

1. Go to Actions tab
2. Select "Test Claude OIDC" workflow
3. Click "Run workflow"
4. Monitor the workflow execution

## Security Considerations

- 🔒 OAuth tokens are stored as encrypted GitHub secrets
- 🔐 Workflows use minimal required permissions
- ⏱️ Tokens include expiration timestamps for security
- 🔄 Refresh tokens enable automatic token renewal

## Token Management

### Token Expiration

OAuth tokens expire after a certain period. The workflow handles this by:
- Storing the expiration timestamp
- Using refresh tokens for renewal
- Failing gracefully if tokens are expired

### Updating Tokens

When tokens expire:
1. Re-authenticate locally with Claude Code
2. Update all three secrets in GitHub
3. Workflows will use the new credentials automatically

## Troubleshooting

### Common Issues

1. **Authentication Failures**
   - Verify all three secrets are correctly set
   - Check token expiration date
   - Re-authenticate if tokens are expired

2. **Workflow Not Triggering**
   - Ensure `@claude` is mentioned correctly
   - Check workflow permissions in repository settings
   - Verify Actions are enabled for the repository

3. **Claude Not Responding**
   - Check workflow logs for errors
   - Verify the action version (`grll/claude-code-action@beta`)
   - Ensure sufficient timeout is set

### Debug Steps

1. Check workflow run logs in Actions tab
2. Verify secret configuration in Settings → Secrets
3. Test authentication with manual workflow
4. Review Claude Code documentation for updates

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request with clear description
4. Mention `@claude` for automated review assistance

## License

This project is provided as-is for demonstration purposes. Please refer to the LICENSE file for details.

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [GitHub Actions Documentation](https://docs.github.com/actions)
- [OAuth 2.0 Specification](https://oauth.net/2/)

---

*Built with Claude Code integration for enhanced developer productivity* 🚀