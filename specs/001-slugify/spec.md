# Feature Specification: slugify

**Feature Branch**: `001-slugify`

## User Scenarios & Testing

### User Story 1 - Turn a title into a URL slug (Priority: P1)

A blog author passes a post title and gets a slug they can put in a URL.

**Acceptance Scenarios**:

1. **Given** the title `Hello World`, **When** it is slugified, **Then** the result is `hello-world`.
2. **Given** the title `  Spaces   everywhere  `, **When** it is slugified, **Then** the result is `spaces-everywhere`.
3. **Given** the title `Crème brûlée & café!`, **When** it is slugified, **Then** the result is `creme-brulee-cafe`.

### User Story 2 - Short slugs and display titles (Priority: P2)

The author can cut a slug to a maximum length at a word boundary, and turn a slug back into a display title.

**Acceptance Scenarios**:

1. **Given** the slug `the-quick-brown-fox` and a limit of 12, **When** it is truncated, **Then** the result is `the-quick`.
2. **Given** the slug `hello-world`, **When** it is turned into a title, **Then** the result is `Hello World`.

## Requirements

- **FR-001**: `slugify(text)` MUST return lower-case ASCII words joined by single hyphens, with no leading or trailing hyphen.
- **FR-002**: `slugify` MUST remove accents (é → e) and drop every character that is not a letter or a digit.
- **FR-003**: `slugify` MUST throw a `TypeError` when `text` is not a string.
- **FR-004**: `truncateSlug(slug, max)` MUST return the longest prefix of whole words not longer than `max`.
- **FR-005**: `titleFromSlug(slug)` MUST split on hyphens and capitalize the first letter of each word.
- **FR-006**: The project MUST have no runtime dependencies; tests use `node:test`.
