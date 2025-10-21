# Handoff: 501(c)(6) Compliance Work

**Date**: 2025-10-13
**Status**: In Progress - Ready for Homepage Audit
**Context Window**: Fresh agent needed

---

## What We've Accomplished

### 1. ✅ Bylaws Updated (COMPLETED)
- **PR #5**: Updated bylaws to 2025-02-11 approved version
- **Status**: Merged and deployed live
- **File**: `/obada-foundation/bylaws.md`
- **Result**: Now shows proper 501(c)(6) business league language

### 2. ✅ 501c6 Knowledge Base (COMPLETED)
- **File**: `.claude/knowledge/501c6-website-best-practices.md`
- **Content**: ChatGPT-5 Deep Research completed comprehensive guide
- **Purpose**: Reference for all 501(c)(6) compliance updates

### 3. ✅ Compliance Auditor Agent Created (COMPLETED)
- **File**: `.claude/agents/501c6-compliance-auditor.md`
- **Purpose**: Audits pages for 501(c)(6) compliance
- **Features**:
  - References knowledge base automatically
  - Identifies problematic 501(c)(3) language
  - Provides specific recommendations
  - **Should save audit reports automatically** in same directory as audited file
- **Status**: Agent created and updated to include auto-save functionality

---

## Current Issue

The **501c6-compliance-auditor agent needs to audit the homepage** but we hit context window limits.

**Problem**: When spawned as a general-purpose agent, it doesn't automatically save its audit report to the filesystem as instructed in step 5 of its task list.

---

## What You Need To Do

### Immediate Task: Audit Homepage

**Goal**: Get the 501c6-compliance-auditor agent to audit the homepage AND save the report.

**File to audit**: `/Users/hom/Sync/MasterFiles/external-repos/obadafoundation.github.io/index.md`

**Expected output**: Audit report saved as `index-501c6-audit-2025-10-13.md` in the same directory

### How to Proceed

**Option A: Fix Agent to Save Reports**
The agent at `.claude/agents/501c6-compliance-auditor.md` has instructions in step 5 to save reports, but when spawned via general-purpose agent, it may not be following them. You might need to:
1. Test if the agent saves reports when spawned
2. If not, modify the agent instructions to be more explicit about saving
3. Consider adding example code/commands for saving reports

**Option B: Manual Audit + Save**
1. Read the agent definition at `.claude/agents/501c6-compliance-auditor.md`
2. Read the homepage at `index.md`
3. Reference the knowledge base at `.claude/knowledge/501c6-website-best-practices.md`
4. Perform the audit following the agent's format
5. Save the audit report as `index-501c6-audit-2025-10-13.md` in the root directory

### After Homepage Audit is Complete

**Next pages to audit** (in priority order):
1. ✅ Homepage (`/index.md`) - CURRENT TASK
2. Mission page (`/obada-foundation/mission.md`)
3. About/Foundation page (`/obada-foundation/index.md`)
4. Any other pages with 501(c)(3) language

**Workflow after audits**:
1. Create new branch: `content/501c6-mission-about` (or similar)
2. Use **content-editor agent** to implement recommended changes
3. Test locally with Jekyll: `bundle exec jekyll serve`
4. Create PR with all changes
5. Review and merge

---

## Key Context

### Why We're Doing This
- OBADA Foundation applied to IRS as 501(c)(3) - REJECTED
- IRS said website didn't align with 501(c)(3) requirements
- Pivoting to 501(c)(6) business league status
- Need to update ALL website content to meet 501(c)(6) standards before resubmission

### Critical Changes Needed (based on KB)
- Remove all "501(c)(3)" references → "501(c)(6)"
- Remove "charitable," "donations," "public benefit" → "business league," "membership dues," "member benefits"
- Add "consortium," "industry collaboration," "member services"
- Focus on MEMBER BUSINESS INTERESTS, not general public benefit

### Git Workflow
- Protected main branch - all changes via PRs
- Feature branches with descriptive names
- Test locally before committing
- Content-editor agent handles Git workflow automatically

---

## Important Files Reference

**Agent Files**:
- `.claude/agents/501c6-compliance-auditor.md` - Auditor agent (needs to save reports!)
- `.claude/agents/content-editor.md` - Makes content changes
- `.claude/agents/git-operations.md` - Git workflow

**Knowledge Base**:
- `.claude/knowledge/501c6-website-best-practices.md` - Compliance guide
- `.claude/knowledge/2025-02-11-approved-bylaws.md` - Approved bylaws (reference)
- `.claude/knowledge/site-architecture.md` - Jekyll site technical details

**Project Docs**:
- `CLAUDE.md` - Project instructions
- `README.md` - Site overview

**Current Branch**: `main` (bylaws work is merged)

---

## Todo List

- [ ] Fix 501c6-compliance-auditor to save reports automatically
- [ ] Audit homepage and save report to `index-501c6-audit-2025-10-13.md`
- [ ] Audit mission page
- [ ] Audit about page
- [ ] Create new feature branch for updates
- [ ] Use content-editor to implement homepage changes
- [ ] Use content-editor to implement mission changes
- [ ] Use content-editor to implement about changes
- [ ] Test all changes locally
- [ ] Create PR for review
- [ ] Update agent-guidelines.md to clarify voice usage (low priority)

---

## Questions You Might Have

**Q: Why can't we just edit the pages directly?**
A: User wants proper Git workflow with PRs and review. Content-editor agent handles this automatically.

**Q: Should we update all pages at once?**
A: Start with homepage, mission, about (critical pages). Can do others in follow-up PRs.

**Q: What if the audit report shows the page is already compliant?**
A: Unlikely - homepage explicitly says "501(c)(3)" on line 13. But if so, move to next page.

**Q: Can I modify the auditor agent?**
A: Yes! User expects agents to be improved if they're not working properly.

---

## Success Criteria

You'll know you're successful when:
1. ✅ Homepage audit report exists at `/index-501c6-audit-2025-10-13.md`
2. ✅ Report identifies the "501(c)(3)" claim on line 13 as CRITICAL
3. ✅ Report provides specific before/after recommendations
4. ✅ Report references the knowledge base for justification

Then you can proceed with implementing the changes using the content-editor agent.

---

**Good luck! The bylaws are done and deployed - now we need to fix the rest of the site.**

**Repository**: /Users/hom/Sync/MasterFiles/external-repos/obadafoundation.github.io
**Live Site**: https://obadafoundation.org
**GitHub**: https://github.com/obada-foundation/obadafoundation.github.io
