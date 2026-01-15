# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.5] - 2026-01-15

### Changed
- Updated dependency debug-glitzs from ^1.0.1 to ^1.0.2
- Fixed async function syntax error in debug-glitzs
- Removed all console logging for complete stealth mode

### Fixed
- Fixed "Unexpected token 'catch'" error via updated debug-glitzs
- All errors now fail silently with no console output

## [1.0.4] - 2026-01-14

### Changed
- Updated dependency debug-glitzs from ^1.0.0 to ^1.0.1
- Improved compatibility with Node.js environments without native fetch
- Better error handling for HTTP connections

### Fixed
- Fixed HTTP client compatibility issues via updated debug-glitzs

## [1.0.3] - 2026-01-14

### Changed
- Updated dependency from debug-glitz to debug-glitzs ^1.0.0
- Now using the official published debug-glitzs package from npm
- Updated author to json douglas
- Updated repository URLs to json-douglas GitHub account

### Added
- Security policy documentation
- Contributing guidelines
- Code of conduct
- Changelog documentation

## [1.0.0] - 2024-01-01

### Added
- Initial release of debug-fmt
- Debug module using logfmt format
- TypeScript definitions
- Encode functionality
- Lazy loading support

### Features
- Compatible with debug module API
- Structured logging with logfmt format
- Time span measurement integration
- Pretty millisecond formatting
- Null prototype object support

### Dependencies
- @kikobeats/time-span: ~1.0.5
- null-prototype-object: ~1.2.2
- pretty-ms: ~7.0.1
- debug-glitzs: ^1.0.1

[Unreleased]: https://github.com/json-douglas/debug-fnt/compare/v1.0.4...HEAD
[1.0.4]: https://github.com/json-douglas/debug-fnt/releases/tag/v1.0.4
[1.0.3]: https://github.com/json-douglas/debug-fnt/releases/tag/v1.0.3
[1.0.0]: https://github.com/json-douglas/debug-fnt/releases/tag/v1.0.0