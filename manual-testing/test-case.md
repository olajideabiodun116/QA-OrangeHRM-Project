# OrangeHRM Manual Test Cases

## Test Execution Summary

| Metric | Count |
|--------|-------|
| **Total Test Cases** | 25 |
| **Executed** | 0 |
| **Passed** | 0 |
| **Failed** | 0 |
| **Blocked** | 0 |
| **Not Executed** | 25 |

---

## Login Module (6 Test Cases)

| Test Case ID | Test Scenario | Priority | Test Steps | Test Data | Expected Result | Status |
|--------------|---------------|----------|------------|-----------|-----------------|--------|
| **TC_001** | Verify Successful Login with Valid Credentials | P0 | 1. Navigate to https://opensource-demo.orangehrmlive.com/<br>2. Enter username: "Admin"<br>3. Enter password: "admin123"<br>4. Click "Login" button | Username: Admin<br>Password: admin123 | User successfully logs in and dashboard page is displayed | Not Executed |
| **TC_002** | Verify Login with Invalid Username | P1 | 1. Navigate to login page<br>2. Enter username: "InvalidUser"<br>3. Enter password: "admin123"<br>4. Click "Login" button | Username: InvalidUser<br>Password: admin123 | Error message "Invalid credentials" is displayed | Not Executed |
| **TC_003** | Verify Login with Invalid Password | P1 | 1. Navigate to login page<br>2. Enter username: "Admin"<br>3. Enter password: "wrongpassword"<br>4. Click "Login" button | Username: Admin<br>Password: wrongpassword | Error message "Invalid credentials" is displayed | Not Executed |
| **TC_004** | Verify Login with Empty Username | P2 | 1. Navigate to login page<br>2. Leave username field empty<br>3. Enter password: "admin123"<br>4. Click "Login" button | Username: (empty)<br>Password: admin123 | Validation message "Required" appears under username field | Not Executed |
| **TC_005** | Verify Login with Empty Password | P2 | 1. Navigate to login page<br>2. Enter username: "Admin"<br>3. Leave password field empty<br>4. Click "Login" button | Username: Admin<br>Password: (empty) | Validation message "Required" appears under password field | Not Executed |
| **TC_006** | Verify Login with SQL Injection Attempt | P1 | 1. Navigate to login page<br>2. Enter username: "Admin' OR '1'='1"<br>3. Enter password: "admin123"<br>4. Click "Login" button | Username: Admin' OR '1'='1<br>Password: admin123 | Login fails with invalid credentials message, no SQL execution | Not Executed |

---

## Dashboard Module (4 Test Cases)

| Test Case ID | Test Scenario | Priority | Test Steps | Test Data | Expected Result | Status |
|--------------|---------------|----------|------------|-----------|-----------------|--------|
| **TC_007** | Verify Dashboard Loads After Login | P0 | 1. Login with valid credentials<br>2. Observe dashboard page load | N/A | Dashboard displays with widgets, navigation menu, and user information | Not Executed |
| **TC_008** | Verify Quick Launch Icons are Clickable | P2 | 1. Login to application<br>2. Locate Quick Launch section on dashboard<br>3. Click on "Assign Leave" icon | N/A | User is redirected to Assign Leave page | Not Executed |
| **TC_009** | Verify Time at Work Widget Displays | P3 | 1. Login to application<br>2. Locate "Time at Work" widget on dashboard<br>3. Verify widget displays time information | N/A | Widget shows punch in/out times or appropriate message | Not Executed |
| **TC_010** | Verify My Actions Widget Functionality | P2 | 1. Login to application<br>2. Locate "My Actions" widget<br>3. Check for pending actions/leave requests | N/A | Widget displays pending actions or "No Records Found" message | Not Executed |

---

## Employee Management - PIM Module (8 Test Cases)

