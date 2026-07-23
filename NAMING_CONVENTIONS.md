# Naming Conventions — Teaching Site Vault

This file defines file and folder naming standards for this vault. Following these conventions ensures URLs stay clean, files sort predictably, and the site remains navigable for decades.

---

## Core Rules

1. **Always lowercase** — no capital letters anywhere in file or folder names
2. **Hyphens only** — use `-` to separate words; never spaces, underscores, or camelCase
3. **No special characters** — no apostrophes, ampersands, colons, slashes, or punctuation
4. **Be descriptive but concise** — a name should tell you what the file is without opening it
5. **Dates in ISO format** — always `YYYY` or `YYYY-MM` or `YYYY-MM-DD`, never `Fall26` or `F26`

These rules exist because file names become URLs. A space becomes `%20`. A capital letter creates case-sensitivity bugs. A special character can break a link entirely. Consistent naming now prevents broken links later.

---

## Top-Level Structure

All public content lives inside a `content/` folder at the vault root. Three subfolders, no numbers, no exceptions:

```
content/
   courses/
   workshops/
   resources/
```

---

## Folder Naming

### Courses

```
content/
   courses/
      course-name/
         institution-semester-year/
```

**Course name:** use the canonical short title, lowercase, hyphenated

```
✓ artificial-intelligence
✓ drawing-and-materiality
✓ web-design-fundamentals
✗ AI
✗ Drawing & Materiality
✗ WebDesign
```

**Offering folder:** institution abbreviation, semester, four-digit year

```
✓ saic-fall-2026
✓ risd-spring-2027
✓ independent-fall-2028
✗ SAIC_F26
✗ fall2026
✗ saic26
```

For independent or self-organized courses with no institution:

```
independent-fall-2026
```

### Workshops

```
content/
   workshops/
      descriptive-workshop-name/
```

Workshops don't have an institution/semester subfolder unless the same workshop is repeated. If repeated, add a date suffix:

```
intro-to-github-pages/
intro-to-github-pages-2026-03/
intro-to-github-pages-2027-09/
```

Use `YYYY-MM` rather than a full date unless you run the same workshop multiple times in one month (rare).

### Resources

```
content/
   resources/
      software/
      workflows/
```

Sub-categorize only if the folder grows beyond ~10 files. Premature sub-categorization creates folders with one or two files in them.

---

## File Naming

### Index Files

Every course, offering, and workshop has an `index.md` at its root. Always named exactly `index.md` — no variation.

```
✓ index.md
✗ overview.md
✗ home.md
✗ artificial-intelligence-index.md
```

Quartz treats `index.md` as the folder's landing page and generates a clean URL without a filename: `yoursite.com/courses/artificial-intelligence/` not `yoursite.com/courses/artificial-intelligence/index`

### Syllabus

Always named exactly `syllabus.md` within its offering folder.

```
saic-fall-2026/
   syllabus.md
```

### Week Files

Zero-padded two-digit numbers. This ensures correct alphabetical sorting in both your file system and on the published site.

```
✓ week-01.md
✓ week-12.md
✗ week-1.md
✗ week1.md
✗ lecture-01.md
```

Always use `week-` as the prefix, not `lecture-`, `session-`, or `class-`. Consistency across all courses makes the URL pattern predictable.

### Assignment Files

Zero-padded two-digit numbers followed by a descriptive name.

```
✓ assignment-01-software-install.md
✓ assignment-02-dataset-critique.md
✓ assignment-03-midterm-project.md
✗ assignment1.md
✗ a1-software.md
✗ midterm.md
```

The number ensures sort order. The descriptive name makes the file identifiable without opening it, and creates a readable URL: `yoursite.com/courses/artificial-intelligence/saic-fall-2026/assignments/assignment-02-dataset-critique`

### Resource Guides

Named after what they teach you to do, not the tool itself.

```
✓ installing-python.md
✓ publishing-with-github-pages.md
✓ setting-up-vscode.md
✗ python.md
✗ github.md
✗ vscode-guide.md
```

Starting with a verb (`installing-`, `setting-up-`, `publishing-`, `using-`, `creating-`) makes the file's purpose immediately clear and sorts related guides together.

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
               week-02.md
               week-03.md
               week-04.md
               week-05.md
               week-06.md
               week-07.md
               week-08.md
               week-09.md
               week-10.md
               week-11.md
               week-12.md
               week-13.md
               week-14.md
               week-15.md
            assignments/
               assignment-01-tool-survey.md
               assignment-02-dataset-critique.md
               assignment-03-midterm-project.md
               assignment-04-final-project.md
         saic-spring-2028/
            index.md
            syllabus.md
            weeks/
               week-01.md
               ...

   workshops/
      intro-to-github-pages/
         index.md
         materials.md
         assignments/
            assignment-01-publish-your-first-page.md
      intro-to-github-pages-2027-09/
         index.md
         materials.md

   resources/
      software/
         installing-python.md
         setting-up-vscode.md
         installing-node.md
      workflows/
         publishing-with-quartz.md
         using-github-desktop.md
```

---

## URL Patterns

Following these conventions produces clean, predictable URLs:

|Content|URL|
|---|---|
|Course landing page|`/courses/artificial-intelligence`|
|Specific offering|`/courses/artificial-intelligence/saic-fall-2026`|
|Week note|`/courses/artificial-intelligence/saic-fall-2026/weeks/week-03`|
|Assignment|`/courses/artificial-intelligence/saic-fall-2026/assignments/assignment-02-dataset-critique`|
|Workshop|`/workshops/intro-to-github-pages`|
|Resource guide|`/resources/software/installing-python`|

---

## What to Do When Names Change

Avoid renaming files and folders after publishing if at all possible. A renamed file is a broken link for anyone who bookmarked the old URL.

If a rename is unavoidable:

1. Update the file or folder name
2. Add a Quartz redirect from the old URL to the new one
3. Search the vault for internal links to the old name and update them

The best way to avoid this problem is to name things carefully the first time, using the conventions above, before publishing.

---

## Quick Reference Card

| Thing                    | Convention                     | Example                             |
| ------------------------ | ------------------------------ | ----------------------------------- |
| All names                | lowercase, hyphens             | `artificial-intelligence`           |
| Top-level content folder | always `content/`              | `content/`                          |
| Course folder            | short canonical title          | `drawing-and-materiality`           |
| Offering folder          | institution-semester-year      | `saic-fall-2026`                    |
| Index file               | always `index.md`              | `index.md`                          |
| Week files               | `week-XX.md` zero-padded       | `week-07.md`                        |
| Assignment files         | `assignment-XX-description.md` | `assignment-02-dataset-critique.md` |
| Resource guides          | verb-first description         | `installing-python.md`              |
| Dates in names           | ISO format                     | `2026-09`                           |
| Repeated workshops       | name + `YYYY-MM` suffix        | `intro-to-github-pages-2026-03`     |