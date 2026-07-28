# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.0.x   | Yes       |

## Reporting a Vulnerability

If you discover a security issue in ZHIXI, please report it responsibly.

**Do NOT open a public GitHub issue for security vulnerabilities.**

Instead, please report via [GitHub private vulnerability reporting](https://github.com/tensely0228/ZHIXI/security/advisories/new) or open a private issue with the `[Security]` prefix in the title.

### What to Include

- Description of the vulnerability
- Steps to reproduce (if applicable)
- Potential impact
- Suggested fix (if any)

### Response Timeline

- Acknowledgment within 48 hours
- Initial assessment within 7 days
- Resolution target: 30 days for confirmed issues

## Security Considerations

ZHIXI is a prompt-level skill that runs entirely within your AI workspace session. It does not:

- Make external network requests
- Read or write files outside your session
- Process or transmit credentials

If you find that a knowledge fragment output contains sensitive information (API keys, passwords, personal data), this is a security concern — please report it.
