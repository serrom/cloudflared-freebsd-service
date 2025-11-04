# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.1] - 2025-11-04

### Fixed
- **CRITICAL**: Added missing `--config` parameter to cloudflared command, which caused the tunnel to ignore user configuration and run in quick tunnel mode (trycloudflare.com) instead of using the configured tunnel

### Changed
- Updated command_args to properly pass configuration file path to cloudflared

## [1.0.0] - 2025-10-21

### Added
- Initial release
- rc.d script for running cloudflared as a service on FreeBSD
- Automatic log rotation configuration
- Socket buffer size warning for QUIC performance
- Configuration example file
- README with installation and configuration instructions
- MIT License
