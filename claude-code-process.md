# Sprint Documentation Process

This document outlines the process for managing sprint documentation using Claude Code.

## Sprint Structure

- **Duration:** 2 weeks
- **First Sprint:** October 20, 2025 - October 31, 2025
- **Subsequent Sprints:** Start on Mondays following the previous sprint's end date
- **File Location:** `docs/sprints/`
- **Naming Convention:** `YYYY-mm-dd-sprint.md` (using the sprint start date)

## Creating a New Sprint Document

### Steps

1. **Determine Sprint Dates**
   - Calculate the next sprint start date (should be a Monday)
   - Calculate the sprint end date (13 days after start, which is the second Friday)
   
2. **Create Sprint File**
   ```bash
   # Copy the template
   cp docs/sprints/sprint-template.md docs/sprints/YYYY-mm-dd-sprint.md
   
   # Example for first sprint:
   cp docs/sprints/sprint-template.md docs/sprints/2025-10-20-sprint.md
   ```

3. **Replace Template Variables**
   Replace the following placeholders in the new file:
   - `{{START_DATE}}` → Sprint start date (e.g., "October 20, 2025")
   - `{{END_DATE}}` → Sprint end date (e.g., "October 31, 2025")

4. **Remove Task Template Section**
   Remove or comment out the example task section, leaving just the header and overview.

### Sprint Date Calculation

Given the first sprint starts October 20, 2025 (Monday):
- Sprint 1: Oct 20 - Oct 31, 2025
- Sprint 2: Nov 3 - Nov 14, 2025 (next Monday)
- Sprint 3: Nov 17 - Nov 28, 2025
- And so on...

Each sprint is exactly 2 weeks (14 days), starting on Monday and ending on the second Friday.

## Adding a New Task to a Sprint

### Task Template

```markdown
### Task: {{TASK_TITLE}}

**Date:** {{DATE}}

#### Business Impact
{{BUSINESS_IMPACT}}

#### Requirements
{{REQUIREMENTS}}

#### Solution
{{SOLUTION}}

#### Systems/Processes Impacted
{{SYSTEMS_IMPACTED}}

---
```

### Steps

1. **Open Current Sprint Document**
   - Navigate to `docs/sprints/`
   - Open the current sprint file (e.g., `2025-10-20-sprint.md`)

2. **Copy Task Template**
   - Copy the task template section from `sprint-template.md`
   - Or use the template above

3. **Add Task to Sprint**
   - Paste the task template at the end of the Tasks section
   - Before any subsequent task separators

4. **Fill in Task Details**
   Replace the following placeholders:
   - `{{TASK_TITLE}}` → Descriptive title of the task/work item
   - `{{DATE}}` → Date the work was completed (e.g., "October 21, 2025")
   - `{{BUSINESS_IMPACT}}` → Describe the business value and impact
   - `{{REQUIREMENTS}}` → List the requirements that drove this work
   - `{{SOLUTION}}` → Describe the solution implemented
   - `{{SYSTEMS_IMPACTED}}` → List systems, services, or processes affected

### Example Task

```markdown
### Task: Implement API Rate Limiting

**Date:** October 21, 2025

#### Business Impact
Protects API infrastructure from abuse and ensures fair usage across all clients. Reduces risk of service degradation and improves system reliability.

#### Requirements
- Limit requests to 1000 per hour per API key
- Return appropriate HTTP 429 status codes
- Include rate limit headers in responses
- Provide grace period for legitimate burst traffic

#### Solution
Implemented Redis-based rate limiting using sliding window algorithm. Added middleware to Express application that tracks request counts per API key. Configured rate limit thresholds in environment variables for easy adjustment per environment.

#### Systems/Processes Impacted
- API Gateway
- Redis Cache
- Authentication Service
- Monitoring/Alerting (new metrics added)
- API Documentation (updated with rate limit info)

---
```

## Claude Code Automation

### Command to Create New Sprint

```bash
# Calculate next sprint dates (implement date logic)
NEXT_SPRINT_START="YYYY-mm-dd"
NEXT_SPRINT_START_FORMATTED="Month DD, YYYY"
NEXT_SPRINT_END_FORMATTED="Month DD, YYYY"

# Copy template
cp docs/sprints/sprint-template.md docs/sprints/${NEXT_SPRINT_START}-sprint.md

# Replace placeholders (using sed or similar)
sed -i "s/{{START_DATE}}/${NEXT_SPRINT_START_FORMATTED}/g" docs/sprints/${NEXT_SPRINT_START}-sprint.md
sed -i "s/{{END_DATE}}/${NEXT_SPRINT_END_FORMATTED}/g" docs/sprints/${NEXT_SPRINT_START}-sprint.md

# Remove the example task template section
# (Keep header and overview, remove task example)
```

### Command to Add New Task

```bash
# Read task template
TASK_TEMPLATE=$(cat docs/sprints/sprint-template.md | grep -A 20 "### Task:")

# Append to current sprint file
echo "$TASK_TEMPLATE" >> docs/sprints/CURRENT_SPRINT_FILE.md
```

## Notes

- Always maintain the sprint template file (`sprint-template.md`) as the source of truth
- Sprint documents should be created at the start of each sprint period
- Tasks can be added throughout the sprint as work is completed
- Keep task descriptions concise but comprehensive
- Focus on business value and technical impact
