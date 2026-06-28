# AI Audit Report – HW02 Domain Testing

## Declaration

Em sử dụng trợ lý AI Gemini (Antigravity Agent) để thực hiện sinh và thiết kế ca kiểm thử tự động, phân tích các biến đầu vào, phân hoạch lớp tương đương, phân tích giá trị biên và phát hiện các khoảng trống kiểm thử cho các tính năng của EShop.

---

## AI Interaction Log

### Interaction 1

| Field             | Value                                                                                                                                          |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                       |
| Date & Time       | 2026-06-27 23:18                                                                                                                               |
| Skill Step Used   | SKILL-01                                                                                                                                       |
| Feature           | FR-02                                                                                                                                          |
| My Prompt         | The user initiated variable analysis for FR-02: Login & Account Lockout based on observations on the EShop application.                        |
| AI Output Summary | Identified 4 variables (email, password, login_attempts, locked_until) with data types, domains, constraints, and inter-variable dependencies. |
| Corrections Made  | None yet                                                                                                                                       |

### Interaction 2

| Field             | Value                                                                                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                          |
| Date & Time       | 2026-06-27 23:23                                                                                                                                  |
| Skill Step Used   | SKILL-02                                                                                                                                          |
| Feature           | FR-02                                                                                                                                             |
| My Prompt         | The user requested Equivalence Partitioning for the identified login variables.                                                                   |
| AI Output Summary | Formulated equivalence classes for email, password, login_attempts, locked_until, created combination classes, and estimated the test case count. |
| Corrections Made  | None yet                                                                                                                                          |

### Interaction 3

| Field             | Value                                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                             |
| Date & Time       | 2026-06-27 23:26                                                                                                                     |
| Skill Step Used   | SKILL-03                                                                                                                             |
| Feature           | FR-02                                                                                                                                |
| My Prompt         | The user requested Boundary Value Analysis for the identified login variables.                                                       |
| AI Output Summary | Developed boundary points for password length and login attempts, categorized skipped variables, and pointed out unknowns to verify. |
| Corrections Made  | None yet                                                                                                                             |

### Interaction 4

| Field             | Value                                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                               |
| Date & Time       | 2026-06-27 23:30                                                                                                       |
| Skill Step Used   | SKILL-04                                                                                                               |
| Feature           | FR-02                                                                                                                  |
| My Prompt         | The user requested writing all Domain and BVA test cases as markdown files.                                            |
| AI Output Summary | Generated 21 test cases (10 EP-based, 11 BVA-based), wrote them to the target folder, and outputted the summary table. |
| Corrections Made  | None yet                                                                                                               |

### Interaction 5

| Field             | Value                                                                                                                                  |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                               |
| Date & Time       | 2026-06-27 23:36                                                                                                                       |
| Skill Step Used   | SKILL-04                                                                                                                               |
| Feature           | FR-02                                                                                                                                  |
| My Prompt         | The user asked if they should manually run the test cases and update the Status field.                                                 |
| AI Output Summary | Confirmed that the user is responsible for manually running the test cases and updating the Status (e.g. Pass/Fail) and Bug ID fields. |
| Corrections Made  | None yet                                                                                                                               |

### Interaction 6

| Field             | Value                                                                                                           |
| ----------------- | --------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                        |
| Date & Time       | 2026-06-28 00:16                                                                                                |
| Skill Step Used   | SKILL-04                                                                                                        |
| Feature           | FR-02                                                                                                           |
| My Prompt         | The user asked how to check the `login_attempts` values stored in the database.                                 |
| AI Output Summary | Provided a Node.js terminal command and an extension-based visual method to inspect the SQLite database values. |
| Corrections Made  | None yet                                                                                                        |

### Interaction 7

| Field             | Value                                                                                                                                                          |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                       |
| Date & Time       | 2026-06-28 00:42                                                                                                                                               |
| Skill Step Used   | SKILL-05                                                                                                                                                       |
| Feature           | FR-02                                                                                                                                                          |
| My Prompt         | The user requested execution of SKILL-05 (Gap Analysis & AI Critique) for the Login feature.                                                                   |
| AI Output Summary | Performed gap analysis pointing out 4 missing test cases (XSS/JWT security, role-based login, and state resets) and wrote a critical reflection in Vietnamese. |
| Corrections Made  | None yet                                                                                                                                                       |