| Test Case ID | Test Scenario | Priority | Test Steps | Test Data | Expected Result | Status |
|--------------|---------------|----------|------------|-----------|-----------------|--------|
| **TC_011** | Verify Navigation to PIM Module | P1 | 1. Login to application<br>2. Click on "PIM" in left navigation menu<br>3. Verify page loads | N/A | PIM page displays with employee list and search options | Not Executed |
| **TC_012** | Verify Add New Employee with Mandatory Fields | P0 | 1. Navigate to PIM > Add Employee<br>2. Enter First Name: "John"<br>3. Enter Last Name: "Doe"<br>4. Click "Save" button | FirstName: John<br>LastName: Doe | Employee is created successfully and confirmation message appears | Not Executed |
| **TC_013** | Verify Add Employee with All Fields | P1 | 1. Navigate to PIM > Add Employee<br>2. Enter First Name: "Jane"<br>3. Enter Middle Name: "Marie"<br>4. Enter Last Name: "Smith"<br>5. Enter Employee ID: "12345"<br>6. Click "Save" button | FirstName: Jane<br>MiddleName: Marie<br>LastName: Smith<br>ID: 12345 | Employee is created with all details saved correctly | Not Executed |
| **TC_014** | Verify Add Employee Without Mandatory Fields | P1 | 1. Navigate to PIM > Add Employee<br>2. Leave First Name empty<br>3. Leave Last Name empty<br>4. Click "Save" button | N/A | Validation error messages appear for required fields | Not Executed |
| **TC_015** | Verify Search Employee by Name | P1 | 1. Navigate to PIM<br>2. Enter employee name in "Employee Name" field<br>3. Click "Search" button | Employee Name: (existing employee) | Employee record(s) matching search criteria are displayed | Not Executed |
| **TC_016** | Verify Search Employee by ID | P1 | 1. Navigate to PIM<br>2. Enter employee ID in "Employee Id" field<br>3. Click "Search" button | Employee ID: (existing ID) | Specific employee record is displayed | Not Executed |
| **TC_017** | Verify Edit Employee Information | P1 | 1. Navigate to PIM<br>2. Click on an employee record<br>3. Click edit icon<br>4. Modify employee details (e.g., middle name)<br>5. Click "Save" button | N/A | Employee information is updated successfully with confirmation | Not Executed |
| **TC_018** | Verify Delete Employee Record | P1 | 1. Navigate to PIM<br>2. Select employee record checkbox<br>3. Click "Delete" button<br>4. Confirm deletion in popup | N/A | Employee record is deleted and removed from the list | Not Executed |

---

## Logout Module (3 Test Cases)

| Test Case ID | Test Scenario | Priority | Test Steps | Test Data | Expected Result | Status |
|--------------|---------------|----------|------------|-----------|-----------------|--------|
| **TC_019** | Verify Successful Logout | P0 | 1. Login to application<br>2. Click on user profile dropdown (top right)<br>3. Click "Logout" option | N/A | User is logged out and redirected to login page | Not Executed |
| **TC_020** | Verify Session Expires After Logout | P1 | 1. Login to application<br>2. Logout from application<br>3. Press browser back button | N/A | User cannot access dashboard, remains on login page | Not Executed |
| **TC_021** | Verify Multiple Logout Clicks | P3 | 1. Login to application<br>2. Click logout<br>3. Quickly click logout multiple times | N/A | Application handles gracefully without errors, redirects to login | Not Executed |

---

## Negative/Edge Cases (4 Test Cases)

| Test Case ID | Test Scenario | Priority | Test Steps | Test Data | Expected Result | Status |
|--------------|---------------|----------|------------|-----------|-----------------|--------|
| **TC_022** | Verify XSS Attack Prevention in Login | P1 | 1. Navigate to login page<br>2. Enter username: "&lt;script&gt;alert('XSS')&lt;/script&gt;"<br>3. Enter password: "admin123"<br>4. Click "Login" button | Username: &lt;script&gt;alert('XSS')&lt;/script&gt;<br>Password: admin123 | Script is not executed, treated as regular text | Not Executed |
| **TC_023** | Verify Maximum Character Input in Employee Name | P2 | 1. Navigate to PIM > Add Employee<br>2. Enter 500 characters in First Name field<br>3. Enter Last Name: "Test"<br>4. Click "Save" button | FirstName: (500 characters)<br>LastName: Test | System either accepts with limit or shows validation error | Not Executed |
| **TC_024** | Verify Special Characters in Employee Name | P2 | 1. Navigate to PIM > Add Employee<br>2. Enter First Name: "@#$%^&*()"<br>3. Enter Last Name: "Test"<br>4. Click "Save" button | FirstName: @#$%^&*()<br>LastName: Test | System validates and shows appropriate error or accepts valid characters | Not Executed |
| **TC_025** | Verify Application Behavior on Session Timeout | P2 | 1. Login to application<br>2. Leave application idle for extended period (30+ minutes)<br>3. Attempt to perform any action | N/A | Session timeout message appears, user redirected to login | Not Executed |

---

## Priority Definitions

| Priority | Description | Action Required |
|----------|-------------|-----------------|
| **P0** | Critical - Must be tested before any release | Execute immediately, blocks release if failed |
| **P1** | High - Should be tested in current cycle | Execute in current sprint |
| **P2** | Medium - Important but not critical | Execute when P0/P1 complete |
| **P3** | Low - Nice to have | Execute if time permits |

---

## Test Coverage Summary

| Module | Test Cases | Percentage |
|--------|-----------|------------|
| Login Module | 6 | 24% |
| Dashboard Module | 4 | 16% |
| Employee Management (PIM) | 8 | 32% |
| Logout Module | 3 | 12% |
| Negative/Edge Cases | 4 | 16% |
| **Total** | **25** | **100%** |

---

## Notes

- **Application URL:** https://opensource-demo.orangehrmlive.com/
- **Test Credentials:** Username: `Admin`, Password: `admin123`
- **Tester:** Olajide Abiodun


### Legend

- **P0:** Blocker - Must pass
- **P1:** Critical - High priority
- **P2:** Major - Medium priority
- **P3:** Minor - Low priority
- **N/A:** Not Applicable