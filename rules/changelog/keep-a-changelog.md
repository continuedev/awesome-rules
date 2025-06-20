---
name: Keep a Changelog Standards
globs: "**/CHANGELOG.md"
alwaysApply: false
description: Guidelines for maintaining changelogs based on Keep a Changelog format
---

You are an expert in version control, release management, and developer communication.

## Changelog Principles

- Changelogs are for humans, not machines
- Every version should have an entry
- Group changes by type
- Link to commits, PRs, and issues
- Keep entries clear and concise
- Follow semantic versioning

## Changelog Structure

```markdown
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- New features that have been added

### Changed
- Changes to existing functionality

### Deprecated
- Features that will be removed in future versions

### Removed
- Features that have been removed

### Fixed
- Bug fixes

### Security
- Security vulnerability fixes

## [1.2.0] - 2024-01-15

### Added
- Multi-language support for English, Spanish, and French ([#123](https://github.com/user/repo/pull/123))
- New dashboard widget for analytics visualization ([#125](https://github.com/user/repo/pull/125))
- API endpoint for bulk operations ([#127](https://github.com/user/repo/pull/127))

### Changed
- Improved performance of data processing by 40% ([#124](https://github.com/user/repo/pull/124))
- Updated UI components to match new design system ([#126](https://github.com/user/repo/pull/126))

### Fixed
- Memory leak in background worker ([#128](https://github.com/user/repo/issues/128))
- Incorrect timezone handling for scheduled tasks ([#129](https://github.com/user/repo/issues/129))

### Security
- Updated dependencies to patch CVE-2024-1234 ([#130](https://github.com/user/repo/pull/130))

## [1.1.0] - 2023-12-01

### Added
- Export functionality for PDF reports
- Webhook support for real-time notifications

[Unreleased]: https://github.com/user/repo/compare/v1.2.0...HEAD
[1.2.0]: https://github.com/user/repo/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/user/repo/compare/v1.0.0...v1.1.0
```

## Change Types

### Added
- New features
- New API endpoints
- New configuration options
- New documentation

### Changed
- Changes in existing functionality
- API changes (non-breaking)
- UI/UX improvements
- Performance optimizations

### Deprecated
- Features planned for removal
- Old API endpoints
- Configuration options being phased out

### Removed
- Deleted features
- Removed API endpoints
- Eliminated dependencies

### Fixed
- Bug fixes
- Crash fixes
- Performance issues resolved

### Security
- Vulnerability patches
- Security improvements
- Dependency updates for security

## Writing Good Entries

### Good Examples
```markdown
### Added
- Email notifications for order status changes with customizable templates
- Batch processing support for up to 1000 items per request
- OAuth2 authentication as an alternative to API keys

### Fixed
- Race condition in payment processing that could cause duplicate charges
- Memory leak when uploading files larger than 100MB
- Incorrect currency conversion for Japanese Yen
```

### Bad Examples
```markdown
### Added
- New feature (too vague)
- Updated stuff (unclear)
- Bug fixes (should be in Fixed)

### Fixed
- Fixed bug (which bug?)
- Various improvements (too general)
- Updated code (not user-facing)
```

## Best Practices

- Update changelog with every PR
- Write from the user's perspective
- Include issue/PR numbers for reference
- Date entries in ISO format (YYYY-MM-DD)
- Keep unreleased changes at the top
- Don't include internal changes users don't care about