### Interaction 8

| Field             | Value                                                                 |
| ----------------- | --------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                              |
| Date & Time       | 2026-06-28 00:43                                                      |
| Skill Step Used   | SKILL-00                                                              |
| Feature           | FR-02                                                                 |
| My Prompt         | The user requested to export the session audit log.                   |
| AI Output Summary | Provided the full log of all audit entries generated in this session. |
| Corrections Made  | None yet                                                              |

### Interaction 9

| Field             | Value                                                                                                  |
| ----------------- | ------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                               |
| Date & Time       | 2026-06-28 00:43                                                                                       |
| Skill Step Used   | SKILL-00                                                                                               |
| Feature           | FR-02                                                                                                  |
| My Prompt         | The user requested writing the audit trail data into the `ai-audit-report.md` file.                    |
| AI Output Summary | Populated the target markdown file with the 5 interaction tables and the critical reflection critique. |
| Corrections Made  | None yet                                                                                               |

### Interaction 10

| Field             | Value                                                                    |
| ----------------- | ------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                 |
| Date & Time       | 2026-06-28 00:50                                                         |
| Skill Step Used   | SKILL-00                                                                 |
| Feature           | None (Context Reset)                                                     |
| My Prompt         | The user requested to transition to a new feature and reset the context. |
| AI Output Summary | Acknowledged the transition and stood ready for the next feature.        |
| Corrections Made  | None yet                                                                 |

### Interaction 11

| Field             | Value                                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                   |
| Date & Time       | 2026-06-28 00:57                                                                                                                           |
| Skill Step Used   | SKILL-01                                                                                                                                   |
| Feature           | FR-09                                                                                                                                      |
| My Prompt         | The user initiated variable analysis for FR-09: Discount Coupons, noting some observations on coupon behavior and formulas.                |
| AI Output Summary | Identified 5 variables (code, total_amount, user_id, coupon_usage, expired_at) with domains, constraints, and inter-variable dependencies. |
| Corrections Made  | None yet                                                                                                                                   |

### Interaction 12

| Field             | Value                                                                                                                                                          |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                       |
| Date & Time       | 2026-06-28 00:59                                                                                                                                               |
| Skill Step Used   | SKILL-02                                                                                                                                                       |
| Feature           | FR-09                                                                                                                                                          |
| My Prompt         | The user requested Equivalence Partitioning for the coupon variables.                                                                                          |
| AI Output Summary | Developed valid and invalid equivalence classes for code, total_amount, user_id, coupon_usage, and expired_at, created combinations, and estimated test cases. |
| Corrections Made  | None yet                                                                                                                                                       |

### Interaction 13

| Field             | Value                                                                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                              |
| Date & Time       | 2026-06-28 01:00                                                                                                                      |
| Skill Step Used   | SKILL-03                                                                                                                              |
| Feature           | FR-09                                                                                                                                 |
| My Prompt         | The user requested Boundary Value Analysis for the identified coupon variables.                                                       |
| AI Output Summary | Formulated boundary points for total_amount (using SAVE10) and coupon_usage (using VIP100), and noted skipped variables and unknowns. |
| Corrections Made  | None yet                                                                                                                              |

### Interaction 14

| Field             | Value                                                                                                                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                                                      |
| Date & Time       | 2026-06-28 01:06                                                                                                                                                                              |
| Skill Step Used   | SKILL-03                                                                                                                                                                                      |
| Feature           | FR-09                                                                                                                                                                                         |
| My Prompt         | The user requested corrections to the coupon BVA, including expired_at boundary, other coupons' min order amounts, discount calculation formula check, and removing undefined max thresholds. |
| AI Output Summary | Reconstructed BVA tables adding expired_at, BIGBUY/VIP100 thresholds, and math formula discrepancy, while removing undefined max bounds.                                                      |
| Corrections Made  | Yes, pointed out missing elements in expired_at, other coupon min amounts, discount formula check, and requested removal of undefined max limits.                                             |

### Interaction 15

