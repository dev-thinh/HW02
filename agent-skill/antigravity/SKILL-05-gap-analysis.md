# SKILL-05 – Gap Analysis & AI Critique (Agent Version)

## Kích hoạt
Nói với agent: **"SKILL-05"** (sau SKILL-04 trong cùng session)

---

## System instruction (load vào agent)

```
When the user says "SKILL-05", execute the following using all previous SKILL outputs in this conversation:

TASK A – Gap Detection:
Review all EP classes (SKILL-02), BVA boundaries (SKILL-03), and test cases (SKILL-04).
Find anything missing.

Check these 5 dimensions:
1. EP GAPS: Any equivalence class without a test case?
2. BVA GAPS: Any boundary point without a test case?
3. COMBINATION GAPS: Any inter-variable interaction not tested?
4. CONTEXT GAPS: EShop-specific scenarios missed?
   - Vietnamese locale / VND currency / UTF-8 input
   - Concurrent sessions (same user logged in on 2 browsers)
   - Mobile browser vs desktop
   - Admin role vs user role
5. SECURITY GAPS: Any security scenario missed?
   - SQL injection in input fields
   - XSS in string inputs
   - Brute-force after lockout (try again after reset)
   - Session token behavior after lockout

OUTPUT FORMAT for Task A:

### SKILL-05 Output: Gap Analysis
**Feature:** [feature name]

| Gap ID | Dimension | Missing Scenario | Why Missed | Proposed TC ID |
|--------|-----------|-----------------|------------|----------------|
| GAP-01 | Security | SQL injection in email field | Prompt did not mention security | TC-LOGIN-SEC-001 |

**Action required:** [list new TC files to create]

---

TASK B – AI Critique (for Section 10 of report):
Write a 200–300 word critical reflection in Vietnamese, first person, addressing:
1. Cụ thể AI bỏ sót điều gì trong session này (nêu tên class/boundary/scenario)
2. Tại sao AI bỏ sót (chất lượng prompt / giới hạn AI / độ phức tạp feature)
3. Bài học thực tế khi dùng AI để làm kiểm thử

Be specific and critical. Mention at least 2 concrete gaps found. Do not be generic.

Output Task B directly below Task A.

---
> SKILL-05 complete.
> Next steps:
> 1. Create additional TC files for any gaps worth covering
> 2. Commit: git commit -m "feat(fr02): add gap analysis test cases"
> 3. Say "export audit log" to get your AI Audit Report for this session
```

---

## Ví dụ lệnh → output

**Bạn gõ:**
```
SKILL-05
```

**Agent trả về:**
```
### SKILL-05 Output: Gap Analysis
Feature: FR-02: Login & Account Lockout

| Gap ID | Dimension | Missing Scenario | Why Missed | Proposed TC ID |
|--------|-----------|-----------------|------------|----------------|
| GAP-01 | Security | Email field SQL injection: ' OR 1=1 -- | Prompt không đề cập security | TC-LOGIN-SEC-001 |
| GAP-02 | Context | Login với email chứa ký tự Unicode/Vietnamese | Prompt không đề cập locale | TC-LOGIN-005 |
| GAP-03 | Combination | Account bị lockout rồi admin reset → thử login lại | Inter-state dependency bị bỏ qua | TC-LOGIN-006 |
| GAP-04 | BVA | Email dài đúng 255 ký tự (MAX length) | Không biết MAX length email field | TC-LOGIN-BVA-013 |

Action required: Create TC-LOGIN-SEC-001, TC-LOGIN-005, TC-LOGIN-006, TC-LOGIN-BVA-013

---

### AI Critique (Section 10)

Trong quá trình áp dụng Domain Testing và BVA cho FR-02, tôi nhận thấy AI bỏ sót một số test case đáng kể...

[200–300 từ tiếp theo...]
```

---

## Sau SKILL-05

```bash
# Tạo TC files cho các gaps quan trọng
git add tests/test-cases/fr02-login/
git commit -m "feat(fr02): add gap analysis TCs (security + context)"

# Lấy audit log
# Nói với agent: "export audit log"
```

## → Lặp lại từ SKILL-01 cho feature tiếp theo (FR-09, FR-14, FR-06 Mobile)
