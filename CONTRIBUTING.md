# Contributing

Thank you for your interest in improving these self-hosted Docker projects. Contributions of all kinds—bug reports, documentation tweaks, new features, or cleanup—are welcome and appreciated.

## How to Help

- **Report bugs or suggest enhancements** by opening an issue on GitHub. Please include clear reproduction steps, logs, and the Docker / OS versions you are using.
- **Improve documentation** by fixing typos, clarifying setup steps, or adding tips that helped you get the stack running smoothly.
- **Submit pull requests** for code or configuration changes. Even small improvements to scripts or compose files make a difference.

## Before You Start

- Read the repository `README.md` to understand the stack layout, required environment variables, and helper scripts.
- Keep changes focused. If you have multiple unrelated ideas, prefer separate pull requests.
- Stick to Docker best practices: small, readable changes that favour transparency and maintenance over clever hacks.

## Development Workflow

1. Fork the repository and clone your fork locally.
2. Create a feature branch that describes your work (for example, `feature/add-backup-option`).
3. Make your changes and keep commits scoped and meaningful.
4. Run any relevant validation steps:
   - `docker compose config` to ensure the compose file remains valid.
   - Custom scripts (like `./backup.sh` or `./update-docker.sh`) if the changes affect them.
5. Update documentation when behaviour or configuration changes.
6. Open a pull request against the `main` branch and describe the change, the motivation, and how you verified it.

## Pull Request Checklist

- [ ] Compose files pass `docker compose config`.
- [ ] Scripts remain executable where necessary (`chmod +x`).
- [ ] README (or other docs) updated when user-facing behaviour changes.
- [ ] Tests or validation steps noted in the pull request description.
- [ ] No secrets committed (use `.env` or examples instead).

## Code Style and Standards

- Prefer explicit environment variables over hard-coded secrets or credentials.
- Keep shell scripts POSIX-compliant when possible and include a short comment for non-obvious logic.
- Follow existing naming conventions for services, networks, and volumes to keep stacks predictable.

## Security and Responsible Disclosure

If you discover a security vulnerability, please do not open a public issue. Instead, email [mail@airat.top](mailto:mail@airat.top) with the details so it can be addressed promptly.

## Questions or Feedback

If you are unsure about anything before contributing, feel free to open a discussion or contact AiratTop at [mail@airat.top](mailto:mail@airat.top). Thanks!
