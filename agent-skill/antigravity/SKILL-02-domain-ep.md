# SKILL-02 – Equivalence Partitioning (Agent Version)

## Kích hoạt
Nói với agent: **"SKILL-02"** (sau khi đã chạy SKILL-01 trong cùng session)

Agent tự lấy output SKILL-01 từ context, không cần paste lại.

---

## System instruction (load vào agent)

```
When the user says "SKILL-02", execute the following using the SKILL-01 output already in this conversation:

TASK: Apply Equivalence Partitioning to all variables from SKILL-01.

Rules:
- Each class = group of values the system treats IDENTICALLY
- Minimum: 1 VALID + 1 INVALID class per variable
- Always include: empty/null class for required fields
- Always include: special characters class for string fields
- Add COMBINATION classes for inter-variable dependencies

OUTPUT FORMAT — return exactly this structure:

### SKILL-02 Output: Equivalence Partitioning
**Feature:** [feature name]

| Class ID | Variable | Type | Description | Representative Value | Expected Behavior |
|----------|----------|------|-------------|---------------------|-------------------|
| EP-[VAR]-01 | ... | VALID | ... | ... | ... |
| EP-[VAR]-02 | ... | INVALID | ... | ... | ... |

**Combination classes:**
| Combo ID | Variables | Description | Expected Behavior |
|----------|-----------|-------------|-------------------|
| COMBO-01 | ... | ... | ... |

**TC count estimate:** [N] test cases will be needed to cover all classes

---
> SKILL-02 complete. Tell me "SKILL-03" for boundary values, or "SKILL-04" to write test case files.
```

---

## Ví dụ lệnh → output

**Bạn gõ:**
```
SKILL-02
```

**Agent trả về:**
```
### SKILL-02 Output: Equivalence Partitioning
Feature: FR-02: Login & Account Lockout

| Class ID | Variable | Type | Description | Representative Value | Expected Behavior |
|----------|----------|------|-------------|---------------------|-------------------|
| EP-EMAIL-01 | email | VALID | Correct format, exists in DB | user01@gmail.com | Proceed to check password |
| EP-EMAIL-02 | email | INVALID | Correct format, NOT in DB | ghost@gmail.com | Fail – generic error |
| EP-EMAIL-03 | email | INVALID | Wrong format | notanemail | Fail – format error |
| EP-EMAIL-04 | email | INVALID | Empty | "" | Fail – required field |
| EP-PASS-01 | password | VALID | Correct password | Abc@123456 | Login success |
| EP-PASS-02 | password | INVALID | Wrong password | WrongPass! | Fail – counter++ |
| EP-PASS-03 | password | INVALID | Empty | "" | Fail – required field |
| EP-LOCK-01 | failed_attempts | VALID | Below lockout threshold | 0 | Account active |
| EP-LOCK-02 | failed_attempts | INVALID | At/above threshold | N | Account locked |

Combination classes:
| Combo ID | Variables | Description | Expected Behavior |
|----------|-----------|-------------|-------------------|
| COMBO-01 | EP-EMAIL-01 + EP-PASS-01 + EP-LOCK-01 | Valid login | Login success |
| COMBO-02 | EP-EMAIL-01 + EP-PASS-02 + EP-LOCK-02 | Correct email, wrong pass, locked | Locked error shown |

TC count estimate: 11 test cases
```

---

## Review checklist
- [ ] Mỗi biến có ít nhất 1 VALID và 1 INVALID class
- [ ] Có class "empty" cho mọi required field
- [ ] Combination classes cover các inter-variable dependencies
- [ ] Representative values là giá trị thực tế dùng được ngay
- [ ] Điền "User corrections" vào audit log
