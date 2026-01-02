# Exploratory Testing Session Report - OrangeHRM

## Table of Contents
1. [Session Information](#session-information)
2. [Areas Explored](#areas-explored)
    * [Login & Authentication](#1-login--authentication-5-minutes)
    * [Dashboard & Navigation](#2-dashboard--navigation-5-minutes)
    * [PIM Module](#3-pim-personnel-information-management-8-minutes)
    * [Leave Management](#4-leave-management-module-5-minutes)
    * [Time Module](#5-time-module-4-minutes)
    * [Admin Module](#6-admin-module-3-minutes)
3. [Summary of Issues Found](#summary-of-issues-found)
4. [Improvement Suggestions](#improvement-suggestions)
5. [Risk Areas Identified](#risk-areas-identified)
6. [Testing Techniques & Findings](#testing-techniques-used)
7. [ Conclusion](#next-steps)

---

## Session Information
| Field | Details                                    |
| :--- |:-------------------------------------------|
| **Application** | OrangeHRM Demo                             |
| **URL** | https://opensource-demo.orangehrmlive.com/ |
| **Tester** | Olajide Abiodun                            |
| **Date** | December, 2025                             |
| **Duration** | 30 minutes                                 |
| **Browser** | Chrome Version 120.0                       |
| **OS** | Windows 11                                 |

**Session Charter:** Explore OrangeHRM core functionality to identify usability issues, bugs, and improvement opportunities across Login, Dashboard, PIM, Leave, Time, and Admin modules.

---

## Areas Explored

### 1. Login & Authentication (5 minutes)
**What I Tested:**
* Valid and invalid login scenarios
* Password visibility toggle functionality
* "Forgot Password" link behavior
* Login form validation and error messages
* Session handling after logout

**Observations:**
* Password field has show/hide toggle - good UX feature
* Login credentials pre-filled in demo environment (Admin/admin123)
* Error messages are clear: "Invalid credentials" displays prominently
* Login page is responsive and loads quickly
* Form validation works for empty fields

**Issues Found:**
* **Issue:** "Forgot Password" link redirects to a placeholder page with no actual functionality.  
  *Impact: Users cannot reset passwords (expected in demo, but noted).*
* **Issue:** No "Remember Me" checkbox option available.  
  *Impact: Users must re-enter credentials every session.*
* **Issue:** No CAPTCHA or rate limiting visible after multiple failed login attempts.  
  *Impact: Potential security concern for brute force attacks.*

---

### 2. Dashboard & Navigation (5 minutes)
**What I Tested:**
* Dashboard widget loading and display
* Quick launch icons functionality
* Left navigation menu accessibility
* Breadcrumb navigation
* User profile menu options

**Observations:**
* Dashboard loads within 2-3 seconds
* Widgets display relevant information (Time at Work, My Actions, Quick Launch)
* Navigation menu is well-organized with clear icons
* Search functionality available in header
* User dropdown shows username and logout option

**Issues Found:**
* **Issue:** "Time at Work" widget shows "Punch In" button but no actual time tracking data.  
  *Impact: Unclear if feature is functional or placeholder.*
* **Issue:** Some Quick Launch icons don't provide visual feedback on hover.  
  *Impact: Reduced user experience, unclear if items are clickable.*
* **Issue:** No way to customize or rearrange dashboard widgets.  
  *Impact: Limited personalization for different user roles.*

---

### 3. PIM (Personnel Information Management) (8 minutes)
**What I Tested:**
* Employee list view and pagination
* Add new employee workflow
* Employee search functionality (by name and ID)
* Edit employee details
* Delete employee operation
* Employee photo upload
* Custom fields and data validation

**Observations:**
* Employee list displays clearly with sortable columns
* Search works with partial name matching
* Add employee form is comprehensive with mandatory field indicators
* Employee ID auto-generates if not provided
* Photo upload accepts common image formats

**Issues Found:**
* **Issue:** Search doesn't handle special characters well (e.g., "O'Brien" returns no results).  
  *Impact: Cannot find employees with apostrophes, accents, or hyphens in names.* (**Severity: Medium**)
* **Issue:** No file size validation on photo upload - accepted 15MB image without warning.  
  *Impact: Can slow down application and waste storage.* (**Severity: Low**)
* **Issue:** When adding employee with duplicate Employee ID, error message is generic.  
  *Impact: User doesn't know exactly what went wrong.* (**Severity: Low**)
* **Issue:** Delete confirmation popup appears too quickly without clear warning about data loss.  
  *Impact: Risk of accidental deletion.* (**Severity: Medium**)
* **Issue:** No bulk operations available (e.g., delete multiple employees at once).  
  *Impact: Tedious for administrators managing many records.* (**Severity: Low**)
* **Issue:** Employee list pagination resets to page 1 after performing any action.  
  *Impact: Frustrating navigation experience.* (**Severity: Low**)

---

### 4. Leave Management Module (5 minutes)
**What I Tested:**
* Leave list view and filters
* Apply leave functionality
* Leave types and entitlements
* Leave balance display
* Leave approval workflow
* Leave calendar view

**Observations:**
* Leave types are pre-configured (Vacation, Sick Leave, etc.)
* Calendar view provides good visual representation
* Apply leave form includes date validation
* Leave balance displays for each type
* Filters work correctly (status, leave type, date range)

**Issues Found:**
* **Issue:** Cannot apply leave for past dates - form blocks it entirely.  
  *Impact: Admins cannot retroactively record leave.* (**Severity: Medium**)
* **Issue:** Leave balance doesn't update in real-time after applying leave.  
  *Impact: Confusing - users must refresh to see updated balance.* (**Severity: Low**)
* **Issue:** No notification or confirmation email mentioned after leave application.  
  *Impact: User uncertainty about whether leave was submitted.* (**Severity: Low**)
* **Issue:** Weekend dates are selectable when applying leave (should be blocked or warned).  
  *Impact: Confusion about whether weekends count toward leave.* (**Severity: Low**)

---

### 5. Time Module (4 minutes)
**What I Tested:**
* Timesheet entry and submission
* Time tracking for projects
* Attendance records
* Project and activity selection
* Timesheet approval process

**Observations:**
* Timesheet interface is straightforward and intuitive
* Project/activity dropdown selection works well
* Time entry validation prevents negative hours
* Weekly timesheet view is clear
* Shows total hours per day

**Issues Found:**
* **Issue:** Can enter more than 24 hours for a single day without warning.  
  *Impact: Data integrity issue, unrealistic time entries.* (**Severity: Medium**)
* **Issue:** No way to copy previous week's timesheet entries.  
  *Impact: Repetitive data entry for consistent work patterns.* (**Severity: Low**)
* **Issue:** Timesheet doesn't auto-save draft entries.  
  *Impact: Data loss if browser crashes or user navigates away.* (**Severity: Medium**)
* **Issue:** No mobile-optimized view for time entry.  
  *Impact: Difficult to use on phones/tablets.* (**Severity: Low**)

---

### 6. Admin Module (3 minutes)
**What I Tested:**
* User management functionality
* Job titles and pay grades configuration
* Organization structure view
* System users list
* User role and permission settings

**Observations:**
* Admin module has comprehensive system configuration options
* User role management appears granular
* Organization structure visualization is clear
* Job titles, pay grades, and employment status are configurable
* System users list shows username, user role, and status

**Issues Found:**
* **Issue:** No password strength indicator when creating new system users.  
  *Impact: Weak passwords may be created.* (**Severity: Medium - Security concern**)
* **Issue:** Cannot bulk import users via CSV or Excel.  
  *Impact: Time-consuming for large organizations.* (**Severity: Low**)
* **Issue:** Organization structure doesn't show reporting relationships clearly.  
  *Impact: Difficult to understand hierarchy.* (**Severity: Low**)

---

## Summary of Issues Found

### High Priority Issues
* None found during this session.

### Medium Priority Issues
| Issue Title | Description | Recommendation |
| :--- | :--- | :--- |
| **Special Character Search Failure (PIM)** | Search doesn't handle names with apostrophes, accents, or special characters. | Improve search query parsing to handle Unicode and special characters. |
| **Session Timeout Handling** | After idle timeout, actions show errors instead of graceful redirect. | Implement automatic redirect to login with session timeout message. |
| **Delete Confirmation Insufficient** | Delete confirmation doesn't clearly warn about permanent data loss. | Enhance confirmation dialog with clear warning text. |
| **Timesheet Hours Validation** | Allows entry of >24 hours per day. | Add validation to cap daily hours at 24 with warning message. |
| **No Password Strength Indicator** | Password field doesn't show strength or requirements. | Add real-time password strength meter. |

### Low Priority Issues
* **Photo Upload Size Validation Missing:** No file size limit on employee photo uploads. (Recommendation: 1-2MB limit).
* **Leave Balance Not Real-Time:** Balance doesn't update immediately after applying leave. (Recommendation: Real-time calculation).
* **No Bulk Operations:** Cannot perform bulk actions (delete, export, update). (Recommendation: Add multi-select).
* **Pagination Reset Issue:** Pagination returns to page 1 after any action. (Recommendation: Maintain page state).
* **No Draft Auto-Save:** Timesheet entries don't auto-save. (Recommendation: Implement 30s auto-save).

---

## Improvement Suggestions

### Usability Improvements
* **Enhanced Search Functionality:** * Add advanced search with multiple filters (department, location, status).
    * Implement fuzzy search for better name matching.
    * Add search history or recent searches and support for wildcards.
* **Better Visual Feedback:** * Add loading spinners for all async operations.
    * Improve success/error message positioning (toast notifications).
    * Add confirmation dialogs for all destructive actions.
* **Navigation Enhancements:** * Add keyboard shortcuts (e.g., Ctrl+S to save).
    * Implement clickable breadcrumb paths.
    * Add "Recent Items" or "Frequently Accessed" quick access panel.

### Dashboard Customization
* Allow users to add/remove widgets.
* Enable drag-and-drop widget rearrangement.
* Add widgets for quick stats (total employees, pending leaves, etc.).

### Performance Improvements
* **Optimize Large Lists:** Implement virtual scrolling for employee lists with 500+ records.
* **Asset Optimization:** Lazy loading for images and automatic compression on upload.
* **Code Efficiency:** Minimize and bundle JavaScript/CSS files; use CDN for static assets.

### Feature Suggestions
* **Bulk Operations:** CSV/Excel import/export for employees and bulk updates.
* **Export Functionality:** Export reports in PDF, Excel, CSV formats with a custom report builder.
* **Mobile Responsiveness:** Optimize all forms for mobile devices or create a PWA.
* **Notifications System:** Email and In-app notifications for leave approvals and pending actions.
* **Audit Trail:** Log all data changes with user and timestamp for compliance reporting.

---

## Risk Areas Identified

| Category | Risks Identified |
| :--- | :--- |
| **Data Validation** | Fields accept overly long inputs; Special character handling is inconsistent; Date/Email validation is weak. |
| **Security Concerns** | No CAPTCHA/Rate limiting; Weak password requirements; Poor session timeout handling. |
| **Performance Concerns** | Potential lag on large employee lists; No file size limits; No visible caching strategy. |
| **Usability Concerns** | Limited accessibility (WCAG); Lack of keyboard navigation; Mobile experience unoptimized. |

---

## Testing Techniques Used
* **Boundary Value Analysis:** Tested minimum/maximum values in numeric fields.
* **Equivalence Partitioning:** Grouped similar test scenarios.
* **Error Guessing:** Attempted common error-prone scenarios.
* **User Workflow Testing:** Followed realistic user journeys.
* **Negative Testing:** Tried invalid inputs and edge cases.
* **Exploratory Testing:** Free-form testing to discover unexpected issues.

### Positive Findings
* **Intuitive UI:** Overall interface is clean and easy to navigate.
* **Comprehensive Features:** Wide range of HR functions covered.
* **Consistent Design:** UI patterns are consistent across modules.
* **Fast Performance:** Most pages load within 2-3 seconds.
* **Logical Workflow:** Process flows make sense.

---


## Conclusion
During this 30-minute exploratory testing session, I identified **10 issues** (5 medium, 5 low priority) and documented **15+ improvement suggestions**. The application shows good fundamental design, but requires work on search query parsing, data validation, and session management.

* **Total Issues Found:** 10
* **Total Time:** 30 minutes
* **Session Completed:** December, 2025

---