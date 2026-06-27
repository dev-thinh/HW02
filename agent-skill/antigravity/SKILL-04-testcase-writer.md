# SKILL-04 – Test Case Writer (Agent Version)

## Kích hoạt
Nói với agent: **"SKILL-04"** (sau SKILL-02 + SKILL-03 trong cùng session)

---

## System instruction (load vào agent)

```
When the user says "SKILL-04", execute the following using SKILL-02 and SKILL-03 outputs already in this conversation:

TASK: Generate all test case files in Markdown format.

NAMING RULES:
- Domain Testing (EP-based): TC-[MODULE]-[3-digit], e.g., TC-LOGIN-001
- BVA-based: TC-[MODULE]-BVA-[3-digit], e.g., TC-LOGIN-BVA-001
- Module codes: LOGIN, COUPON, CAT, MPROD

OUTPUT RULE: For each test case, output a complete Markdown block with a clear separator.
Wrap each file in a code block labeled with its filename so the user knows exactly which file to create.

For EACH equivalence class from SKILL-02, write one test case.
For EACH boundary point from SKILL-03, write one test case.

TEMPLATE for each test case:

=== FILE: tests/test-cases/[folder]/[TC-ID].md ===
# [TC-ID]: [Short descriptive title]

## Requirement ID
[FR-XX]

## Module / Test type / Technique
[Module] / Functional / [Domain Testing – EP (Class ID) OR BVA (Boundary point)]

## Preconditions
- [condition]

## Test data
| Field | Value |
|-------|-------|
| [field] | [value] |

## Test steps
1. [step]
2. [step]

## Expected result
[Clear, specific expected outcome]

## Status / Related bugs
Not Run / None
=== END FILE ===

After all test cases, output a SUMMARY TABLE:
| TC ID | Technique | Class/Boundary | Title |
|-------|-----------|----------------|-------|

Total: [N] Domain Testing TCs + [M] BVA TCs = [N+M] total
```

---

## Ví dụ lệnh → output (excerpt)

**Bạn gõ:**
```
SKILL-04
```

**Agent trả về:**
```
=== FILE: tests/test-cases/fr02-login/TC-LOGIN-001.md ===
# TC-LOGIN-001: Đăng nhập thành công với credentials hợp lệ

## Requirement ID
FR-02

## Module / Test type / Technique
Login / Functional / Domain Testing – EP (COMBO-01)

## Preconditions
- Tài khoản user01@gmail.com tồn tại và chưa bị khóa
- failed_attempts = 0
- Đang ở trang /login

## Test data
| Field | Value |
|-------|-------|
| Email | user01@gmail.com |
| Password | Abc@123456 |

## Test steps
1. Mở trang /login
2. Nhập Email: user01@gmail.com
3. Nhập Password: Abc@123456
4. Bấm Login

## Expected result
- Login thành công
- Redirect về trang Home
- Header hiển thị tên user

## Status / Related bugs
Not Run / None
=== END FILE ===

[... tiếp tục cho mọi TC khác ...]

Summary:
| TC ID | Technique | Class/Boundary | Title |
|-------|-----------|----------------|-------|
| TC-LOGIN-001 | EP | COMBO-01 | Login thành công |
| TC-LOGIN-002 | EP | EP-EMAIL-02 | Email không tồn tại |
...
| TC-LOGIN-BVA-001 | BVA | password MIN-1 | Password 5 ký tự bị từ chối |

Total: 11 Domain Testing TCs + 12 BVA TCs = 23 total
```

---

## Sau khi agent trả output

1. **Review từng TC** — sửa bất kỳ expected result nào không đúng với app thực tế
2. **Tạo file** — copy từng block vào file `.md` tương ứng trong repo
3. **Commit:**
```bash
git add tests/test-cases/fr02-login/
git commit -m "feat(fr02): add 23 test cases – domain testing + BVA"
git push
```
4. Điền "User corrections" vào audit log

## → Tiếp theo: "SKILL-05" để kiểm tra gaps
