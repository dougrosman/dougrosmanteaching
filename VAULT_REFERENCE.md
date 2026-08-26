# Vault Reference — Teaching Site

This vault is a Quartz-powered static website for teaching materials.
It is separate from the personal PKM vault.
All content in this vault is public-facing by default.

---

## Purpose

This vault publishes three types of content:
1. **Course materials** — syllabi, weekly lectures, assignments
2. **Workshop guides** — standalone workshops independent of institutions
3. **Resources** — how-to guides, software installs, workflows

---

## Folder Structure

```
content/
   courses/     ← organized by course name, then institution/semester
   workshops/   ← standalone workshops; add date suffix if repeated
   resources/   ← how-to guides; sub-categorize by software/ and workflows/
```

---

## Course Hierarchy

Courses are organized **by course name first**, then by offering.
This allows the same course taught at multiple institutions to live
under one roof and show its evolution over time.

```
content/courses/
   course-name/
      index.md                    ← top-level course page; lists all offerings
      institution-semester-year/
         index.md                 ← landing page for this specific offering
         syllabus.md
         weeks/
            week-01.md
            ...
         assignments/
            assignment-01-name.md
            ...
```

---

## Frontmatter Conventions

### Property Types

| Property | Type | Notes |
|---|---|---|
| `title` | Text | Plain string |
| `course` | Text | Course name slug e.g. `artificial-intelligence` |
| `institution` | Text | e.g. `SAIC` |
| `semester` | Text | e.g. `Fall` |
| `year` | Number | Four-digit e.g. `2026` |
| `week` | Number | Integer |
| `due` | Date | ISO format |
| `points` | Number | Integer |
| `description` | Text | One-line summary |
| `software-version` | Text | e.g. `3.11` |
| `last-updated` | Date | ISO format |
| `tags` | List | Thematic tags |
| `publish` | Checkbox | Always true in this vault |

---

## Naming Conventions Summary

- Always lowercase, hyphens only, no special characters
- Course folders: `course-name/institution-semester-year/`
- Week files: zero-padded `week-01.md` through `week-15.md`
- Assignment files: `assignment-01-descriptive-name.md`
- Resource guides: verb-first `installing-python.md`
- Index files: always `index.md`
- See NAMING_CONVENTIONS.md for full reference

---

## When Working With This Vault as an AI Agent

- All content in this vault is public — `publish: true` on everything
- Always include `course`, `institution`, `semester`, and `year`
  in frontmatter for course-related files
- Week files are always named `week-XX.md` with zero-padding
- Assignment files always include a number and descriptive name
- Resource guides always include `software-version` and `last-updated`
- Never create content outside the `content/` folder
- Never add numbered prefixes to folder names
- Refer to NAMING_CONVENTIONS.md for any naming decisions
