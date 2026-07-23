# Vault Reference — AI Agent Context File

This file describes the structure, conventions, and logic of this Obsidian vault. Feed it as context to Claude Code at the start of any working session.

---

## Vault Purpose

This is a single unified vault for a scholar and artist. It serves four functions:

1. Personal knowledge management (reading, research, permanent notes)
2. Project management for art and writing projects
3. Teaching material (syllabi, lectures, assignments) published publicly via Quartz
4. A public wiki of concepts, thinkers, and ideas that recur across teaching and practice

---

## Folder Structure

```
Dashboard.md                  ← Daily driver, pinned in sidebar
Templates/                    ← Template files, not content
   Source Note.md
   Project Note.md
   Course Index.md
   Course Offering Index.md
   Week Note.md
   Assignment Note.md
   Wiki Entry.md
   Resource Guide.md

00 Inbox/                     ← Everything lands here first, no exceptions
10 Sources/                   ← One note per book, article, talk, film, podcast
20 Notes/                     ← Processed permanent notes, one idea per note
30 Projects/                  ← Active projects; flat files or subfolders
40 Outputs/                   ← Drafts and finished work; mirrors 30 Projects structure
50 Archive/                   ← Completed or dormant projects
60 Public/                    ← Everything Quartz publishes; the only public-facing folder
   60.1 Courses/              ← Course material organized by course name first
   60.2 Workshops/            ← Independent workshops not tied to an institution
   60.3 Wiki/                 ← Public-facing permanent notes
   60.4 Resources/            ← How-to guides, software installs, workflows
      software/
      workflows/
```

---

## Folder Logic

|Folder|Purpose|Default Publish|
|---|---|---|
|`00 Inbox`|Unprocessed capture, total mess allowed|false|
|`10 Sources`|One note per external source|false|
|`20 Notes`|Processed permanent thinking, one idea per note|false|
|`30 Projects`|Project hubs with tasks and links|false|
|`40 Outputs`|Actual drafts; mirrors project subfolder structure|false|
|`50 Archive`|Finished or dormant work|false|
|`60.1 Courses`|Public course material|true|
|`60.2 Workshops`|Public workshop material|true|
|`60.3 Wiki`|Public permanent notes|true|
|`60.4 Resources`|Public how-to guides|true|

**Key rule:** Folders 00–50 are private. Only `60 Public/` is published by Quartz. `publish: false` is the default. `publish: true` must be set intentionally.

---

## Course Structure

Courses are organized **by course name first**, then by institution and semester. This allows the same course taught multiple times to live under one roof.

```
60.1 Courses/
   course-name/
      index.md                       ← Top-level course page; lists all offerings
      institution-semester-year/
         index.md                    ← Landing page for this specific offering
         syllabus.md
         weeks/
            week-01.md
            week-02.md
            ...
         assignments/
            assignment-01.md
            assignment-02.md
```

**URL pattern:** `yoursite.com/courses/artificial-intelligence/saic-fall-2026/weeks/week-01`

**Folder naming convention:** lowercase, hyphenated

- Course: `artificial-intelligence`
- Offering: `saic-fall-2026`
- Assignment: `assignment-01-descriptive-name`

---

## Project and Output Structure

Simple projects are flat files in `30 Projects/`. Complex projects with multiple related notes get a subfolder. **When a project has a subfolder in `30 Projects/`, it gets a matching subfolder in `40 Outputs/`.**

```
30 Projects/
   simple-project.md
   complex-project/
      complex-project.md            ← Main project note
      complex-project-subproject.md ← Sub-project note

40 Outputs/
   simple-project-draft.md
   complex-project/
      draft-01.md
      draft-02.md
      final.md
```

---

## Frontmatter Conventions

### Property Types

|Property|Obsidian Type|Notes|
|---|---|---|
|`title`|Text|Plain string|
|`author`|List|Handles multiple authors|
|`year`|Number|Numeric for sorting|
|`type`|List|Predefined values per template|
|`status`|List|Predefined values per template|
|`publish`|Checkbox|true or false|
|`started`|Date|ISO format|
|`due`|Date|ISO format|
|`last-updated`|Date|ISO format|
|`week`|Number|Integer|
|`points`|Number|Integer|
|`aliases`|List|Alternative names for wiki entries|
|`course`|Text|Course name slug|
|`institution`|Text|e.g. SAIC|
|`semester`|Text|e.g. Fall|
|`software-version`|Text|e.g. 3.11|
|`description`|Text|One-line summary|
|`tags`|List|Thematic tags only|
|`parent`|Text|Link to parent project for sub-projects|

### Status Values

**Source notes:** `unread` · `inprogress` · `complete`

**Project notes:** `active` · `dormant`

### Type Values

**Source notes:** `book` · `article` · `talk` · `film` · `podcast`

**Project notes:** `art` · `teaching` · `writing`

---

## Template Frontmatter

### Source Note (`10 Sources/`)

```yaml
---
title: 
author: 
year: 
type: book
status: unread
tags:
publish: false
---
```

### Project Note (`30 Projects/`)

```yaml
---
title: 
type: art
status: active
started: 
parent:
publish: false
---
```

