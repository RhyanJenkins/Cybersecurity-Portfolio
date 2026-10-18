# Portfolio Assets

This directory stores public-facing visual assets used across my cybersecurity portfolio, including website graphics, architecture diagrams, and supporting illustrations.

All published assets are reviewed to ensure they are relevant, accurate, and appropriate for public release.

## Purpose

The assets directory provides a central location for reusable portfolio media, including:

- Sanitized network architecture diagrams
- Portfolio website graphics
- Project overview illustrations
- Reusable icons and visual resources

Investigation-specific evidence should be maintained with its associated project or case study whenever possible, rather than mixed with general website assets.

## Asset Organization

As visual assets are added, the directory may be organized into:

- `diagrams/` — Sanitized network and infrastructure diagrams
- `images/` — Portfolio graphics and reusable illustrations
- `icons/` — Icons used by the portfolio website

These subdirectories are proposed and will be created only when needed.

## File Naming Standards

Use descriptive, lowercase filenames with hyphens.

Examples:

- `homelab-logical-topology.png`
- `security-monitoring-architecture.png`
- `portfolio-project-banner.png`

Evidence screenshots should follow the naming conventions established for their respective investigations.

## Security & Sanitization

Before publishing any image or document, review it for:

- Credentials, API keys, and authentication tokens
- Private IP addresses, MAC addresses, and live management endpoints
- Internal DNS names and sensitive network configuration
- Session identifiers, personal information, or confidential content
- Unnecessary metadata that could expose sensitive details

Redaction must be applied to a separate public copy, while the original remains preserved privately.

Sensitive information should be permanently removed or covered with opaque redaction before publication. Visual blur alone should not be relied upon to conceal secrets.

## Evidence Integrity

Original investigation artifacts are preserved separately from public presentation files.

When applicable, evidence records should identify:

- Original filename
- Evidence identifier
- Source system
- Collection date and time
- Integrity hash
- Redactions or other modifications
- Public filename and location

Sanitized images must not be represented as unchanged originals.

[View Project Evidence Management Standards](../01-homelab-infrastructure/PRJ-001-homelab-architecture/evidence/README.md)

## Usage in Portfolio Documentation

Images stored here may be referenced using relative Markdown paths.

Example:

`![Logical Homelab Topology](assets/diagrams/homelab-logical-topology.png)`

This example assumes the image is being linked from the repository's root README and that the image file has been added.

Paths must be adjusted when referenced from nested project directories.

## Current Status

**Status:** Asset publishing standards established.

Visual assets will be added after their content and security implications have been reviewed.

---

[Return to Main Portfolio](../README.md)