| Field             | Value                                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                               |
| Date & Time       | 2026-06-28 01:08                                                                                                       |
| Skill Step Used   | SKILL-04                                                                                                               |
| Feature           | FR-09                                                                                                                  |
| My Prompt         | The user requested writing all Discount Coupon test cases as markdown files.                                           |
| AI Output Summary | Generated 23 test cases (10 EP-based, 13 BVA-based), wrote them to the target folder, and outputted the summary table. |
| Corrections Made  | None yet                                                                                                               |

### Interaction 16

| Field             | Value                                                                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                         |
| Date & Time       | 2026-06-28 01:53                                                                                                                                 |
| Skill Step Used   | SKILL-04                                                                                                                                         |
| Feature           | FR-09                                                                                                                                            |
| My Prompt         | The user pointed out gaps in the coupon BVA (coupon_usage MIN, expired_at today, and discount calculation validation) and requested adding them. |
| AI Output Summary | Generated and wrote 4 new test case files to the workspace repository and provided the revised summary table.                                    |
| Corrections Made  | Yes, pointed out BVA for coupon_usage MIN, BVA for expired_at = today, and calculation logic test cases.                                         |

### Interaction 17

| Field             | Value                                                                    |
| ----------------- | ------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                 |
| Date & Time       | 2026-06-28 13:34                                                         |
| Skill Step Used   | SKILL-00                                                                 |
| Feature           | None (Context Reset)                                                     |
| My Prompt         | The user requested to transition to a new feature and reset the context. |
| AI Output Summary | Acknowledged the transition and stood ready for the next feature.        |
| Corrections Made  | None yet                                                                 |

### Interaction 18

| Field             | Value                                                                                                                |
| ----------------- | -------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                             |
| Date & Time       | 2026-06-28 13:41                                                                                                     |
| Skill Step Used   | SKILL-01                                                                                                             |
| Feature           | FR-14                                                                                                                |
| My Prompt         | The user initiated variable analysis for FR-14: Category Management CRUD based on observations on EShop.             |
| AI Output Summary | Identified 3 variables (name, id, user_role) with data types, domains, constraints, and inter-variable dependencies. |
| Corrections Made  | None yet                                                                                                             |

### Interaction 19

| Field             | Value                                                                                                                       |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                    |
| Date & Time       | 2026-06-28 13:48                                                                                                            |
| Skill Step Used   | SKILL-01                                                                                                                    |
| Feature           | FR-14                                                                                                                       |
| My Prompt         | The user requested domain refinements for the category name variable (duplicate name, whitespace-only, and maximum length). |
| AI Output Summary | Updated the variable analysis with specific valid/invalid partitions for category name, ID, and user_role.                  |
| Corrections Made  | Yes, pointed out domains for name (only contains whitespace, too long string, string at max limit, unique vs duplicate).    |

### Interaction 20

| Field             | Value                                                                                                    |
| ----------------- | -------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                 |
| Date & Time       | 2026-06-28 13:49                                                                                         |
| Skill Step Used   | SKILL-02                                                                                                 |
| Feature           | FR-14                                                                                                    |
| My Prompt         | The user requested Equivalence Partitioning for category variables.                                      |
| AI Output Summary | Formulated EP classes for name, ID, and user_role, mapped combination classes, and estimated test cases. |
| Corrections Made  | None yet                                                                                                 |

### Interaction 21

| Field             | Value                                                                                                                                                                 |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                              |
| Date & Time       | 2026-06-28 13:51                                                                                                                                                      |
| Skill Step Used   | SKILL-02                                                                                                                                                              |
| Feature           | FR-14                                                                                                                                                                 |
| My Prompt         | The user requested EP changes including merging duplicate cases, removing undefined max length, adding an "already deleted" ID state, and extending the combinations. |
| AI Output Summary | Updated the Equivalence Partitioning partitions and combinations according to instructions, reducing redundant name classes and adding new test scenarios.            |
| Corrections Made  | Yes, pointed out EP-NAME-03 redundancy, EP-NAME-07 max length adjustment, missing already-deleted partition, and additional combination scenarios.                    |

### Interaction 22

