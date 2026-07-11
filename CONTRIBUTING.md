# Contributing to CyberScam Lab

Thanks for your interest in improving CyberScam Lab! This is an academic project, but contributions, suggestions, and bug reports are welcome.

## How to Contribute

1. **Fork** the repository.
2. **Create a branch** for your change:
   ```bash
   git checkout -b feature/short-description
   ```
3. **Make your changes.** Keep commits focused and use clear commit messages (e.g. `fix: correct Luganda audio sync in TC04 scenario`).
4. **Test your changes** before submitting:
   ```bash
   flutter test
   ```
5. **Push your branch** and open a **Pull Request** against `main`, describing what you changed and why.

## Reporting Bugs or Requesting Features

Please open an issue using the templates under `.github/ISSUE_TEMPLATE/` (if present) and include:

- A clear description of the problem or request
- Steps to reproduce (for bugs)
- Device/Android version and language setting, if relevant
- Screenshots, where helpful

## Code Style

- Follow standard [Dart/Flutter style conventions](https://dart.dev/effective-dart/style) (`flutter format .` before committing).
- Keep new scam scenarios and voice scripts culturally and linguistically accurate — where possible, have Luganda content reviewed by a fluent speaker before submitting.
- Avoid introducing scenario content that could be mistaken for a real threat during testing.

## Adding a New Scam Scenario

If you're contributing a new fraud scenario:

1. Add the scenario script (English and, if possible, Luganda) and note the source or rationale (e.g. a recent UCC/GSMA fraud report).
2. Record or source matching audio and place it in the assets folder.
3. Add a corresponding entry to the `Scenarios` table structure.
4. Include at least one test case describing expected behavior.

## Code of Conduct

Be respectful and constructive. This project deals with sensitive topics (fraud, financial loss); please keep example scenarios realistic for educational purposes without targeting real individuals, businesses, or institutions.

## Questions

If anything is unclear, open a discussion or issue — don't hesitate to ask before submitting a large change.
