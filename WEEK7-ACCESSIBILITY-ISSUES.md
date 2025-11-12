# Week 7 Lab 2: Intentional Accessibility Issues

This document lists the **intentional accessibility issues** added to the starter code for Week 7 Lab 2 audit exercise.

Students will discover these using axe DevTools and manual testing, then fix at least one high-priority issue.

---

## Summary

- **Critical**: 0
- **Serious**: 2 (1 real, 1 false positive)
- **Moderate**: 1 (verified OK)
- **Minor**: 3 (real issues)
- **Total**: 6 issues

---

## Serious Issues

### Issue 1: Form label missing (Serious) - FALSE POSITIVE
- **Element**: `<input id="title" name="title">` in `tasks/index.peb`
- **Rule**: `label` (WCAG 1.3.1, 4.1.2)
- **Status**: ❌ **FALSE POSITIVE** — Label exists. Students should verify manually.
- **Location**: N/A (not a real issue)

### Issue 2: Insufficient color contrast (Serious) ✅ REAL ISSUE
- **Element**: `<button type="submit">` elements
- **Rule**: `color-contrast` (WCAG 1.4.3 Contrast Minimum)
- **Description**: Button text color `#6c757d` on white background = 4.2:1 contrast (fails AA requirement of 4.5:1)
- **Impact**: People with low vision struggle to read button text
- **Location**: `src/main/resources/static/css/custom.css` lines 263-266
- **Fix**: Students should override with darker color (e.g., `#495057` = 7:1 contrast)
- **Status**: ✅ **CONFIRMED** — High priority fix for Week 7 Lab 2 Activity 5

---

## Moderate Issues

### Issue 3: Skip link not keyboard-accessible (Moderate) - VERIFIED OK
- **Element**: `<a href="#main" class="skip-link">` in `base.peb`
- **Rule**: `skip-link` (best practice)
- **Status**: ✅ **VERIFIED** — Skip link becomes visible on focus. No action needed.
- **Location**: N/A (not a real issue)

---

## Minor Issues

### Issue 4: Empty heading (Minor) ✅ REAL ISSUE
- **Element**: `<h3></h3>` in task list section
- **Rule**: `empty-heading` (WCAG 1.3.1 Info and Relationships)
- **Description**: Heading element has no content
- **Impact**: Screen readers announce empty heading, causing confusion
- **Location**: `src/main/resources/templates/tasks/index.peb` line 32
- **Fix**: Remove empty heading or add appropriate heading text
- **Status**: ✅ **CONFIRMED** — Low priority, defer to later

### Issue 5: Link text is non-descriptive (Minor) ✅ REAL ISSUE
- **Element**: `<a href="...">Click here</a>` in footer
- **Rule**: `link-name` (WCAG 2.4.4 Link Purpose in Context, 2.4.9 Link Purpose Link Only)
- **Description**: Link text "Click here" doesn't describe destination
- **Impact**: Screen reader users navigating by links list can't determine purpose
- **Location**: `src/main/resources/templates/_layout/base.peb` line 49
- **Fix**: Change to descriptive text (e.g., "WCAG 2.2 Quick Reference")
- **Status**: ✅ **CONFIRMED** — Low priority, best practice

### Issue 6: Redundant navigation link (Minor) ✅ REAL ISSUE
- **Element**: Duplicate "Tasks" link in navigation
- **Rule**: Best practice (not a WCAG violation, but poor UX)
- **Description**: "Tasks" link appears twice in same navigation menu
- **Impact**: Confusing for all users, especially keyboard/screen reader users who must tab through duplicate
- **Location**: `src/main/resources/templates/_layout/base.peb` lines 29 and 31
- **Fix**: Remove duplicate link
- **Status**: ✅ **CONFIRMED** — Low priority, UX improvement

---

## Expected Student Actions

1. **Run axe DevTools** → Find all 6 issues
2. **Verify Issue 1** → Confirm it's a false positive (label exists)
3. **Verify Issue 3** → Confirm skip link works (Tab key reveals it)
4. **Prioritize Issue 2** → Highest severity, affects inclusion
5. **Implement fix for Issue 2** → Override button color in CSS
6. **Test fix** → Verify contrast ratio with WebAIM contrast checker
7. **Document in backlog** → Add Issues 2, 4, 5, 6 to inclusive backlog with severity scores
8. **Defer Issues 4-6** → Low priority, document for future iteration

---

## Implementation Notes

These issues were intentionally added in commit `be5c216` (button contrast) and subsequent commits (minor issues).

**DO NOT** remove these issues from the starter code — they are pedagogical scaffolding for Week 7 Lab 2.

Students will fix Issue 2 (button contrast) in Week 7 Lab 2 Activity 5 as their priority accessibility fix.
