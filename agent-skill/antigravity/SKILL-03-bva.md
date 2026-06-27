# SKILL-03 – Boundary Value Analysis (Agent Version)

## Kích hoạt
Nói với agent: **"SKILL-03"** (sau SKILL-01 trong cùng session)

---

## System instruction (load vào agent)

```
When the user says "SKILL-03", execute the following using SKILL-01 output already in this conversation:

TASK: Apply BVA to all variables flagged as "Variables to BVA" in SKILL-01.

For each applicable variable, produce ALL of these boundary points:
- MIN-1 : one step below minimum → INVALID
- MIN   : minimum valid value → VALID
- MIN+1 : one step above minimum → VALID
- NOM   : typical middle value → VALID
- MAX-1 : one step below maximum → VALID
- MAX   : maximum valid value → VALID
- MAX+1 : one step above maximum → INVALID

If the actual MIN or MAX is unknown from the spec, write "⚠️ UNKNOWN – must verify in app or source code" and provide a best-guess based on common practice.

For string-length variables: apply BVA to the CHARACTER COUNT, not the content.
For integer count variables: apply BVA to the COUNT VALUE.
Skip boolean and pure enum variables — note them as "SKIPPED: no ordered boundary".

OUTPUT FORMAT:

### SKILL-03 Output: Boundary Value Analysis
**Feature:** [feature name]

| Variable | Boundary | Concrete Value | Domain | Expected Behavior |
|----------|----------|----------------|--------|-------------------|
| password | MIN-1 | 5 chars: "Ab@1!" | INVALID | Reject – too short |
| password | MIN | 6 chars: "Ab@12!" | VALID | Accept |
...

**Skipped variables:** [list + reason]
**⚠️ Unknowns to verify:** [list what needs real app verification]

**BVA TC count estimate:** [N] additional test cases

---
> SKILL-03 complete. Tell me "SKILL-04" to generate all test case files.
```

---

## Ví dụ lệnh → output

**Bạn gõ:**
```
SKILL-03
```

**Agent trả về:**
```
### SKILL-03 Output: Boundary Value Analysis
Feature: FR-02: Login & Account Lockout

| Variable | Boundary | Concrete Value | Domain | Expected Behavior |
|----------|----------|----------------|--------|-------------------|
| password (length) | MIN-1 | 5 chars: "Ab@1!" | INVALID | Reject – too short |
| password (length) | MIN | 6 chars: "Ab@12!" | VALID | Accept |
| password (length) | MIN+1 | 7 chars: "Ab@123!" | VALID | Accept |
| password (length) | NOM | 12 chars: "Abc@123456xy" | VALID | Accept |
| password (length) | MAX-1 | ⚠️ UNKNOWN–1 | VALID | Accept |
| password (length) | MAX | ⚠️ UNKNOWN | VALID | Accept |
| password (length) | MAX+1 | ⚠️ UNKNOWN+1 | INVALID | Reject – too long |
| failed_attempts | MIN | 0 | VALID | Account active |
| failed_attempts | MIN+1 | 1 | VALID | Account active |
| failed_attempts | MAX-1 | threshold–1 | VALID | Active, last warning |
| failed_attempts | MAX | threshold (⚠️ verify) | INVALID | Account locked |
| failed_attempts | MAX+1 | threshold+1 | INVALID | Already locked |

Skipped variables: email format – SKIPPED: categorical, no ordered boundary

⚠️ Unknowns to verify:
- password MAX length: check input field or backend validation
- lockout threshold N: check app behavior by testing 3→4→5 failed attempts

BVA TC count estimate: 12 additional test cases
```

---

## Review checklist
- [ ] Tất cả biến ordered đã có đủ 7 boundary points
- [ ] ⚠️ Unknowns đã được verify thực tế trên app trước khi sang SKILL-04
- [ ] Concrete values là giá trị dùng được ngay (không phải placeholder)
- [ ] Điền "User corrections" vào audit log