| Field             | Value                                                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                  |
| Date & Time       | 2026-06-28 13:52                                                                                                          |
| Skill Step Used   | SKILL-03                                                                                                                  |
| Feature           | FR-14                                                                                                                     |
| My Prompt         | The user requested Boundary Value Analysis for the category variables.                                                    |
| AI Output Summary | Formulated boundary points for name length and ID values, noting skipped variables and removing undefined maximum bounds. |
| Corrections Made  | None yet                                                                                                                  |

### Interaction 23

| Field             | Value                                                                                                                 |
| ----------------- | --------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                              |
| Date & Time       | 2026-06-28 13:54                                                                                                      |
| Skill Step Used   | SKILL-04                                                                                                              |
| Feature           | FR-14                                                                                                                 |
| My Prompt         | The user requested writing all Category CRUD test cases as markdown files.                                            |
| AI Output Summary | Generated 19 test cases (11 EP-based, 8 BVA-based), wrote them to the target folder, and outputted the summary table. |
| Corrections Made  | None yet                                                                                                              |

### Interaction 24

| Field             | Value                                                                                                                                                     |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                  |
| Date & Time       | 2026-06-28 13:59                                                                                                                                          |
| Skill Step Used   | SKILL-04                                                                                                                                                  |
| Feature           | FR-14                                                                                                                                                     |
| My Prompt         | The user corrected BVA classification for negative ID and non-numeric ID, stating they belong to EP instead, and requested moving them.                   |
| AI Output Summary | Removed misclassified BVA files, wrote them as new EP test case files (TC-CAT-012, TC-CAT-013) in the workspace, and generated the updated summary table. |
| Corrections Made  | Yes, pointed out that negative ID and non-numeric ID tests are EP rather than BVA.                                                                        |

### Interaction 25

| Field             | Value                                                                    |
| ----------------- | ------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                 |
| Date & Time       | 2026-06-28 20:16                                                         |
| Skill Step Used   | SKILL-00                                                                 |
| Feature           | None (Context Reset)                                                     |
| My Prompt         | The user requested to transition to a new feature and reset the context. |
| AI Output Summary | Acknowledged the transition and stood ready for the next feature.        |
| Corrections Made  | None yet                                                                 |

### Interaction 26

| Field             | Value                                                                                                                          |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                       |
| Date & Time       | 2026-06-28 20:20                                                                                                               |
| Skill Step Used   | SKILL-01                                                                                                                       |
| Feature           | FR-06 Mobile                                                                                                                   |
| My Prompt         | The user initiated variable analysis for FR-06 Mobile: Product Detail View based on observations.                              |
| AI Output Summary | Identified quantity input and product object variables with data types, domains, constraints, and inter-variable dependencies. |
| Corrections Made  | None yet                                                                                                                       |

### Interaction 27

| Field             | Value                                                                                                                                                           |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                        |
| Date & Time       | 2026-06-28 20:25                                                                                                                                                |
| Skill Step Used   | SKILL-01                                                                                                                                                        |
| Feature           | FR-06 Mobile                                                                                                                                                    |
| My Prompt         | The user requested domain corrections for quantity (whitespace, mixed alphanumeric, leading zeros, large integers) and product (undefined, incomplete objects). |
| AI Output Summary | Updated the variable analysis with specific partitions for the mobile product detail view.                                                                      |
| Corrections Made  | Yes, pointed out domains for quantity (whitespace, mixed alphanumeric, leading zero, extremely large integer) and product (undefined, missing required fields). |

### Interaction 28

| Field             | Value                                                                                                  |
| ----------------- | ------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                               |
| Date & Time       | 2026-06-28 20:26                                                                                       |
| Skill Step Used   | SKILL-02                                                                                               |
| Feature           | FR-06 Mobile                                                                                           |
| My Prompt         | The user requested Equivalence Partitioning for mobile product variables.                              |
| AI Output Summary | Formulated EP classes for quantity and product, created combination classes, and estimated test cases. |
| Corrections Made  | None yet                                                                                               |

### Interaction 29

