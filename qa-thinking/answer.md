# Part 3: QA Thinking

---

## Question 1: What Should Be Prioritized in Production Testing?

**Answer:**  
In production, testing time is limited and risk is high, so prioritization must focus on business impact and user risk.

### High Priority
- **Critical User Journeys:** Login, checkout, payment, core workflows
- **Data Integrity & Security:** User data protection, authentication, API security
- **Integrations:** Payment gateways, third-party APIs, notifications
- **Performance & Stability:** Page load times, API response times, system availability
- **Error Handling:** Proper error messages, logging, and monitoring

### Medium Priority
- Configuration and environment validation
- Session management and timeouts
- Monitoring dashboards and alerts

### Lower Priority
- Cosmetic UI issues
- Low-usage or non-critical features

**Approach:**  
I use a **risk-based and user-centric approach**, focusing first on what affects revenue, security, and the largest number of users.

---

## Question 2: Which Tests Should NOT Be Automated and Why?

**Answer:**  
Not all tests are suitable for automation. Some require human judgment and flexibility.

### Tests Best Kept Manual
- **Exploratory Testing**  
  Requires intuition and creativity to discover unknown issues.

- **Usability & UX Testing**  
  Automation cannot judge visual quality, intuitiveness, or user experience.

- **One-Time or Ad-hoc Tests**  
  Not cost-effective to automate scenarios that run once.

- **Frequently Changing UI**  
  Automation maintenance cost is high until the UI stabilizes.

- **Accessibility Testing (Partially)**  
  Some checks can be automated, but real accessibility requires human testing with assistive tools.

**Rule of Thumb:**  
Automate **stable, repetitive, high-risk tests**.  
Test manually when **human judgment adds more value than scripts**.

---

## Question 3: When Should a Bug Block a Release?

**Answer:**  
A bug should block a release when the risk of releasing is higher than the cost of delaying.

### Release-Blocking Bugs
- Security vulnerabilities
- Data loss or corruption
- Core functionality failures (login, payment, checkout)
- System crashes or severe performance issues
- Legal or compliance violations

### Non-Blocking Bugs
- Cosmetic UI issues
- Low-impact bugs with workarounds
- Issues affecting rarely used features

**Decision Factors:**
- Severity and user impact
- Number of users affected
- Availability of a workaround
- Business, legal, or reputational risk

I align release decisions with stakeholders using these factors to balance quality and delivery timelines.
