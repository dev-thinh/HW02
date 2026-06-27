# SKILL-01 – Variable Analysis (Agent Version)

## Kích hoạt
Nói với agent: **"SKILL-01 [FR-XX: tên feature]"**

Ví dụ: `SKILL-01 FR-02: Login & Account Lockout`

---

## System instruction (load vào agent)

```
When the user says "SKILL-01 [feature]", execute the following:

TASK: Identify all input variables for the given feature on EShop SUT (https://github.com/ttbhanh/eshop-sut).

OUTPUT FORMAT — return exactly this structure, nothing else before the table:

### SKILL-01 Output: Variable Analysis
**Feature:** [feature name and ID]

| # | Variable | Data Type | Valid Domain | Invalid Domain | Constraints |
|---|----------|-----------|--------------|----------------|-------------|
| 1 | ... | ... | ... | ... | ... |

**Inter-variable dependencies:**
- [dependency 1]
- [dependency 2]

**Variables to BVA (ordered/numeric):** [list variables suitable for BVA]
**Variables EP-only (enum/boolean):** [list variables only needing EP]

---
> SKILL-01 complete. Tell me "SKILL-02" to partition these into equivalence classes, or "SKILL-03" to find boundary values.
```

---

## Ví dụ lệnh → output

**Bạn gõ:**
```
SKILL-01 FR-02: Login & Account Lockout
```

**Agent trả về:**
```
### SKILL-01 Output: Variable Analysis
Feature: FR-02: Login & Account Lockout

| # | Variable | Data Type | Valid Domain | Invalid Domain | Constraints |
|---|----------|-----------|--------------|----------------|-------------|
| 1 | email | string | Valid format, exists in DB | Wrong format, not in DB, empty | Required, max 255 chars |
| 2 | password | string | Correct password for account | Wrong password, empty | Required, min 6 chars |
| 3 | failed_attempts | integer | 0 to (threshold–1) | ≥ threshold | System-managed, not direct input |

Inter-variable dependencies:
- password only validated if email exists in DB
- failed_attempts increments only when email exists but password is wrong

Variables to BVA: password (length), failed_attempts (count)
Variables EP-only: email (format categories)

---
> SKILL-01 complete. Tell me "SKILL-02" to partition these into equivalence classes...
```

---

## Review checklist (bạn làm sau khi agent trả output)
- [ ] Có đủ tất cả field trên form/API không?
- [ ] Valid/Invalid domain có đúng với app thực tế không? (verify bằng cách chạy app)
- [ ] Dependencies có đúng không?
- [ ] Điền "User corrections" vào audit log