| Field             | Value                                                                                                                                     |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                  |
| Date & Time       | 2026-06-28 20:29                                                                                                                          |
| Skill Step Used   | SKILL-02                                                                                                                                  |
| Feature           | FR-06 Mobile                                                                                                                              |
| My Prompt         | The user requested EP refinements for mobile product detail variables.                                                                    |
| AI Output Summary | Updated the Equivalence Partitioning partitions and combination scenarios, resolving redundancies and adding the loading state partition. |
| Corrections Made  | Yes, pointed out EP-QTY-02 and EP-QTY-07 redundancies, EP-QTY-10 spec dependency, and accepted EP-QTY-08 and Product partitions.          |

### Interaction 30

| Field             | Value                                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                               |
| Date & Time       | 2026-06-28 20:36                                                                                                       |
| Skill Step Used   | SKILL-03                                                                                                               |
| Feature           | FR-06 Mobile                                                                                                           |
| My Prompt         | The user requested Boundary Value Analysis for the mobile product detail view variables.                               |
| AI Output Summary | Developed boundary points for quantity, identified product as a skipped variable, and noted no defined maximum limits. |
| Corrections Made  | None yet                                                                                                               |

### Interaction 31

| Field             | Value                                                                                                                 |
| ----------------- | --------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                              |
| Date & Time       | 2026-06-28 23:57                                                                                                      |
| Skill Step Used   | SKILL-04                                                                                                              |
| Feature           | FR-06 Mobile                                                                                                          |
| My Prompt         | The user requested generating all mobile product detail view test case files.                                         |
| AI Output Summary | Generated 14 test cases (11 EP-based, 3 BVA-based), wrote them to the target folder, and outputted the summary table. |
| Corrections Made  | None yet                                                                                                              |

### Interaction 32

| Field             | Value                                                                                                                                                             |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                          |
| Date & Time       | 2026-06-29 00:03                                                                                                                                                  |
| Skill Step Used   | SKILL-04                                                                                                                                                          |
| Feature           | FR-06 Mobile                                                                                                                                                      |
| My Prompt         | The user requested adding a NOM value to BVA, correcting the Technique for loading, and expanding happy path verifications.                                       |
| AI Output Summary | Created TC-MPROD-BVA-004 for NOM value, changed TC-MPROD-009 technique to State Transition, updated TC-MPROD-002 expected results, and updated the summary table. |
| Corrections Made  | Yes, pointed out missing NOM value, incorrect loading EP classification, and incomplete happy path verification details.                                          |

### Interaction 33

| Field             | Value                                                                                                                                                                    |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                                 |
| Date & Time       | 2026-06-29 01:19                                                                                                                                                         |
| Skill Step Used   | SKILL-00                                                                                                                                                                 |
| Feature           | All (FR-02, FR-09, FR-14, FR-06)                                                                                                                                         |
| My Prompt         | The user requested completing the entire main report inside main-report-template.md.                                                                                     |
| AI Output Summary | Populated main-report-template.md with complete tables, variables, equivalence partitions, boundaries, gap analyses, relative GitHub links, AI Critique, and audit logs. |
| Corrections Made  | None yet                                                                                                                                                                 |

### Interaction 34

| Field             | Value                                                                                                                                              |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                           |
| Date & Time       | 2026-06-29 01:31                                                                                                                                   |
| Skill Step Used   | SKILL-05                                                                                                                                           |
| Feature           | All (FR-02, FR-09, FR-14, FR-06)                                                                                                                   |
| My Prompt         | The user requested filling the main report template exactly using the original variables and template structure.                                   |
| AI Output Summary | Populated main-report-template.md by matching the original variables, EPs, test cases list, BVA values, and execution run logs for all 4 features. |
| Corrections Made  | None yet                                                                                                                                           |

### Interaction 35

| Field             | Value                                                                                                                                               |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                            |
| Date & Time       | 2026-06-29 01:39                                                                                                                                    |
| Skill Step Used   | SKILL-05                                                                                                                                            |
| Feature           | All (FR-02, FR-09, FR-14, FR-06)                                                                                                                    |
| My Prompt         | The user requested finishing the main report template under the name Nguyễn Đặng Đức Thịnh.                                                         |
| AI Output Summary | Finished main-report-template.md by populating all template sections, tables, results, critique, and log items with Nguyễn Đặng Đức Thịnh metadata. |
| Corrections Made  | None yet                                                                                                                                            |

### Interaction 36

