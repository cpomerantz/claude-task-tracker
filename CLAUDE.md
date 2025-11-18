# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository implements a sprint documentation strategy for tracking work completed outside of coding activities on a two-week sprint cadence. It provides a structured approach to documenting business impact, requirements, solutions, and system changes.

## Sprint Documentation System

### Sprint Structure
- **Duration:** 2 weeks (Monday through second Friday, 14 days total)
- **First Sprint:** October 20, 2025 - October 31, 2025
- **Cadence:** Continuous, starting each Monday after previous sprint ends
- **Location:** `docs/sprints/`
- **Naming:** `YYYY-mm-dd-sprint.md` (using sprint start date)

### Sprint Date Calculation
Given the first sprint starts October 20, 2025 (Monday):
- Sprint 1: Oct 20 - Oct 31, 2025
- Sprint 2: Nov 3 - Nov 14, 2025
- Sprint 3: Nov 17 - Nov 28, 2025
- Each sprint is exactly 14 days, starting Monday and ending the second Friday

### Creating New Sprint Documents

When asked to create a new sprint document:

1. Calculate the sprint dates (next Monday after previous sprint ends)
2. Create the file at `docs/sprints/YYYY-mm-dd-sprint.md`
3. Copy content from `sprint-template.md`
4. Replace template variables:
   - `{{START_DATE}}` → Full date format (e.g., "October 20, 2025")
   - `{{END_DATE}}` → Full date format (e.g., "October 31, 2025")
5. Remove the task template section, leaving only the header and overview

### Adding Tasks to Sprints

Each task documents:
- **Business Impact:** Why this work matters
- **Requirements:** What needed to be done
- **Solution:** How it was accomplished
- **Systems/Processes Impacted:** What changed

When adding a task:
1. Identify the current sprint file in `docs/sprints/`
2. Copy the task template from `sprint-template.md` (lines 12-28)
3. Append to the Tasks section
4. Replace all placeholders:
   - `{{TASK_TITLE}}` → Descriptive title
   - `{{DATE}}` → Completion date (e.g., "October 21, 2025")
   - `{{BUSINESS_IMPACT}}` → Business value description
   - `{{REQUIREMENTS}}` → List of requirements
   - `{{SOLUTION}}` → Implementation description
   - `{{SYSTEMS_IMPACTED}}` → List of affected systems/processes

## Key Files

- `sprint-template.md` - Master template for all sprint documents (source of truth)
- `claude-code-process.md` - Detailed process guide for automation
- `README.md` - High-level overview and quick start guide
- `docs/sprints/` - Directory containing sprint documentation files

## Important Notes

- The `sprint-template.md` file is the authoritative template and should not be modified during normal operations
- Sprint documents are created at the start of each sprint period
- Tasks are added throughout the sprint as work is completed
- Focus on capturing business value and technical impact, not just implementation details
- Sprint documents older than 1 year should be archived to `docs/sprints/archive/`