### Course Index (`60.1 Courses/course-name/index.md`)

```yaml
---
title: 
description: 
tags:
publish: true
---
```

### Course Offering Index (`60.1 Courses/course-name/offering/index.md`)

```yaml
---
title: 
course: 
institution: 
semester: 
year: 
description: 
tags:
publish: true
---
```

### Week Note (`...offering/weeks/week-XX.md`)

```yaml
---
title: 
course: 
week: 
topic: 
institution: 
semester: 
year: 
publish: true
---
```

### Assignment Note (`...offering/assignments/assignment-XX.md`)

```yaml
---
title: 
course: 
institution: 
semester: 
year: 
due: 
points: 
publish: true
---
```

### Wiki Entry (`60.3 Wiki/`)

```yaml
---
title: 
aliases:
tags:
last-updated: 
publish: true
---
```

### Resource Guide (`60.4 Resources/`)

```yaml
---
title: 
description: 
tags:
software-version: 
last-updated: 
publish: true
---
```

---

## Tags

Tags serve two purposes: **content type** (handled by the `type` property) and **thematic connections** (handled by the `tags` property).

**Do not use tags for content type** — that is handled by the `type` List property. **Use `tags` only for thematic connections** — subjects, concepts, or ideas that cut across multiple notes and folders.

Thematic tags should be:

- Broad rather than narrow (`pedagogy` not `critical-pedagogy-in-stem`)
- Flat or one level deep (`source/book` is acceptable; deeper nesting is not)
- Consistent in form (always lowercase, hyphenated)
- Emergent rather than planned — add a tag when the absence of it creates a real problem

---

## Links vs. Tags

|Use a `[[link]]` when...|Use a `#tag` when...|
|---|---|
|The connection is specific|The connection is categorical|
|You'd want to read the linked note to understand this one|You want to find this note alongside others in the same territory|
|One note directly uses or engages with another|A note broadly touches a subject area|

---

## Wiki vs. Notes

`20 Notes/` is private and can be messy. Notes graduate to `60.3 Wiki/` when:

- They are developed enough to be publicly useful
- They represent a concept, thinker, or idea that recurs across teaching and practice
- They are written in a voice suitable for students or colleagues

**Wiki entries are not course-specific.** They are the intellectual infrastructure that courses and projects draw from. A student following a link from a lecture note to a wiki entry should find deeper context, not course-specific material.

---

## Stopping Note Convention

Every project note contains a **Stopping Note** section at the bottom. At the end of every work session, update it with two sentences:

1. Where you currently are in the project
2. What comes next

This is the single most important habit in the system. It enables you to pick up where you left off without reconstructing your own thinking.

---

## Weekly Processing Ritual

Once per week (20–30 minutes):

1. **Drain `00 Inbox`** — process every item: delete, convert to source note, convert to permanent note, or add to a project
2. **Scan active projects** — open each project note, check task lists, update status
3. **Write one permanent note** — one idea, in your own words, linked to at least one other note
4. **Archive finished projects** — move completed work to `50 Archive/`

---

## Publishing Pipeline

Only `60 Public/` is pointed at by Quartz. Private material is protected by folder structure, not just frontmatter. `publish: true` is a secondary safety check, not the primary protection.

**Flow for course material:**

```
40 Outputs/Teaching/ (draft) → 60.1 Courses/ (publish: true)
```

**Flow for wiki entries:**

```
20 Notes/ (private, developing) → 60.3 Wiki/ (publish: true, clean)
```

**Flow for resource guides:** Write directly in `60.4 Resources/` — these don't need a private draft stage unless they are complex. Always include `software-version` and `last-updated`.

---

## Dashboard Queries (Dataview + Tasks plugins)

The Dashboard note at vault root uses:

- **Inbox count:** Dataview query on `00 Inbox/`
- **Overdue tasks:** Tasks query for incomplete tasks due before today
- **Due soon:** Tasks query for tasks due in next 7 days
- **Active projects:** Dataview query on `30 Projects/` where `status = active`

Task syntax: `- [ ] Task description 📅 YYYY-MM-DD`

---

## Plugins in Use

|Plugin|Type|Purpose|
|---|---|---|
|Templates|Core|Insert template files|
|Backlinks|Core|Always open in sidebar|
|Dataview|Community|Query vault for dashboard|
|Tasks|Community|Due date syntax and filtering|

No other plugins are active. Add plugins only when a specific recurring pain requires one.

---

## When Working With This Vault as an AI Agent

- Always check frontmatter to determine a note's type, status, and publish state
- Never set `publish: true` on notes in `00–50` folders
- When creating course material, always include `course`, `institution`, `semester`, and `year` in frontmatter for Dataview compatibility
- When creating a new project with multiple components, create a subfolder in both `30 Projects/` and `40 Outputs/` with matching names
- When creating a wiki entry, confirm it belongs in `60.3 Wiki/` and not in `20 Notes/` — wiki entries are public and should be written accordingly
- The Stopping Note section of every project note should be updated at the end of every session
- Prefer links over tags for specific connections; prefer tags for broad thematic categorization
- Course folder naming: `course-name/institution-semester-year/` e.g. `artificial-intelligence/saic-fall-2026/`