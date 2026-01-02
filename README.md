# QA Portfolio Assessment - Complete Solution

**Candidate:** [Your Name]  
**Date:** January 2025  
**Application Under Test:** [OrangeHRM Demo](https://opensource-demo.orangehrmlive.com)

---

## Project Structure
```
QA-OrangeHRM-Project/
├── .github/
│   └── workflows/
│       └── ui-tests.yml              # CI/CD pipeline
├── automation/
│   └── ui-test/
│       └── src/
│          └── main/
│              └── java/
│                  └── com.orangehrm/
│                      └── tests/
│                          └── LoginTest.java
│       
│       
│                         # UI testing guide
├── manual-testing/
│   ├── test-cases.md                  # 25 manual test cases
│   ├── exploratory-testing-report.md  # Exploratory testing
│   └── bug-report.md                  # 3 bug reports
│ 
└──── qa-thinking.md                 # QA thinking answers
```

---

## Assessment Overview

This repository contains a comprehensive QA assessment demonstrating:

-  Manual testing skills (test cases & exploratory testing)
-  UI automation with Selenium Java
-  Professional bug reporting and documentation
-  Strategic QA thinking and decision-making

---

## Part 1: Manual Testing

###  Task 1: Test Case Design

**Location:** `manual-testing/test-cases.md`

- **Count:** 25 test cases
- **Coverage:**
    - Login: 6 test cases
    - Dashboard: 4 test cases
    - PIM (Employee Management): 8 test cases
    - Logout: 3 test cases
    - Edge cases: 4 test cases
- **Format:** Markdown table format
- **Google Sheets Link:** [Insert your Google Sheets link here]

###  Task 2: Exploratory Testing

**Location:** `manual-testing/exploratory-testing-report.md`

- **Duration:** 30 minutes
- **Areas Covered:**
    - Login functionality
    - Dashboard widgets & navigation
    - PIM module (employee management)
    - Leave management
    - Time tracking
    - Admin module
- **Issues Found:** 10 issues documented (5 Medium, 5 Low priority)
- **Risks Identified:** Security, data validation, and performance concerns
- **Improvement Suggestions:** Usability, functionality, and technical enhancements

###  Task 3: Bug Reporting

**Location:** `manual-testing/bug-report.md`

- **Bugs Documented:** 3 bugs
    1. Employee search with special characters (Medium severity)
    2. Session timeout handling (High severity)
    3. Photo upload validation (Low severity)
- **Format:** Detailed bug reports with title, severity, priority, steps to reproduce, expected vs actual results

---

## Part 2: Automation Testing

###  Task 4: UI Automation (Selenium Java)

**Location:** `automation/ui-test/`

**Framework:** Selenium WebDriver + Java + TestNG + Maven

**Test Coverage:**
- ✅ Successful login with valid credentials
- ✅ Login with invalid username
- ✅ Login with invalid password
- ✅ Empty username validation
- ✅ Empty password validation
- ✅ Both fields empty validation
- ✅ Successful logout functionality

**Technology Stack:**
- **Language:** Java 11+
- **Framework:** Selenium WebDriver 4.15.0
- **Test Runner:** TestNG 7.8.0
- **Build Tool:** Maven
- **Browser:** Chrome with WebDriverManager

**How to Run:**
```bash
cd automation/ui-test
mvn clean install
mvn test
```

**Detailed Instructions:** See `automation/ui-test/README.md`

---

## Part 3: QA Thinking

**Location:** `docs/qa-thinking.md`

**Questions Answered:**

1. **What areas would you prioritize for testing in production?**
    - Critical user journeys & smoke tests
    - Data integrity & security
    - Integration points & payment processing
    - Performance monitoring

2. **Which tests would you NOT automate, and why?**
    - Exploratory testing (requires human intuition)
    - Usability & UX testing (subjective judgment)
    - One-time tests (not cost-effective)
    - Visual validation & accessibility testing

3. **How do you decide when a bug should block a release?**
    - Security vulnerabilities
    - Data loss or corruption
    - Core functionality failures
    - Legal/compliance issues
    - Evaluation framework: Severity × Impact × Frequency

---

## Technologies Used

### Manual Testing
- Markdown documentation
- Google Sheets for test cases
- Exploratory testing methodology

### UI Automation
- **Language:** Java 11+
- **Framework:** Selenium WebDriver 4.15.0
- **Test Runner:** TestNG 7.8.0
- **Build Tool:** Maven
- **Browser:** Chrome with WebDriverManager

### CI/CD
- GitHub Actions
- Automated testing on every push
- Test report generation

---

## Quick Start Guide

### Prerequisites
- Java JDK 11 or higher
- Maven 3.6+
- Chrome Browser
- IntelliJ IDEA (recommended)

### Setup and Run

#### 1. Clone Repository
```bash
git clone https://github.com/olajideabiodun116/QA-OrangeHRM-Project
cd QA-OrangeHRM-Project
```

#### 2. Run UI Tests
```bash
cd automation/ui-test
mvn clean install
mvn test
```

#### 3. View Test Reports
```bash
# Open in browser
open target/surefire-reports/index.html
```

---

## Documentation Links

| Document | Description | Location                                      |
|----------|-------------|-----------------------------------------------|
| Test Cases | 25 manual test cases | `manual-testing/test-cases.md`                |
| Google Sheets | Test cases in spreadsheet format | https://docs.google.com/spreadsheets/d/1zc3muKs_tIfeGMJYT0EaNAqnEx2vlWfo-O-TF2UcMfw/edit?gid=0#gid=0                                              |
| Exploratory Report | 30-min testing findings | `manual-testing/exploratory-testing-report.md` |
| Bug Reports | 3 documented bugs | `manual-testing/bug-report.md`                |
| UI Tests | Selenium Java automation | `automation/ui-test/`                         |
| QA Thinking | Assessment question answers | `docs/qa-thinking.md`                         |

---

## Assessment Coverage Summary

| Requirement | Status | Details |
|-------------|--------|---------|
| 20-25 Manual Test Cases |  Complete | 25 test cases covering all features |
| Exploratory Testing |  Complete | 30-minute session documented |
| 3+ Bug Reports |  Complete | 3 bugs with full details |
| UI Automation |  Complete | Selenium + Java + TestNG |
| QA Questions |  Complete | All 3 questions answered |

---

## Test Execution Summary

### Manual Testing
- **Test Cases:** 25
- **Priority:** High (4), Medium (11), Low (10)
- **Bugs Found:** 3
- **Coverage:** Login, Dashboard, PIM, Logout, Edge Cases

### UI Automation
- **Tests:** 7 automated tests
- **Framework:** Selenium WebDriver + TestNG
- **Execution Time:** 45 seconds
- **Status:** ✅ All tests passing

---

## CI/CD Pipeline

### GitHub Actions Workflow

- **File:** `.github/workflows/ui-tests.yml`
- **Triggers:** Push to main/master, Pull requests, Manual trigger
- **Steps:**
    1. Checkout code
    2. Setup Java 17
    3. Install Chrome
    4. Run Selenium tests (headless mode)
    5. Upload test reports

**Status:** ![CI Status](https://github.com/olajideabiodun116/QA-OrangeHRM-Project/workflows/UI%20Tests/badge.svg)

---

## Contact Information

- **Name:** Olajide Abiodun
- **Email:** olajideabiodun116@gmail.com
- **GitHub:** [https://github.com/olajideabiodun116/QA-OrangeHRM-Project](https://github.com/yourusername/QA-OrangeHRM-Project)