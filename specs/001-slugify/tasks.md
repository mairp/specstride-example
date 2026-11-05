# Tasks: slugify

## Phase 1: Basic slugs

- [ ] T001 Create src/slugify.js exporting slugify(text): lower-case the text, replace every run of spaces with one hyphen, and trim leading and trailing hyphens (FR-001)
- [ ] T002 Create test/slugify.test.js covering `Hello World` → `hello-world` and `  Spaces   everywhere  ` → `spaces-everywhere`

## Phase 2: Accents, symbols and errors

- [ ] T003 In src/slugify.js, remove accents with NFKD normalization and drop every character that is not a letter or a digit, so `Crème brûlée & café!` → `creme-brulee-cafe` (FR-002)
- [ ] T004 In src/slugify.js, throw a TypeError when the argument is not a string (FR-003)
- [ ] T005 Extend test/slugify.test.js with the accent, symbol and TypeError cases

## Phase 3: Short slugs and display titles

- [ ] T006 [P] Create src/truncate.js exporting truncateSlug(slug, max) that keeps whole words only, and test/truncate.test.js covering `the-quick-brown-fox` with 12 → `the-quick` (FR-004)
- [ ] T007 [P] Create src/title.js exporting titleFromSlug(slug), and test/title.test.js covering `hello-world` → `Hello World` (FR-005)