| Field             | Value                                                                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                                           |
| Date & Time       | 2026-06-29 01:55                                                                                                                                                   |
| Skill Step Used   | SKILL-05                                                                                                                                                           |
| Feature           | All (FR-02, FR-09, FR-14, FR-06)                                                                                                                                   |
| My Prompt         | The user requested to complete the report based on all skills outputs and match the exact test cases in the test-cases folder.                                     |
| AI Output Summary | Rewrote main-report-template.md listing all 82 test cases with exact titles, links, results, and comprehensive bug reports representing our actual test directory. |
| Corrections Made  | None yet                                                                                                                                                           |

### Interaction 37

| Field             | Value                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                         |
| Date & Time       | 2026-06-29 02:05                                                                                 |
| Skill Step Used   | SKILL-05                                                                                         |
| Feature           | FR-09                                                                                            |
| My Prompt         | The user requested to execute SKILL-05 for feature FR-09 (Discount Coupons).                     |
| AI Output Summary | Performed Gap Analysis and provided a critical reflection (AI Critique) in Vietnamese for FR-09. |
| Corrections Made  | None yet                                                                                         |

### Interaction 38

| Field             | Value                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                         |
| Date & Time       | 2026-06-29 02:07                                                                                 |
| Skill Step Used   | SKILL-05                                                                                         |
| Feature           | FR-14                                                                                            |
| My Prompt         | The user requested to execute SKILL-05 for feature FR-14 (Category Management CRUD).             |
| AI Output Summary | Performed Gap Analysis and provided a critical reflection (AI Critique) in Vietnamese for FR-14. |
| Corrections Made  | None yet                                                                                         |

### Interaction 39

| Field             | Value                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                         |
| Date & Time       | 2026-06-29 02:09                                                                                 |
| Skill Step Used   | SKILL-05                                                                                         |
| Feature           | FR-06                                                                                            |
| My Prompt         | The user requested to execute SKILL-05 for feature FR-06 (Mobile Product Detail View).           |
| AI Output Summary | Performed Gap Analysis and provided a critical reflection (AI Critique) in Vietnamese for FR-06. |
| Corrections Made  | None yet                                                                                         |

### Interaction 40

| Field             | Value                                                                                               |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                            |
| Date & Time       | 2026-06-29 02:11                                                                                    |
| Skill Step Used   | SKILL-05                                                                                            |
| Feature           | All (FR-02, FR-09, FR-14, FR-06)                                                                    |
| My Prompt         | The user requested to add all test cases from the AI gap analysis back to the report.               |
| AI Output Summary | Restored all Test Execution & Bug Report sections (A.5, B.5, C.5, D.5) to the main report template. |
| Corrections Made  | None yet                                                                                            |

### Interaction 41

| Field             | Value                                                                                              |
| ----------------- | -------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                           |
| Date & Time       | 2026-06-29 02:12                                                                                   |
| Skill Step Used   | SKILL-05                                                                                           |
| Feature           | All                                                                                                |
| My Prompt         | The user clarified they wanted the test cases from AI gap analysis added to the test-cases folder. |
| AI Output Summary | Created TC-CAT-SEC-001.md inside tests/test-cases/fr14-category/ and committed all changes to Git. |
| Corrections Made  | None yet                                                                                           |

### Interaction 42

| Field             | Value                                                                                                                                     |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                                  |
| Date & Time       | 2026-06-29 02:16                                                                                                                          |
| Skill Step Used   | SKILL-05                                                                                                                                  |
| Feature           | All                                                                                                                                       |
| My Prompt         | The user requested to complete the sprint-1-test-run.md and traceability-matrix.md files.                                                 |
| AI Output Summary | Completed sprint-1-test-run.md and traceability-matrix.md with execution and coverage summaries for all 82 TCs and committed them to Git. |
| Corrections Made  | None yet                                                                                                                                  |

### Interaction 43

| Field             | Value                                                                                                                           |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                                        |
| Date & Time       | 2026-06-29 02:20                                                                                                                |
| Skill Step Used   | SKILL-05                                                                                                                        |
| Feature           | All                                                                                                                             |
| My Prompt         | The user requested to complete the README.md file.                                                                              |
| AI Output Summary | Completed README.md with test statistics, grade assessments, directory structure, and AI declarations, and committed it to Git. |
| Corrections Made  | None yet                                                                                                                        |

