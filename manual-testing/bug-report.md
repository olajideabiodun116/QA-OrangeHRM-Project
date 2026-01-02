# Bug Reports - OrangeHRM Testing

---

##  Table of Contents
1. [Bug Summary](#-bug-summary)
2. [Bugs by Module](#-bugs-by-module)
3. [Detailed Bug Reports](#-detailed-bug-reports)
    * [BUG-001: Employee Search Results](#bug-001-employee-search-returns-incorrect-results-with-special-characters)
    * [BUG-002: Session Timeout Redirect](#bug-002-session-timeout-does-not-redirect-to-login-page)
    * [BUG-003: Photo Upload Validation](#bug-003-employee-photo-upload-accepts-oversized-files-without-validation)
4. [Summary Statistics](#-summary-statistics)
5. [Definitions](#-severity-definitions)

---

##  Bug Summary
| Metric | Count |
| :--- | :--- |
| **Total Bugs Reported** | **3** |
| Critical | 0 |
| High | 1 |
| Medium | 1 |
| Low | 1 |
| **Open** | **3** |
| **Closed** | **0** |

##  Bugs by Module
| Module | Bug Count | Severity Breakdown |
| :--- | :--- | :--- |
| PIM (Employee Management) | 2 | Medium (1), Low (1) |
| Authentication/Security | 1 | High (1) |

---

##  Detailed Bug Reports

### BUG-001: Employee Search Returns Incorrect Results with Special Characters
| Field | Details                   |
| :--- |:--------------------------|
| **Bug ID** | BUG-001                   |
| **Status** | Open                      |
| **Severity** | Medium                    |
| **Priority** | P2                        |
| **Module** | PIM (Employee Management) |
| **Reported By** | Olajide Abiodun           |
| **Reported Date** | 29 December,2025          |
| **Reproducibility** | 100%                      |

#### **Description:**
When searching for employee names containing special characters (e.g., O'Brien, María), the search functionality fails to return accurate results or returns no results at all.

#### **Environment:**
* **Application:** OrangeHRM Demo
* **URL:** https://opensource-demo.orangehrmlive.com/
* **Browser:** Chrome Version 120.0
* **OS:** Windows 11

#### **Steps to Reproduce:**
1. Login with credentials (Admin/admin123)
2. Navigate to PIM module
3. Click "Add Employee"
4. Create employee with name "John O'Brien"
5. Save the employee
6. Return to employee list
7. In the search field, enter "O'Brien"
8. Click "Search" button

#### **Expected Result:**
The system should return employee "John O'Brien" in the search results. Special characters should be handled properly in search queries.

#### **Actual Result:**
No results are displayed OR incorrect results are shown. Search appears to treat the apostrophe as a query terminator.

#### **Severity Justification:**
**Medium** - This affects user ability to search for employees with common name patterns (O'Brien, D'Angelo, etc.), but has a workaround (searching without special characters).

#### **Priority Justification:**
**P2** - Should be fixed in the next release cycle as it impacts data accessibility for a subset of users.

#### **Additional Information:**
* **Workaround:** Search using only the first or last name without special characters
* **Impact:** International names with accents, hyphenated names, names with apostrophes affected
* **Suggested Fix:** Improve search query parsing to handle special characters correctly

---

### BUG-002: Session Timeout Does Not Redirect to Login Page
| Field | Details                 |
| :--- |:------------------------|
| **Bug ID** | BUG-002                 |
| **Status** | Open                    |
| **Severity** | High                    |
| **Priority** | P1                      |
| **Module** | Authentication/Security |
| **Reported By** | Olajide Abiodun         |
| **Reported Date** |  December, 2025         |
| **Reproducibility** | 90%                     |

#### **Description:**
When a user's session times out due to inactivity, attempting to perform actions results in errors rather than a graceful redirect to the login page. This creates a poor user experience and potential data loss.

#### **Environment:**
* **Application:** OrangeHRM Demo
* **URL:** https://opensource-demo.orangehrmlive.com/
* **Browser:** Chrome Version 120.0
* **OS:** Windows 11

#### **Steps to Reproduce:**
1. Login with credentials (Admin/admin123)
2. Navigate to any module (e.g., PIM)
3. Leave the application idle for 30+ minutes (or simulate session timeout)
4. Attempt to perform any action (e.g., click "Add Employee")
5. Observe the behavior

#### **Expected Result:**
User should be redirected to login page with a message: "Session expired. Please login again." Any unsaved data should trigger a warning before redirect. Redirect should happen automatically and gracefully.

#### **Actual Result:**
Application shows error message or blank page. No clear indication that session has expired. User may lose unsaved work without warning.

#### **Severity Justification:**
**High** - This is a security and usability issue. Users experience confusing errors and potential data loss. Session management is critical for application security.

#### **Priority Justification:**
**P1** - Should be fixed urgently as it affects security posture and user experience for all users experiencing session timeouts.

#### **Additional Information:**
* **Workaround:** None available
* **Impact:** Affects all users who leave application idle, causes data loss and confusion
* **Suggested Fix:** Implement proper session timeout handling with automatic redirect and warning message for unsaved data

---

### BUG-003: Employee Photo Upload Accepts Oversized Files Without Validation
| Field | Details                   |
| :--- |:--------------------------|
| **Bug ID** | BUG-003                   |
| **Status** | Open                      |
| **Severity** | Low                       |
| **Priority** | P3                        |
| **Module** | PIM (Employee Management) |
| **Reported By** | Olajide Abiodun           |
| **Reported Date** | December 2025             |
| **Reproducibility** | 100%                      |

#### **Description:**
The employee photo upload feature accepts extremely large image files (e.g., 10MB+) without proper validation or size restrictions. This can lead to performance issues and unnecessary storage consumption.

#### **Environment:**
* **Application:** OrangeHRM Demo
* **URL:** https://opensource-demo.orangehrmlive.com/
* **Browser:** Chrome Version 120.0
* **OS:** Windows 11

#### **Steps to Reproduce:**
1. Login with credentials (Admin/admin123)
2. Navigate to PIM > Add Employee
3. Fill in employee details (First Name: "Test", Last Name: "User")
4. Click on photo upload area
5. Select an image file larger than 5MB (e.g., 10MB high-resolution photo)
6. Observe that file uploads without warning
7. Click "Save"

#### **Expected Result:**
System should validate file size before upload. Display error message: "File size must be less than 1MB". Provide clear guidance on acceptable file sizes and formats. Optionally, auto-resize images to appropriate dimensions.

#### **Actual Result:**
System accepts large files without validation. Upload proceeds normally. No warning or error message displayed. Large files are stored, potentially impacting performance.

#### **Severity Justification:**
**Low** - While this is poor validation, it doesn't break core functionality or pose immediate security risk. It mainly affects performance and storage over time.

#### **Priority Justification:**
**P3** - Should be fixed but not urgent. Can be included in regular maintenance release.

#### **Additional Information:**
* **Workaround:** Manually resize images before uploading
* **Impact:** Minor per user, but cumulative with many employees; affects storage and performance
* **Suggested Fix:** Implement file size validation (1-2MB max), validate file type (MIME type), display user-friendly error messages, consider auto-resizing to standard dimensions (e.g., 200x200px)

---

##  Summary Statistics

### By Severity
| Severity | Count | Percentage |
| :--- | :--- | :--- |
| Critical | 0 | 0% |
| High | 1 | 33% |
| Medium | 1 | 33% |
| Low | 1 | 33% |
| **Total** | **3** | **100%** |

### By Priority
| Priority | Count | Description |
| :--- | :--- | :--- |
| P0 | 0 | Must fix before any release (blocker) |
| P1 | 1 | Must fix in current release |
| P2 | 1 | Should fix in next release |
| P3 | 1 | Fix when time permits (backlog) |
| **Total** | **3** | |

### By Module
| Module | Bugs | Details |
| :--- | :--- | :--- |
| PIM (Employee Management) | 2 | Search functionality, Photo upload |
| Authentication/Security | 1 | Session timeout handling |
| **Total** | **3** | |

---

##  Severity Definitions
| Severity | Definition | Examples |
| :--- | :--- | :--- |
| **Critical** | Application crash, data loss, security vulnerability | System down, data corruption, SQL injection |
| **High** | Major feature broken, no workaround | Login broken, payment fails, data not saving |
| **Medium** | Feature partially working, workaround exists | Search limited, slow performance, minor errors |
| **Low** | Cosmetic issues, minor inconveniences | Typos, alignment issues, color inconsistencies |

##  Priority Definitions
| Priority | Definition | Action Required |
| :--- | :--- | :--- |
| **P0** | Must fix before any release (blocker) | Immediate fix, blocks release |
| **P1** | Must fix in current release | High urgency, fix in current sprint |
| **P2** | Should fix in next release | Medium urgency, schedule for next cycle |
| **P3** | Fix when time permits (backlog) | Low urgency, address when resources available |

---


##  Last Updated
* **Date:** 30 December, 2025
* **Tester:** Olajide Abiodun
* **Application Version:** OrangeHRM Demo
* **Test Environment:** [OrangeHRM Demo Link](https://opensource-demo.orangehrmlive.com/)