# Naming Conventions — Teaching Site Vault

This file defines file and folder naming standards for this vault.
Following these conventions ensures URLs stay clean, files sort predictably,
and the site remains navigable for decades.

---

## Core Rules

1. **Always lowercase** — no capital letters anywhere in file or folder names
2. **Hyphens only** — use `-` to separate words; never spaces, underscores, or camelCase
3. **No special characters** — no apostrophes, ampersands, colons, slashes, or punctuation
4. **Be descriptive but concise** — a name should tell you what the file is without opening it
5. **Dates in ISO format** — always `YYYY` or `YYYY-MM` or `YYYY-MM-DD`, never `Fall26` or `F26`

These rules exist because file names become URLs. A space becomes `%20`.
A capital letter creates case-sensitivity bugs. A special character can break
a link entirely. Consistent naming now prevents broken links later.

---

## Top-Level Structure

All public content lives inside a `content/` folder at the vault root.
Three subfolders, no numbers, no exceptions:

```
content/
   courses/
   workshops/
   resources/
```

---

## Folder Naming

### Courses

**Course name:** use the canonical short title, lowercase, hyphenated

```
✓ artificial-intelligence
✓ drawing-and-materiality
✗ AI
✗ Drawing & Materiality
```

**Offering folder:** institution abbreviation, semester, four-digit year

```
✓ saic-fall-2026
✓ risd-spring-2027
✓ independent-fall-2028
✗ SAIC_F26
✗ fall2026
```

For independent courses with no institution: `independent-fall-2026`

### Workshops

Workshops don't have an institution/semester subfolder unless repeated.
If repeated, add a date suffix:

```
intro-to-github-pages/
intro-to-github-pages-2026-03/
intro-to-github-pages-2027-09/
```

### Resources

Sub-categorize only if the folder grows beyond ~10 files.

---

## File Naming

### Index Files
Always named exactly `index.md` — no variation.
Quartz treats `index.md` as the folder's landing page, producing clean URLs.

### Syllabus
Always named exactly `syllabus.md` within its offering folder.

### Week Files
Zero-padded two-digit numbers:

```
✓ week-01.md
✓ week-12.md
✗ week-1.md
✗ lecture-01.md
```
Always use `week-` prefix, not `lecture-`, `session-`, or `class-`.

### Assignment Files
Zero-padded two-digit numbers followed by a descriptive name:

```
✓ assignment-01-software-install.md
✓ assignment-02-dataset-critique.md
✗ assignment1.md
✗ midterm.md
```

### Resource Guides
Named after what they teach you to do, starting with a verb:

```
✓ installing-python.md
✓ publishing-with-github-pages.md
✗ python.md
✗ github.md
```

---

## Complete Example

```
content/
   courses/
      artificial-intelligence/
         index.md
         saic-fall-2026/
            index.md
            syllabus.md
            weeks/
               week-01.md
               ...
               week-15.md
            assignments/
               assignment-01-tool-survey.md
               assignment-02-dataset-critique.md
         saic-spring-2028/
            index.md
            syllabus.md

   workshops/
      intro-to-github-pages/
         index.md
         materials.md
         assignments/
            assignment-01-publish-your-first-page.md

   resources/
      software/
         installing-python.md
         setting-up-vscode.md
      workflows/
         publishing-with-quartz.md
```

---

## URL Patterns

| Content | URL |
|---|---|
| Course landing page | `/courses/artificial-intelligence` |
| Specific offering | `/courses/artificial-intelligence/saic-fall-2026` |
| Week note | `/courses/artificial-intelligence/saic-fall-2026/weeks/week-03` |
| Assignment | `/courses/artificial-intelligence/saic-fall-2026/assignments/assignment-02-dataset-critique` |
| Workshop | `/workshops/intro-to-github-pages` |
| Resource guide | `/resources/software/installing-python` |

---

## What to Do When Names Change

Avoid renaming files and folders after publishing — a renamed file
breaks bookmarked URLs. If unavoidable:
1. Update the file or folder name
2. Add a Quartz redirect from the old URL to the new one
3. Search the vault for internal links to the old name and update them

---

## Quick Reference Card

| Thing | Convention | Example |
|---|---|---|
| All names | lowercase, hyphens | `artificial-intelligence` |
| Top-level content folder | always `content/` | `content/` |
| Course folder | short canonical title | `drawing-and-materiality` |
| Offering folder | institution-semester-year | `saic-fall-2026` |
| Index file | always `index.md` | `index.md` |
| Week files | `week-XX.md` zero-padded | `week-07.md` |
| Assignment files | `assignment-XX-description.md` | `assignment-02-dataset-critique.md` |
| Resource guides | verb-first description | `installing-python.md` |
| Dates in names | ISO format | `2026-09` |
| Repeated workshops | name + `YYYY-MM` suffix | `intro-to-github-pages-2026-03` |