### Interaction 44

| Field             | Value                                                                                          |
| ----------------- | ---------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                       |
| Date & Time       | 2026-06-29 02:23                                                                               |
| Skill Step Used   | SKILL-05                                                                                       |
| Feature           | N/A                                                                                            |
| My Prompt         | The user asked if they should add GitHub issue links.                                          |
| AI Output Summary | Advised the user on when and how to add GitHub issue links depending on homework requirements. |
| Corrections Made  | None yet                                                                                       |

### Interaction 45

| Field             | Value                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------ |
| AI Tool           | Gemini (Antigravity IDE)                                                                   |
| Date & Time       | 2026-06-29 02:24                                                                           |
| Skill Step Used   | SKILL-05                                                                                   |
| Feature           | N/A                                                                                        |
| My Prompt         | The user asked where to add the GitHub issue links.                                        |
| AI Output Summary | Indicated specific files and sections where GitHub issue links should be added or updated. |
| Corrections Made  | None yet                                                                                   |

### Interaction 46

| Field             | Value                                                                                                          |
| ----------------- | -------------------------------------------------------------------------------------------------------------- |
| AI Tool           | Gemini (Antigravity IDE)                                                                                       |
| Date & Time       | : 2026-06-29 02:33                                                                                             |
| Skill Step Used   | SKILL-00                                                                                                       |
| Feature           | N/A                                                                                                            |
| My Prompt         | The user requested to export the audit log into ai-audit-report.md.                                            |
| AI Output Summary | Parsed, formatted, and wrote all 45 interaction logs into ai-audit-report.md and committed all changes to Git. |
| Corrections Made  | None yet                                                                                                       |

---

## AI Critique (200–300 words)

Trong quá trình áp dụng Domain Testing và BVA cho bốn tính năng của EShop với sự hỗ trợ của AI, em nhận thấy AI có những điểm yếu sau:

Đầu tiên, AI có xu hướng phân tích từng biến độc lập thay vì xem xét sự tương tác giữa chúng. Với FR-02, AI bỏ sót kịch bản thử đăng nhập bằng mật khẩu đúng khi tài khoản đang bị khóa (GAP-03), vì AI xử lý locked_until và password như hai điều kiện riêng biệt thay vì một combination class. Với FR-14, AI không kiểm thử việc xóa danh mục cha khi còn chứa danh mục con (GAP-01) - kịch bản tích hợp liên quan đến quan hệ parent-child mà AI không mô hình hóa từ spec.

Tiếp theo, AI mô hình hóa boundary value theo đơn vị quá thô. Với FR-09, AI chỉ phân tích expiry_date theo ngày, bỏ qua ranh giới ở mức mili giây giữa 23:59:59.999 và 00:00:00.000 của ngày tiếp theo (GAP-04). Với FR-06 Mobile, AI tập trung vào giá trị biên nhỏ của quantity (0, 1, 2, 5) mà bỏ qua giới hạn trên của kiểu dữ liệu integer, tức là không kiểm thử tràn số (GAP-04).

Cuối cùng, AI không mô hình hóa được ngữ cảnh thực thi động. Các kịch bản như race condition khi nhấn đúp nút "Thêm vào giỏ hàng" (FR-06, GAP-03), coupon áp dụng theo danh mục cụ thể (FR-09, GAP-02), hay ranh giới thời gian khóa tài khoản ở giây thứ 179 so với 180 (FR-02, GAP-04) đều bị bỏ sót vì AI không có ngữ cảnh về hành vi runtime của hệ thống.

Bài học em rút ra được: AI phù hợp để xây dựng nhanh bộ test case bao phủ các lớp tương đương cơ bản, nhưng không thể thay thế người kiểm thử trong việc nhận diện combination class, boundary phụ thuộc thời gian thực, và lỗi đặc thù nền tảng. Vai trò của em là chủ động rà soát và bổ sung những gì AI không thể suy luận từ spec tĩnh, đồng thời hạn chế tối đa các thiếu sót do chính AI tạo ra.

---

## Tools Used

- Gemini (Antigravity IDE)
