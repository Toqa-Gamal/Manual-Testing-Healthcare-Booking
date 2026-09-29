# Healthcare Clinic Booking Platform — Manual Testing

### QA Work Portfolio | REQ-FUN-05 Patient Details & Promo Code Engine

A manual testing project for a healthcare clinic booking platform, completed as part of the **DEPI Software Testing Track** with the **Bug Hunters** team.

The project covered the complete manual testing workflow — from SRS analysis and test design to peer review, test execution, and bug reporting using **Jira**.

---

## 📌 Project Snapshot

- **Team:** Bug Hunters — 4 Testers
- **Testing Type:** Manual Testing
- **Tool:** Jira
- **Requirements Covered:** 7 Functional Requirements
- **Main Requirement:** REQ-FUN-05 — Patient Details & Promo Code Engine

### My Contribution

- **39** test cases designed for REQ-FUN-05
- **8** bugs reported in Jira
- **4** Jira tasks completed
- **2** peer reviews performed
- Test case execution and defect verification
- Requirement analysis and team discussions

---

## 🎯 What I Worked On

| Area | My Contribution |
|---|---|
| Requirements Analysis | Analyzed all 7 functional requirements in the SRS and participated in team discussions to understand the complete booking flow. |
| Test Design | Owned REQ-FUN-05 and designed 39 test cases covering positive, negative, boundary, validation, and edge-case scenarios. |
| Peer Review | Reviewed test cases for REQ-FUN-03 and REQ-FUN-04. |
| Test Execution | Executed my test cases against the application and documented failures. |
| Bug Reporting | Reported 8 defects in Jira with reproduction steps, expected vs actual results, and severity. |
| Defect Lifecycle | Followed the simulated fix → resolve → retest → close/reopen workflow. |

---

## 🔍 Requirement Under Test

### REQ-FUN-05 — Patient Details & Promo Code Engine

> As a logged-in patient, I want to enter patient details and apply promo codes to calculate the final consultation price.

### Requirement Rules

#### Patient Selection

- **Booking for Myself** is selected by default.
- Patient can switch to **Booking for Someone Else**.
- When booking for someone else:
  - Beneficiary name is required.
  - Beneficiary phone number is required.

#### Beneficiary Name

- Alphabetic characters and spaces only.
- Length: **3–50 characters**.
- Boundary cases below and above the allowed range were tested.

#### Beneficiary Phone

- Must follow the **11-digit Egyptian phone number format**.
- Valid prefixes tested:
  - `010`
  - `011`
  - `012`
  - `015`

#### Promo Code

- Maximum length: **15 characters**.
- Supports alphanumeric characters and hyphens.
- Input should be:
  - Trimmed.
  - Normalized to uppercase.
- One promo code can be applied per booking session.

### Valid Promo Codes

| Promo Code | Expected Discount |
|---|---:|
| `SAVE10` | 10% |
| `FLAT50` | 50 EGP |
| `BEST-QA` | 100% — total becomes 0 EGP |

### Validation

For an unrecognized promo code:

`Invalid or expired promo code.`

The final consultation price must never become less than **0 EGP**.

---

## 🧪 Test Design

I designed **39 test cases** for REQ-FUN-05 covering positive, negative, boundary, validation, and edge-case scenarios.

| Area | Count | Scenarios Covered |
|---|---:|---|
| Patient Selection | 3 | Default selection, switching beneficiary, end-to-end booking |
| Beneficiary Name | 7 | Valid values, 2/51-character boundaries, spaces, digits, symbols |
| Beneficiary Phone | 7 | Valid prefixes, invalid prefix, length, letters, symbols |
| Valid Promo Codes | 4 | SAVE10, FLAT50, BEST-QA, discount/message validation |
| Promo Case & Hyphens | 5 | Mixed-case and hyphenated variants |
| Promo Trimming | 3 | Leading and trailing spaces |
| Invalid Promo Input | 5 | Empty input, special characters, unknown codes |
| Promo Length | 3 | 14, 15, and 16-character inputs |
| One Promo per Session | 1 | Apply button behavior after applying a code |
| Fee Floor | 1 | Total cannot fall below 0 EGP |

**Total: 39 test cases**

---

## 🐞 Bug Reporting

During test execution, I identified and reported **8 defects** in Jira.

Each defect included:

- Reproduction steps
- Expected result
- Actual result
- Severity
- Requirement linkage
- Relevant test case

| Jira ID | Defect Summary | Severity |
|---|---|---|
| HL-133 | Beneficiary Name accepts 51 characters | Medium |
| HL-134 | BESTQA rejected as invalid code | High |
| HL-135 | SAVE-10 rejected although hyphens should be accepted | Medium |
| HL-136 | FLAT-50 rejected although hyphens should be accepted | Medium |
| HL-137 | BEST-QA treated as already applied on first use | High |
| HL-138 | Mixed-case promo code rejected | Medium |
| HL-139 | Spaces around BESTQA are not trimmed | High |
| HL-140 | Promo field limited to 10 characters instead of 15 | Low |

### Bug Severity Distribution

- **3 High**
- **4 Medium**
- **1 Low**

---
