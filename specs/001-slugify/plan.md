# Implementation Plan: slugify

**Language**: JavaScript (ES modules), Node 22+. **Tests**: `node --test` (`npm test`). **Dependencies**: none.

## Structure

```text
src/slugify.js        slugify(text)
src/truncate.js       truncateSlug(slug, max)
src/title.js          titleFromSlug(slug)
test/*.test.js        one test file per module
```

Accents are removed with `String.prototype.normalize("NFKD")` and by dropping combining marks (`\p{M}`).
